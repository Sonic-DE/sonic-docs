---
title: "KRunner::RunnerManager Class"
description: "The RunnerManager class decides what installed runners are runnable, and their ratings. It is the main proxy to the runners."
---

# KRunner::RunnerManager Class

The [RunnerManager](krunner-runnermanager.md) class decides what installed runners are runnable, and their ratings. It is the main proxy to the runners. [More...](#details)

- **Header:** `#include <KRunner/RunnerManager>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Runner)`  
  `target_link_libraries(mytarget PRIVATE KF6::Runner)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](krunner-runnermanager-members.md)

## Properties

- [\[read-only\] history : QStringList](#history-prop)
- [historyEnabled : bool](#historyEnabled-prop)
- [\[read-only\] querying : bool](#querying-prop)

## Public Functions

- [RunnerManager(QObject \*parent = nullptr)](#RunnerManager)
- [RunnerManager(const KConfigGroup &pluginConfigGroup, const KConfigGroup &stateGroup, QObject \*parent)](#RunnerManager-1) (since 6.0)
- [QString getHistorySuggestion(const QString &typedQuery) const](#getHistorySuggestion)
- [QStringList history() const](#history)
- [bool historyEnabled()](#historyEnabled)
- [KRunner::AbstractRunner \*loadRunner(const KPluginMetaData &pluginMetaData)](#loadRunner)
- [QList\<KRunner::QueryMatch\> matches() const](#matches)
- [QMimeData \*mimeDataForMatch(const KRunner::QueryMatch &match) const](#mimeDataForMatch)
- [QString query() const](#query)
- [bool querying() const](#querying) (since 6.7)
- [void reloadConfiguration()](#reloadConfiguration)
- [void removeFromHistory(int index)](#removeFromHistory)
- [bool run(const KRunner::QueryMatch &match, const KRunner::Action &action = {})](#run) (since 6.0)
- [KRunner::AbstractRunner \*runner(const QString &pluginId) const](#runner)
- [QList\<KRunner::AbstractRunner \*\> runners() const](#runners)
- [KRunner::RunnerContext \*searchContext() const](#searchContext)
- [void setAllowedRunners(const QStringList &runners)](#setAllowedRunners)
- [void setHistoryEnabled(bool enabled)](#setHistoryEnabled) (since 6.0)

## Public Slots

- [void launchQuery(const QString &term, const QString &runnerId = QString())](#launchQuery)
- [void matchSessionComplete()](#matchSessionComplete)
- [void reset()](#reset)
- [void setupMatchSession()](#setupMatchSession)

## Signals

- [void historyChanged()](#historyChanged) (since 6.21)
- [void historyEnabledChanged()](#historyEnabledChanged)
- [void matchesChanged(const QList\<KRunner::QueryMatch\> &matches)](#matchesChanged)
- [void queryFinished()](#queryFinished)
- [void queryingChanged()](#queryingChanged) (since 6.7)
- [void requestUpdateQueryString(const QString &term, int cursorPosition)](#requestUpdateQueryString) (since 6.0)

## Static Public Members

- [QList\<KPluginMetaData\> runnerMetaDataList()](#runnerMetaDataList)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### \[read-only\] history : QStringList {#history-prop}

**Access functions:**

- `QStringList` **[history](krunner-runnermanager.md#history)**() const

**Notifier signal:**

- `void` **[historyChanged](krunner-runnermanager.md#historyChanged)**()

### historyEnabled : bool {#historyEnabled-prop}

**Access functions:**

- `bool` **[historyEnabled](krunner-runnermanager.md#historyEnabled)**()
- `void` **[setHistoryEnabled](krunner-runnermanager.md#setHistoryEnabled)**(`bool` *enabled*)

**Notifier signal:**

- `void` **[historyEnabledChanged](krunner-runnermanager.md#historyEnabledChanged)**()

### \[read-only\] querying : bool {#querying-prop}

**Access functions:**

- `bool` **[querying](krunner-runnermanager.md#querying)**() const

**Notifier signal:**

- `void` **[queryingChanged](krunner-runnermanager.md#queryingChanged)**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] RunnerManager::RunnerManager(QObject \**parent* = nullptr) {#RunnerManager}

Constructs a [RunnerManager](krunner-runnermanager.md) using the default locations for state/plugin config

### \[explicit, since 6.0\] RunnerManager::RunnerManager(const KConfigGroup &*pluginConfigGroup*, const KConfigGroup &*stateGroup*, QObject \**parent*) {#RunnerManager-1}

Constructs a [RunnerManager](krunner-runnermanager.md) with the given parameters

`configurationGroup` Config group used for reading enabled plugins

`stateGroup` Config group used for storing history

This function was introduced in Qt 6.0.

### \[invokable\] QString RunnerManager::getHistorySuggestion(const QString &*typedQuery*) const {#getHistorySuggestion}

Get the suggested history entry for the typed query. If no entry is found an empty string is returned.

`typedQuery`

Returns completion for typedQuery

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### QStringList RunnerManager::history() const {#history}

Returns History of this runner for the current activity. If the [RunnerManager](krunner-runnermanager.md) is not history aware the global entries will be returned.

> **Note:** Getter function for property [history](krunner-runnermanager.md#history-prop).

### \[signal, since 6.21\] void RunnerManager::historyChanged() {#historyChanged}

Emitted when the history has changed

> **Note:** Notifier signal for property [history](krunner-runnermanager.md#history-prop).

This function was introduced in Qt 6.21.

### bool RunnerManager::historyEnabled() {#historyEnabled}

If history completion is enabled, the default value is true.

> **Note:** Getter function for property [historyEnabled](krunner-runnermanager.md#historyEnabled-prop).

*See also* [setHistoryEnabled](krunner-runnermanager.md#setHistoryEnabled)()

### \[signal\] void RunnerManager::historyEnabledChanged() {#historyEnabledChanged}

> **Note:** Notifier signal for property [historyEnabled](krunner-runnermanager.md#historyEnabled-prop).

*See also* [historyEnabled](krunner-runnermanager.md#historyEnabled)

### \[slot\] void RunnerManager::launchQuery(const QString &*term*, const QString &*runnerId* = QString()) {#launchQuery}

Launch a query, this will create threads and return immediately. When the information will be available can be known using the [matchesChanged](krunner-runnermanager.md#matchesChanged) signal.

`term` the term we want to find matches for

`runnerId` optional, if only one specific runner is to be used; providing an id will put the manager into single runner mode

### KRunner::AbstractRunner \*RunnerManager::loadRunner(const KPluginMetaData &*pluginMetaData*) {#loadRunner}

Attempts to add the [AbstractRunner](krunner-abstractrunner.md) plugin represented by the plugin info passed in. Usually one can simply let the configuration of plugins handle loading Runner plugins, but in cases where specific runners should be loaded this allows for that to take place

> **Note:** Consider using [setAllowedRunners](krunner-runnermanager.md#setAllowedRunners) in case you want to only allow specific runners

`pluginMetaData` the metaData to use to load the plugin

Returns the loaded runner or nullptr

### \[slot\] void RunnerManager::matchSessionComplete() {#matchSessionComplete}

Call this method when the query session is finished for the time being.

*See also* prepareForMatchSession

### QList\<KRunner::QueryMatch\> RunnerManager::matches() const {#matches}

Retrieves all available matches found so far for the previously launched query

### \[signal\] void RunnerManager::matchesChanged(const QList\<KRunner::QueryMatch\> &*matches*) {#matchesChanged}

Emitted each time a new match is added to the list

### QMimeData \*RunnerManager::mimeDataForMatch(const KRunner::QueryMatch &*match*) const {#mimeDataForMatch}

Returns mime data of the specified match

### QString RunnerManager::query() const {#query}

Returns the current query term set in [launchQuery](krunner-runnermanager.md#launchQuery)

### \[signal\] void RunnerManager::queryFinished() {#queryFinished}

Emitted when the [launchQuery](krunner-runnermanager.md#launchQuery) finish

### \[since 6.7\] bool RunnerManager::querying() const {#querying}

If the [RunnerManager](krunner-runnermanager.md) is currently querying

> **Note:** Getter function for property [querying](krunner-runnermanager.md#querying-prop).

This function was introduced in Qt 6.7.

### \[signal, since 6.7\] void RunnerManager::queryingChanged() {#queryingChanged}

Emitted when the querying status has changed

> **Note:** Notifier signal for property [querying](krunner-runnermanager.md#querying-prop).

This function was introduced in Qt 6.7.

### void RunnerManager::reloadConfiguration() {#reloadConfiguration}

Causes a reload of the current configuration

This gets called automatically when the config in the KCM is saved

### \[invokable\] void RunnerManager::removeFromHistory(int *index*) {#removeFromHistory}

Delete the given index from the history.

`historyEntry`

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[signal, since 6.0\] void RunnerManager::requestUpdateQueryString(const QString &*term*, int *cursorPosition*) {#requestUpdateQueryString}

Put the given search term in the [KRunner](krunner-module.md) search field

`term` The term that should be displayed

`cursorPosition` Where the cursor should be positioned

This function was introduced in Qt 6.0.

### \[slot\] void RunnerManager::reset() {#reset}

Reset the current data and stops the query

### \[since 6.0\] bool RunnerManager::run(const KRunner::QueryMatch &*match*, const KRunner::Action &*action* = {}) {#run}

Runs a given match. This also respects the extra handling for the InformationalMatch.

This also handles the history automatically

`match` the match to be executed

`selectedAction` the action returned by [QueryMatch::actions](krunner-querymatch.md#actions) that has been selected by the user, nullptr if none

Returns if the RunnerWindow should close

This function was introduced in Qt 6.0.

### KRunner::AbstractRunner \*RunnerManager::runner(const QString &*pluginId*) const {#runner}

Finds and returns a loaded runner or a nullptr

`pluginId` the name of the runner plugin

Returns Pointer to the runner

### \[static\] QList\<KPluginMetaData\> RunnerManager::runnerMetaDataList() {#runnerMetaDataList}

Returns metadata list of all known Runner plugins

### QList\<KRunner::AbstractRunner \*\> RunnerManager::runners() const {#runners}

Returns the list of all currently loaded runners

### KRunner::RunnerContext \*RunnerManager::searchContext() const {#searchContext}

Retrieves the current context

Returns pointer to the current context

### void RunnerManager::setAllowedRunners(const QStringList &*runners*) {#setAllowedRunners}

Sets a whitelist for the plugins that can be loaded by this manager.

Runners that are disabled through the config will not be loaded.

`plugins` the plugin names of allowed runners

### \[since 6.0\] void RunnerManager::setHistoryEnabled(bool *enabled*) {#setHistoryEnabled}

Enables/disabled the history feature for the [RunnerManager](krunner-runnermanager.md) instance. The value will not be persisted and is only kept during the object's lifetime.

> **Note:** Setter function for property [historyEnabled](krunner-runnermanager.md#historyEnabled-prop).

This function was introduced in Qt 6.0.

*See also* [historyEnabled](krunner-runnermanager.md#historyEnabled)()

### \[slot\] void RunnerManager::setupMatchSession() {#setupMatchSession}

Call this method when the runners should be prepared for a query session. Call [matchSessionComplete](krunner-runnermanager.md#matchSessionComplete) when the query session is finished for the time being.

*See also* [matchSessionComplete](krunner-runnermanager.md#matchSessionComplete)
