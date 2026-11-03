---
title: "KRunner::AbstractRunner Class"
description: "An abstract base class for Plasma Runner plugins."
---

# KRunner::AbstractRunner Class

An abstract base class for Plasma Runner plugins. [More...](#details)

- **Header:** `#include <KRunner/AbstractRunner>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Runner)`  
  `target_link_libraries(mytarget PRIVATE KF6::Runner)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](krunner-abstractrunner-members.md)

## Public Functions

- [QString id() const](#id)
- [bool isMatchingSuspended() const](#isMatchingSuspended)
- [void match(KRunner::RunnerContext &context)](#match)
- [QRegularExpression matchRegex() const](#matchRegex)
- [KPluginMetaData metadata() const](#metadata)
- [int minLetterCount() const](#minLetterCount)
- [QString name() const](#name)
- [void reloadConfiguration()](#reloadConfiguration)
- [void run(const KRunner::RunnerContext &context, const KRunner::QueryMatch &match)](#run)
- [void setMatchRegex(const QRegularExpression &regex)](#setMatchRegex)
- [void setMinLetterCount(int count)](#setMinLetterCount)
- [void setTriggerWords(const QStringList &triggerWords)](#setTriggerWords)
- [QList\<KRunner::RunnerSyntax\> syntaxes() const](#syntaxes)

## Signals

- [void prepare()](#prepare)
- [void teardown()](#teardown)

## Protected Functions

- [AbstractRunner(QObject \*parent, const KPluginMetaData &pluginMetaData)](#AbstractRunner)
- [void addSyntax(const KRunner::RunnerSyntax &syntax)](#addSyntax)
- [void addSyntax(const QString &exampleQuery, const QString &description)](#addSyntax-1)
- [KConfigGroup config() const](#config)
- [void init()](#init)
- [QMimeData \*mimeDataForMatch(const KRunner::QueryMatch &match)](#mimeDataForMatch)
- [void setSyntaxes(const QList\<KRunner::RunnerSyntax\> &syntaxes)](#setSyntaxes)
- [void suspendMatching(bool suspend)](#suspendMatching)

## Detailed Description {#details}

Be aware that runners will be moved to their own thread after being instantiated. This means that except for [AbstractRunner::run](krunner-abstractrunner.md#run) and the constructor, all methods will be non-blocking for the UI. Consider doing heavy resource initialization in the init method instead of the constructor.

## Member Function Documentation {#member-function-documentation}

### \[explicit protected\] AbstractRunner::AbstractRunner(QObject \**parent*, const KPluginMetaData &*pluginMetaData*) {#AbstractRunner}

Constructor for a [KRunner](krunner-module.md) plugin

@note You should connect here to the prepare/teardown signals. However, avoid doing heavy initialization here in favor of doing it in [AbstractRunner::init](krunner-abstractrunner.md#init)

`parent` parent object for this runner

`pluginMetaData` metadata that was embedded in the runner

`args` for compatibility with KPluginFactory, since 6.0 this can be omitted

### \[protected\] void AbstractRunner::addSyntax(const KRunner::RunnerSyntax &*syntax*) {#addSyntax}

Adds a registered syntax that this runner understands. This is used to display to the user what this runner can understand and how it can be used.

`syntax` the syntax to register

### \[protected\] void AbstractRunner::addSyntax(const QString &*exampleQuery*, const QString &*description*) {#addSyntax-1}

Utility overload for creating a syntax based on the given parameters

*See also* [RunnerSyntax](krunner-runnersyntax.md)

### \[protected\] KConfigGroup AbstractRunner::config() const {#config}

Provides access to the runner's configuration object. This config is saved in the "krunnerrc" file in the \[Runners\]\[\<pluginId\>\] config group Settings should be written in a KDE config module. See https://develop.kde.org/docs/plasma/krunner/#runner-configuration

### QString AbstractRunner::id() const {#id}

Returns an id from the runner's metadata

### \[virtual protected\] void AbstractRunner::init() {#init}

Reimplement this to run any initialization routines on first load. Because it is executed in the runner's thread, it will not block the UI and is thus preferred. By default, it calls [reloadConfiguration](krunner-abstractrunner.md#reloadConfiguration)();

Until the runner is initialized, it will not be queried by the [RunnerManager](krunner-runnermanager.md).

### bool AbstractRunner::isMatchingSuspended() const {#isMatchingSuspended}

Returns true if the runner is currently busy with non-interuptable work, signaling that the [RunnerManager](krunner-runnermanager.md) may not query it or read it's config properties

### \[pure virtual\] void AbstractRunner::match(KRunner::RunnerContext &*context*) {#match}

This is the main query method. It should trigger creation of [QueryMatch](krunner-querymatch.md) instances through [RunnerContext::addMatch](krunner-runnercontext.md#addMatch) and [RunnerContext::addMatches](krunner-runnercontext.md#addMatches).

If the runner can run precisely the requested term ([RunnerContext::query](krunner-runnercontext.md#query)()), it should create an exact match by setting the type to RunnerContext::ExactMatch. The first runner that creates a [QueryMatch](krunner-querymatch.md) will be the default runner. Other runner's matches will be suggested in the interface. Non-exact matches should be offered via RunnerContext::PossibleMatch.

The match will be activated via [run](krunner-abstractrunner.md#run)() if the user selects it.

All matches need to be reported once this method returns. Asynchronous runners therefore need to make use of a local event loop to wait for all matches.

It is recommended to use local status data in async runners. The simplest way is to have a separate class doing all the work like so:

```cpp
void MyFancyAsyncRunner::match(RunnerContext &context)
{
    QEventLoop loop;
    MyAsyncWorker worker(context);
    connect(&worker, &MyAsyncWorker::finished, &loop, &MyAsyncWorker::quit);
    worker.work();
    loop.exec();
}
```

Here MyAsyncWorker creates all the matches and calls [RunnerContext::addMatch](krunner-runnercontext.md#addMatch) in some internal slot. It emits the finished() signal once done which will quit the loop and make the match() method return.

Execution of the correct action should be handled in the run method.

> **Warning:** Returning from this method means to end execution of the runner.

*See also* [run](krunner-abstractrunner.md#run)(), [RunnerContext::addMatch](krunner-runnercontext.md#addMatch), [RunnerContext::addMatches](krunner-runnercontext.md#addMatches), [QueryMatch](krunner-querymatch.md)

### QRegularExpression AbstractRunner::matchRegex() const {#matchRegex}

If this regex is set with a non empty pattern it must match the query in order for match being called.

Just like the [minLetterCount](krunner-abstractrunner.md#minLetterCount) property this check is ignored when the runner is in the singleRunnerMode.

In case both the regex and the letter count is set the letter count is checked first.

Returns matchRegex property

*See also* [setMatchRegex](krunner-abstractrunner.md#setMatchRegex)(), hasMatchRegex

### KPluginMetaData AbstractRunner::metadata() const {#metadata}

Returns the plugin metadata for this runner that was passed in the constructor

### \[virtual protected\] QMimeData \*AbstractRunner::mimeDataForMatch(const KRunner::QueryMatch &*match*) {#mimeDataForMatch}

Reimplement this if you want your runner to support serialization and drag and drop. By default, this sets the [QMimeData](https://doc.qt.io/qt-6/qmimedata.html) urls to the ones specified in [QueryMatch::urls](krunner-querymatch.md#urls)

### int AbstractRunner::minLetterCount() const {#minLetterCount}

This is the minimum letter count for the query. If the query is shorter than this value and [KRunner](krunner-module.md) is not in the singleRunnerMode, match method is not called. This can be set using the X-Plasma-Runner-Min-Letter-Count property or the [setMinLetterCount](krunner-abstractrunner.md#setMinLetterCount) method. The default value is 0.

*See also* [setMinLetterCount](krunner-abstractrunner.md#setMinLetterCount), [match](krunner-abstractrunner.md#match)

### QString AbstractRunner::name() const {#name}

Returns the translated name from the runner's metadata

### \[signal\] void AbstractRunner::prepare() {#prepare}

This signal is emitted when matching is about to commence, giving runners an opportunity to prepare themselves, e.g. loading data sets or preparing IPC or network connections. Things that should be loaded once and remain extant for the lifespan of the [AbstractRunner](krunner-abstractrunner.md) should be done in [init](krunner-abstractrunner.md#init)().

*See also* [init](krunner-abstractrunner.md#init)()

### \[virtual\] void AbstractRunner::reloadConfiguration() {#reloadConfiguration}

Reloads the runner's configuration. This is called when it's KCM in the PluginSelector is applied.

This function may be used to set for example using [setMatchRegex](krunner-abstractrunner.md#setMatchRegex), [setMinLetterCount](krunner-abstractrunner.md#setMinLetterCount) or [setTriggerWords](krunner-abstractrunner.md#setTriggerWords).

Also, syntaxes should be updated when this method is called.

While reloading the config, matching is suspended.

### \[virtual\] void AbstractRunner::run(const KRunner::RunnerContext &*context*, const KRunner::QueryMatch &*match*) {#run}

Called whenever an exact or possible match associated with this runner is triggered.

`context` The context in which the match is triggered, i.e. for which the match was created. `match` The actual match to run/execute.

### void AbstractRunner::setMatchRegex(const QRegularExpression &*regex*) {#setMatchRegex}

Set the [matchRegex](krunner-abstractrunner.md#matchRegex) property

*See also* [matchRegex](krunner-abstractrunner.md#matchRegex)()

### void AbstractRunner::setMinLetterCount(int *count*) {#setMinLetterCount}

Set the [minLetterCount](krunner-abstractrunner.md#minLetterCount) property

`count`

*See also* [minLetterCount](krunner-abstractrunner.md#minLetterCount)()

### \[protected\] void AbstractRunner::setSyntaxes(const QList\<KRunner::RunnerSyntax\> &*syntaxes*) {#setSyntaxes}

Sets the list of syntaxes; passing in an empty list effectively clears the syntaxes.

`the` syntaxes to register for this runner

*See also* [syntaxes](krunner-abstractrunner.md#syntaxes)()

### void AbstractRunner::setTriggerWords(const QStringList &*triggerWords*) {#setTriggerWords}

Constructs internally a regex which requires the query to start with the trigger words. Multiple words are concatenated with or, for instance: "^word1\|word2\|word3". The trigger words are internally escaped. Also the [minLetterCount](krunner-abstractrunner.md#minLetterCount) is set to the shortest word in the list.

*See also* [matchRegex](krunner-abstractrunner.md#matchRegex)

### \[protected\] void AbstractRunner::suspendMatching(bool *suspend*) {#suspendMatching}

Sets whether or not the runner is available for match requests. Useful to prevent queries when the runner is in a busy state.

> **Note:** Do not permanently suspend the runner. This is only intended as a temporary measure to avoid useless queries being launched or async fetching of config/data being interfered with.

### QList\<KRunner::RunnerSyntax\> AbstractRunner::syntaxes() const {#syntaxes}

Returns the syntaxes the runner has registered that it accepts and understands

*See also* [setSyntaxes](krunner-abstractrunner.md#setSyntaxes)()

### \[signal\] void AbstractRunner::teardown() {#teardown}

This signal is emitted when a session of matches is complete, giving runners the opportunity to tear down anything set up as a result of the [prepare](krunner-abstractrunner.md#prepare)() method.
