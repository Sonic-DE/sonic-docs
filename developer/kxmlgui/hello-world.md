---
title: Hello World!
description: Your first window with SonicDE's libraries.
source_url: https://develop.kde.org/docs/getting-started/kxmlgui/hello_world/
source_authors: [Adriaan de Groot, Alexander Lohnau, Andrew Shark, Arpan Patelia, Carl Schwan, Claudio Cambra, Frederik Schwarzer, Jacky Alcine, Kunda Ki, Marco Parillo, Mikhail Zolotukhin, Nicolas Fella, Thiago Sueto, Tobias Fella]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-widgets-addons (KMessageBox, KGuiItem), sonic-frameworks-core-addons (KAboutData), sonic-frameworks-internationalization (KLocalizedString), sonic-frameworks-io (web shortcuts); all three programs built against SonicDE's frameworks, --version and --author run
---

# Hello World!

## Summary

Your first program greets the world with a friendly "Hello World". It uses a [KMessageBox](/docs/api/kwidgetsaddons/kmessagebox) and customizes one of its buttons.

> **Note:** The API reference of SonicDE's libraries is at [/docs/api](/docs/api). Qt's documentation is useful too, since much of SonicDE's libraries builds on Qt; KRunner's `qt:` web shortcut searches it.

## Preparation

You need SonicDE's development files, so you can build against its libraries. Either install SonicDE from your distribution (on Gentoo and Arch Linux the packages include the headers), or build and install it with sonicde-builder, as described in [Building Sonic-DE](../building.md).

Create a folder for the tutorial's source files, for example `~/src/kxmlgui-tutorial`.

## The code

### Hello World

All the code goes in one file, `main.cpp`. Start simple and extend it as you go. Create it with this code:

```cpp
#include <QApplication>
#include <KMessageBox>

int main (int argc, char *argv[])
{
    QApplication app(argc, argv);

    KGuiItem primaryAction(
        // Content text, Icon
        QStringLiteral("Hello"), QString(),
        // Tooltip text
        QStringLiteral("This is a tooltip"),
        // WhatsThis text
        QStringLiteral("This is a WhatsThis help text."));

    auto messageBox = KMessageBox::questionTwoActions(
        // Parent
        nullptr,
        // MessageBox contents
        QStringLiteral("Hello World"),
        // MessageBox title
        QStringLiteral("Hello Title"),
        // Primary action, Secondary action
        primaryAction, KStandardGuiItem::cancel());

    if (messageBox == KMessageBox::PrimaryAction)
    {
        return EXIT_SUCCESS;
    }
    else
    {
        return EXIT_FAILURE;
    }
}
```

The popup is a [KMessageBox](/docs/api/kwidgetsaddons/kmessagebox) with two buttons: a *primary action*, usually the confirmation, and a *secondary action*, usually something else, such as cancel or discard. Here the primary action is a custom [KGuiItem](/docs/api/kwidgetsaddons/kguiitem) with the text "Hello", and the secondary action is [KStandardGuiItem::cancel()](/docs/api/kwidgetsaddons/kstandardguiitem).

First, create a [QApplication](https://doc.qt.io/qt-6/qapplication.html). Create it exactly once, before any other Qt or SonicDE object: it is the starting point of your application and needed by other components, such as [KI18n](/docs/api/ki18n/ki18n-index) for translations.

The first argument of the [KGuiItem](/docs/api/kwidgetsaddons/kguiitem) constructor is the text shown on the item (here, a button). Next you could give an icon; we don't want one, so we pass an empty `QString()`. Then come the tooltip (shown when you hover over the item) and the "What's This?" text (shown with Shift+F1 or by right-clicking).

With the item for the primary button ready, create the popup with `KMessageBox::questionTwoActions()`. The first argument is the parent widget, which we don't need, so we pass `nullptr`. The second is the text inside the message box, above the buttons: "Hello World". The third is the caption in the window's title bar, "Hello Title". Then comes our custom `primaryAction`, and finally `KStandardGuiItem::cancel()`, a ready-made [KGuiItem](/docs/api/kwidgetsaddons/kguiitem) with translated text, for the secondary button.

> **Important:** Use `QStringLiteral("Hello World!")` instead of plain `"Hello World!"` for strings. It is good practice in Qt programming, and expected in SonicDE's code.

### About data and internationalization

```cpp
#include <QApplication>
#include <KMessageBox>
#include <KAboutData>
#include <KLocalizedString>

int main (int argc, char *argv[])
{
    using namespace Qt::Literals::StringLiterals;

    QApplication app(argc, argv);
    KLocalizedString::setApplicationDomain("tutorial1");

    KAboutData aboutData(
        // The program name used internally. (componentName)
        u"helloworld"_s,
        // A displayable program name string. (displayName)
        i18n("Hello World tutorial"),
        // The program version string. (version)
        u"1.0"_s,
        // Short description of what the app does. (shortDescription)
        i18n("Displays a KMessageBox popup"),
        // The license this code is released under
        KAboutLicense::GPL,
        // Copyright Statement (copyrightStatement = QString())
        i18n("(c) 2024"),
        // Optional text shown in the About box.
        // Can contain any information desired. (otherText)
        i18n("Educational application..."),
        // The program homepage string. (homePageAddress = QString())
        u"https://example.com/helloworld/"_s,
        // Where users report bugs: an email address or a web address
        u"https://example.com/helloworld/bugs/"_s);

    aboutData.addAuthor(
        // Author full name
        i18n("John Doe"),
        // Author role
        i18n("Tutorial learner"),
        // Author email
        u"john.doe@example.com"_s,
        // Author website
        u"https://john-doe.example.com"_s,
        // Username in store.kde.org (for avatar image)
        u"johndoe"_s);

    KAboutData::setApplicationData(aboutData);

    KGuiItem primaryAction(
        i18n("Hello"), QString(),
        i18n("This is a tooltip"),
        i18n("This is a WhatsThis help text."));

    auto messageBox = KMessageBox::questionTwoActions(
        nullptr,
        i18n("Hello World"),
        i18n("Hello Title"),
        primaryAction, KStandardGuiItem::cancel());

    if (messageBox == KMessageBox::PrimaryAction)
    {
        return EXIT_SUCCESS;
    }
    else
    {
        return EXIT_FAILURE;
    }
}
```

For your application to be translated, the code must first be prepared so it can be adapted to languages and regions without engineering changes: [internationalization](https://doc.qt.io/qt-6/internationalization.html). SonicDE uses [KI18n](/docs/api/ki18n/ki18n-index) for that, which provides [KLocalizedString](/docs/api/ki18n/klocalizedstring).

Start by calling `KLocalizedString::setApplicationDomain()`, which sets the translation catalog. It must come before everything else, except creating the `QApplication`. Then wrap the strings users see, which need translating, in `i18n()`. Strings users don't see, which aren't translated, use `QStringLiteral` instead; [KAboutData](/docs/api/kcoreaddons/kaboutdata) uses them below.

> **Important:** Since many string arguments follow, instead of writing `QStringLiteral()` seven times, use QString's [operator""_s](https://doc.qt.io/qt-6/qstring.html#operator-22-22_s), a shorter notation for Qt [string literals](https://en.cppreference.com/w/cpp/language/string_literal) that does the same. That is what `using namespace Qt::Literals::StringLiterals;` is for: instead of `QStringLiteral("Hello World!")`, `u"Hello World!"_s` is enough.

[KAboutData](/docs/api/kcoreaddons/kaboutdata) stores information about the application, which many other components reuse. Create it with its fairly complete constructor and add the author. Use your own homepage and bug address: they appear in the About dialog and in `--author`, and without a bug address KAboutData uses KDE's (`submit@bugs.kde.org`). Then call `KAboutData::setApplicationData()` to set the `QApplication`'s properties from it.

The message box adapts to its content, and the window title now includes "Hello World tutorial", the display name set with KAboutData. The display name is available from `KAboutData::displayName()` when needed.

If your system uses another language, the [KStandardGuiItem::cancel()](/docs/api/kwidgetsaddons/kstandardguiitem) button probably already appears in it instead of saying "Cancel".

### Command line

```cpp
#include <QApplication>
#include <QCommandLineParser>
#include <KMessageBox>
#include <KAboutData>
#include <KLocalizedString>

int main (int argc, char *argv[])
{
    using namespace Qt::Literals::StringLiterals;

    QApplication app(argc, argv);
    KLocalizedString::setApplicationDomain("tutorial1");

    KAboutData aboutData(
        u"helloworld"_s,
        i18n("Hello World tutorial"),
        u"1.0"_s,
        i18n("Displays a KMessageBox popup"),
        KAboutLicense::GPL,
        i18n("(c) 2024"),
        i18n("Educational application..."),
        u"https://example.com/helloworld/"_s,
        u"https://example.com/helloworld/bugs/"_s);

    aboutData.addAuthor(
        i18n("John Doe"),
        i18n("Tutorial learner"),
        u"john.doe@example.com"_s,
        u"https://john-doe.example.com"_s,
        u"johndoe"_s);

    KAboutData::setApplicationData(aboutData);

    QCommandLineParser parser;
    aboutData.setupCommandLine(&parser);
    parser.process(app);
    aboutData.processCommandLine(&parser);

    KGuiItem primaryAction(
        i18n("Hello"), QString(),
        i18n("This is a tooltip"),
        i18n("This is a WhatsThis help text."));

    auto messageBox = KMessageBox::questionTwoActions(
        nullptr,
        i18n("Hello World"),
        i18n("Hello Title"),
        primaryAction, KStandardGuiItem::cancel());

    if (messageBox == KMessageBox::PrimaryAction)
    {
        return EXIT_SUCCESS;
    }
    else
    {
        return EXIT_FAILURE;
    }
}
```

Finally, [QCommandLineParser](https://doc.qt.io/qt-6/qcommandlineparser.html). It is what you would use for command-line options, for example to open the program with a given file. Here we only set it up with the KAboutData, so the program gets the `--version`, `--author` and `--license` options.

That's all the code. Now build it and try it.

## Building and running the project

To build the project you need a build system that compiles and links the libraries. We use the industry standard, CMake, with a file called `CMakeLists.txt` in the project folder.

### Writing a CMakeLists.txt

Create `CMakeLists.txt` next to `main.cpp`:

```cmake
cmake_minimum_required(VERSION 3.20)

project(helloworld)

set(QT_MIN_VERSION "6.6.0")
set(KF_MIN_VERSION "6.0.0")

find_package(ECM ${KF_MIN_VERSION} REQUIRED NO_MODULE)
set(CMAKE_MODULE_PATH ${ECM_MODULE_PATH} ${CMAKE_CURRENT_SOURCE_DIR}/cmake)

include(KDEInstallDirs)
include(KDECMakeSettings)
include(KDECompilerSettings NO_POLICY_SCOPE)
include(FeatureSummary)

find_package(Qt6 ${QT_MIN_VERSION} CONFIG REQUIRED COMPONENTS
    Core    # QCommandLineParser, QStringLiteral
    Widgets # QApplication
)

find_package(KF6 ${KF_MIN_VERSION} REQUIRED COMPONENTS
    CoreAddons      # KAboutData
    I18n            # KLocalizedString
    WidgetsAddons   # KMessageBox
)

add_executable(helloworld)

target_sources(helloworld
    PRIVATE
    main.cpp
)

target_link_libraries(helloworld
    Qt6::Widgets
    KF6::CoreAddons
    KF6::I18n
    KF6::WidgetsAddons
)

install(TARGETS helloworld ${KDE_INSTALL_TARGETS_DEFAULT_ARGS})

feature_summary(WHAT ALL INCLUDE_QUIET_PACKAGES FATAL_ON_MISSING_REQUIRED_PACKAGES)
```

[`find_package()`](https://cmake.org/cmake/help/latest/command/find_package.html) finds a package (here ECM, Qt6 and KF6) and sets variables for the location of its headers and libraries. ECM, Extra CMake Modules (SonicDE's `sonic-frameworks-cmake-modules`), provides CMake files and functions for building these applications.

The `Qt6` and `KF6` calls find the Qt 6 and SonicDE libraries the tutorial needs (SonicDE's frameworks keep the `KF6` package names). CMake passes their files to the compiler. The minimum versions are set at the top of the file for easy reference; SonicDE itself requires Qt 6.11.

[`add_executable()`](https://cmake.org/cmake/help/latest/command/add_executable.html) creates the executable `helloworld`, and [`target_link_libraries()`](https://cmake.org/cmake/help/latest/command/target_link_libraries.html) links it to the libraries. [`install()`](https://cmake.org/cmake/help/latest/command/install.html) creates an install target that puts executables and libraries in the default places, with ECM's `KDE_INSTALL_TARGETS_DEFAULT_ARGS`. Including ECM also creates an uninstall target from the install target.

### Building and running

In the project folder, run:

```bash
cmake -B build/ --install-prefix ~/.local
cmake --build build/ --parallel
cmake --install build/
```

These are the three steps: configuring, building and installing.

`--parallel` lets CMake compile several files at once, and `--install-prefix` says where to install. Here `helloworld` is installed as `~/.local/bin/helloworld`.

Run it with:

```bash
helloworld
```

You can also run it with options. `--help` is added by Qt's [QCommandLineParser](https://doc.qt.io/qt-6/qcommandlineparser.html), and `--version`, `--author` and `--license` show what you set with [KAboutData](/docs/api/kcoreaddons/kaboutdata):

```bash
helloworld --help
helloworld --version
helloworld --author
helloworld --license
```

Next: [Creating the main window](main-window.md).
