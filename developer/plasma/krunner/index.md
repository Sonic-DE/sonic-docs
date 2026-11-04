---
title: KRunner C++ plugins
description: Write a plugin that adds search results to KRunner and the application launchers.
source_url: https://develop.kde.org/docs/plasma/krunner/
source_authors: [Alexander Lohnau, Carl Schwan, Joshua Wug, Marius P, Nate Graham, Nicolas Fella, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "AbstractRunner, RunnerManager, QueryMatch and RunnerContext in sonic-frameworks-runner; runners in sonic-workspace and sonic-workspace-addons; the example and its config module built against the local build, and the runner queried through AbstractRunnerTest. The config module was compiled but not opened, and run() was not triggered."
---

# KRunner C++ plugins

KRunner is the search window of the SonicDE desktop: as you type, matching actions and information appear. The results come from plugins called runners, loaded at runtime. Any application using the KRunner library can use them, such as the application launcher. This tutorial shows how to create one.

## Anatomy of a runner

[KRunner::AbstractRunner](/docs/api/krunner/krunner-abstractrunner) is the base class of all runners. It provides the structure to:

- do one-time setup after creation
- do setup and teardown before and after a match session
- create matches for a search term
- define secondary actions for a match
- act on the match the user chooses
- show configuration options

Three other classes are important here:

- [KRunner::RunnerContext](/docs/api/krunner/krunner-runnercontext) gives the plugin information about the current query.
- [KRunner::QueryMatch](/docs/api/krunner/krunner-querymatch) represents one match for a query.
- [KRunner::RunnerSyntax](/docs/api/krunner/krunner-runnersyntax) advertises the query syntax the plugin understands.

## Creating a runner project

We'll create a runner that finds files in the home directory matching the query and offers to open them. The [`runner6` template](https://github.com/Sonic-DE/sonic-frameworks-runner/tree/master/templates/runner6) in `sonic-frameworks-runner` is another starting point.

### CMakeLists.txt

`kcoreaddons_add_plugin()` builds the plugin and installs it where runners are looked for, `kf6/krunner` in Qt's plugin directory.

```cmake
cmake_minimum_required(VERSION 3.16)
project(runnerexample)

find_package(ECM 6.0.0 REQUIRED NO_MODULE)
set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH})

include(KDEInstallDirs)
include(KDECMakeSettings)
include(KDECompilerSettings NO_POLICY_SCOPE)

find_package(Qt6 REQUIRED COMPONENTS Core Gui)
find_package(KF6 REQUIRED COMPONENTS I18n Config Runner KIO KCMUtils)

add_definitions(-DTRANSLATION_DOMAIN=\"plasma_runner_homefiles\")

kcoreaddons_add_plugin(runner_example_homefiles
    SOURCES homefilesrunner.cpp
    INSTALL_NAMESPACE "kf6/krunner"
)
target_link_libraries(runner_example_homefiles
    KF6::I18n
    KF6::ConfigCore
    KF6::Runner
    KF6::KIOWidgets
)

# If the runner has no config module, remove these lines, KCMUtils
# and X-KDE-ConfigModule from the JSON file
kcoreaddons_add_plugin(kcm_homefilesrunner
    SOURCES kcm_homefilesrunner.cpp
    INSTALL_NAMESPACE "kf6/krunner/kcms"
)
target_link_libraries(kcm_homefilesrunner
    KF6::ConfigCore
    KF6::KCMUtils
)
```

### The JSON metadata file

KRunner reads metadata embedded in each plugin. Here it comes from `homefilesrunner.json`, which is named in the `K_PLUGIN_CLASS_WITH_JSON` macro below.

```json
{
    "KPlugin": {
        "Description": "Part of a tutorial demonstrating how to create Runner plugins",
        "EnabledByDefault": true,
        "Icon": "user-home",
        "Name": "Home Files"
    },
    "X-KDE-ConfigModule": "kf6/krunner/kcms/kcm_homefilesrunner"
}
```

The plugin ID comes from the plugin's file name, here `runner_example_homefiles`. Entries such as `Name` and `Description` are shown in the user interface. Avoid jargon in them, so that people can tell what your plugin does. The [metadata format](metadata.md) page has more.

### The header file

```cpp
#pragma once

#include <KRunner/AbstractRunner>

class HomeFilesRunner : public KRunner::AbstractRunner
{
    Q_OBJECT

public:
    HomeFilesRunner(QObject *parent, const KPluginMetaData &data);

    void match(KRunner::RunnerContext &context) override;
    void run(const KRunner::RunnerContext &context, const KRunner::QueryMatch &match) override;
    void reloadConfiguration() override;

protected:
    void init() override;

private:
    QString m_path;
    QString m_triggerWord;
};
```

## Threads

A runner plugin is created once and reused for many queries. `RunnerManager` gives each C++ runner its own thread:

- `init()`, `reloadConfiguration()` and `match()` run in the runner's thread, so they don't block the user interface, and `match()` calls for one runner don't overlap.
- The constructor runs in the thread that creates the manager, before the runner moves to its own thread.
- `run()` is called directly by the manager, normally in the main thread.

Any data used by both `match()` and `run()` must therefore be protected, or passed along in the match, as this example does.

## Initializing the runner

### The plugin declaration macro

The implementation (`.cpp`) file ends with:

```cpp
K_PLUGIN_CLASS_WITH_JSON(HomeFilesRunner, "homefilesrunner.json")

#include "homefilesrunner.moc"
```

The macro generates the factory that creates the plugin. Its parameters are the class and the JSON metadata file.

### The constructor

```cpp
HomeFilesRunner::HomeFilesRunner(QObject *parent, const KPluginMetaData &data)
    : KRunner::AbstractRunner(parent, data)
{
}
```

`parent` and `data` are needed to load the plugin, and go to the base class.

### init()

`init()` holds setup that should happen once in the plugin's lifespan, before any matching. The runner isn't queried until `init()` has finished. By default it calls `reloadConfiguration()`.

```cpp
void HomeFilesRunner::init()
{
    reloadConfiguration();
    connect(this, &KRunner::AbstractRunner::prepare, this, []() {
        // Initialize data for the match session
    });
    connect(this, &KRunner::AbstractRunner::teardown, this, []() {
        // Clean up data from the match session
    });
}
```

The `prepare` signal is emitted when matching is about to start. Any number of `match()` calls may follow, and then the `teardown` signal. Use them for data needed only during a match session.

## Matching queries

The main purpose of a runner is to return matches for a query string. `match(KRunner::RunnerContext &context)` is called when there is a new query, with a context that holds the query and collects your matches along with those of other runners. Here is the whole method:

```cpp
void HomeFilesRunner::match(KRunner::RunnerContext &context)
{
    QString query = context.query();
    if (query == QLatin1Char('.') || query == QLatin1String("..")) {
        return;
    }
    // This should not get in the way of the help runner, which is triggered by queries starting with '?'
    if (query.startsWith(QLatin1Char('?'))) {
        return;
    }

    if (!m_triggerWord.isEmpty()) {
        if (!query.startsWith(m_triggerWord)) {
            return;
        }
        query.remove(0, m_triggerWord.length());
    }

    const QString pattern = query.length() > 2 ? QLatin1Char('*') + query + QLatin1Char('*') : query;

    QMimeDatabase mimeDb;
    QDir dir(m_path);
    QList<KRunner::QueryMatch> matches;
    const QStringList files = dir.entryList(QStringList(pattern));
    for (const QString &file : files) {
        const QString path = dir.absoluteFilePath(file);
        if (!path.startsWith(m_path)) {
            // This file isn't in our directory; looks like we got a query with some ..'s in it!
            continue;
        }
        if (!context.isValid()) {
            return;
        }
        KRunner::QueryMatch match(this);
        match.setText(i18n("Open %1", path));
        match.setData(path);
        match.setId(path);
        match.setIconName(mimeDb.mimeTypeForFile(path).iconName());

        if (file.compare(query, Qt::CaseInsensitive) == 0) {
            match.setRelevance(1.0);
            match.setCategoryRelevance(KRunner::QueryMatch::CategoryRelevance::Highest);
        } else {
            match.setRelevance(0.8);
        }

        matches.append(match);
    }
    context.addMatches(matches);
}
```

The start shows some common techniques. If the query can't produce anything useful, the method returns quickly.

It also uses a *trigger word*, a keyword that lets the user control the results. The spell checker runner, for example, uses "spell" (translated to the user's language), so typing "spell plasma" checks that word. This doesn't suit every runner, but it can be very effective.

A third technique is to treat a query differently by its size. Queries of 3 or more letters become a glob with a `*` on each end. Shorter ones don't, as they would likely match far more than anyone wants.

The list of matches lets them all be added together at the end, which is slightly more efficient than adding them one at a time.

The query may change while the runner is working. The context is then marked as invalid, so check `context.isValid()` before expensive work and in long loops, to avoid wasting processor time.

[KRunner::QueryMatch](/docs/api/krunner/krunner-querymatch) objects are small data containers. They are generally created on the stack and can be copied freely.

The match's text and icon are shown in the user interface. The ID is specific to the runner and identifies the match. Its data is also specific to the runner: any `QVariant` that makes it easier to run the match later.

`setRelevance()` takes a value between 0.0 and 1.0 for how close the match is to the query, and it sorts matches within their category. `setCategoryRelevance()` sorts the categories themselves. It takes a value from `Lowest` to `Highest`, or a number from 0 to 100, and the default is `Moderate`. Here an exact file name gets `Highest`.

Finally, the matches are added to the context. The runner doesn't need to worry about whether they're still valid for the current query. It can also offer them in batches, or call `context.addMatch()` for each one, though `addMatches()` is more efficient.

## Running a match

When the user selects a match, `run()` is called. It runs in the main thread, so blocking in it is poor form. If something will take any considerable time, make it asynchronous.

```cpp
void HomeFilesRunner::run(const KRunner::RunnerContext & /*context*/, const KRunner::QueryMatch &match)
{
    // KIO::OpenUrlJob deletes itself, so we can create it and forget it
    auto *job = new KIO::OpenUrlJob(QUrl::fromLocalFile(match.data().toString()));
    job->setUiDelegate(new KNotificationJobUiDelegate(KJobUiDelegate::AutoErrorHandlingEnabled));
    job->setRunExecutables(false);
    job->start();
}
```

The file also needs these includes:

```cpp
#include "homefilesrunner.h"

#include <KConfigGroup>
#include <KIO/OpenUrlJob>
#include <KLocalizedString>
#include <KNotificationJobUiDelegate>
#include <QDir>
#include <QMimeDatabase>
```

Besides its main action, a match can offer secondary ones with `QueryMatch::setActions()`; `run()` can read which one was chosen from `match.selectedAction()`.

## Configuration

Read and write a runner's options through the `KConfigGroup` from `AbstractRunner::config()`. It is the runner's group in `[Runners]` in `krunnerrc`. The best place to read them is `reloadConfiguration()`, which is called when the configuration changes on disk.

```cpp
void HomeFilesRunner::reloadConfiguration()
{
    KConfigGroup c = config();
    m_triggerWord = c.readEntry("trigger", QString());
    if (!m_triggerWord.isEmpty()) {
        m_triggerWord.append(QLatin1Char(' '));
    }

    m_path = c.readPathEntry("path", QDir::homePath());
    QFileInfo pathInfo(m_path);
    if (!pathInfo.isDir()) {
        m_path = QDir::homePath();
    }

    setSyntaxes({KRunner::RunnerSyntax(QStringLiteral("%1:q:").arg(m_triggerWord), i18n("Finds files matching :q: in the %1 folder", m_path))});
}
```

If you provide a default trigger word, mark it for translation with `i18nc("Note this is a KRunner keyword", "trigger")`. Translators then know how to translate it, and users can use the runner in their own language.

### Publishing recognized syntax

Runners can advertise the queries they understand with [KRunner::RunnerSyntax](/docs/api/krunner/krunner-runnersyntax) objects, which users can read as documentation at runtime. They are optional but highly recommended.

The first parameter is an example of the query and the second describes what it does. In this runner the syntax is created when the configuration is read, because it depends on the trigger word.

The special string `:q:` in both stands for the text the user enters, and is replaced with something more meaningful in the user interface.

If a runner understands several queries that give the same matches, add them as a list: `addSyntax()` also takes a `QStringList` of example queries.

### Config modules

A runner can have a settings module of its own. Register its path in the JSON metadata, as above, and install it to `kf6/krunner/kcms`. It needs no embedded metadata.

`kcm_homefilesrunner.cpp`:

```cpp
#include <KCModule>
#include <KConfigGroup>
#include <KPluginFactory>
#include <KSharedConfig>
#include <QDir>
#include <QLabel>

class HomeFilesRunnerConfig : public KCModule
{
    Q_OBJECT

public:
    HomeFilesRunnerConfig(QObject *parent, const KPluginMetaData &data)
        : KCModule(parent, data)
    {
        KSharedConfigPtr krunnerConfig = KSharedConfig::openConfig(QStringLiteral("krunnerrc"));
        KConfigGroup pluginConfig = krunnerConfig->group(QStringLiteral("Runners")).group(QStringLiteral("runner_example_homefiles"));

        const QString triggerWord = pluginConfig.readEntry("trigger");
        const QString path = pluginConfig.readEntry("path", QDir::homePath());

        new QLabel(QStringLiteral("The keyword is %1 and the path is %2").arg(triggerWord, path), widget());

        // To allow editing the values, override KCModule::load(), save() and defaults()
    }
};

K_PLUGIN_CLASS(HomeFilesRunnerConfig)

#include "kcm_homefilesrunner.moc"
```

The module can be opened from KRunner's settings page or from the help runner, activated by typing `?`. When the settings are saved, `reloadConfiguration()` is called.

## Single runner mode

An application usually uses many runners at once through `KRunner::RunnerManager`, but it can also use just one. KRunner offers this over D-Bus, through its `querySingleRunner` method, which is useful for binding a keyboard shortcut to a runner:

```bash
qdbus org.kde.krunner /App org.kde.krunner.App.querySingleRunner runner_example_homefiles ""
```

A runner can detect this by calling [`RunnerContext::singleRunnerQueryMode()`](/docs/api/krunner/krunner-runnercontext) on the context passed to `match()`. If it returns `true`, the runner might change its behavior, for example by not requiring a trigger word.

## Testing a runner

`KRunner::AbstractRunnerTest` loads your plugin and runs queries against it from a [Qt Test](https://doc.qt.io/qt-6/qtest-overview.html). The `krunner_configure_test()` CMake function connects the test to the runner:

```cmake
find_package(Qt6 REQUIRED COMPONENTS Test)

add_executable(homefilesrunnertest homefilesrunnertest.cpp)
target_link_libraries(homefilesrunnertest Qt::Test KF6::Runner)
krunner_configure_test(homefilesrunnertest runner_example_homefiles)
```

```cpp
#include <KRunner/AbstractRunner>
#include <KRunner/AbstractRunnerTest>
#include <KRunner/RunnerManager>
#include <QTest>

class HomeFilesRunnerTest : public KRunner::AbstractRunnerTest
{
    Q_OBJECT

private Q_SLOTS:
    void testQuery()
    {
        initProperties();
        launchQuery(QStringLiteral("alpha.txt"));
        for (const KRunner::QueryMatch &match : manager->matches()) {
            qInfo() << match.text() << match.relevance();
        }
    }
};

QTEST_MAIN(HomeFilesRunnerTest)

#include "homefilesrunnertest.moc"
```
