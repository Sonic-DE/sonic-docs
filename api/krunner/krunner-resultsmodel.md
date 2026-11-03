---
title: "KRunner::ResultsModel Class"
description: "A model that exposes and sorts results for a given query. This class was introduced in Qt 6.0."
---

# KRunner::ResultsModel Class

A model that exposes and sorts results for a given query. This class was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <KRunner/ResultsModel>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Runner)`  
  `target_link_libraries(mytarget PRIVATE KF6::Runner)`
- **Inherits:** [QSortFilterProxyModel](https://doc.qt.io/qt-6/qsortfilterproxymodel.html)

[List of all members, including inherited members](krunner-resultsmodel-members.md)

## Public Types

- [enum ResultsModel::Roles](#Roles-enum)

## Properties

- [favoriteIds : QStringList](#favoriteIds-prop)
- [limit : int](#limit-prop)
- [queryString : QString](#queryString-prop)
- [\[read-only\] querying : bool](#querying-prop)
- [runnerManager : KRunner::RunnerManager\*](#runnerManager-prop)
- [singleRunner : QString](#singleRunner-prop)
- [\[read-only\] singleRunnerMetaData : KPluginMetaData](#singleRunnerMetaData-prop)

## Public Functions

- [ResultsModel(QObject \*parent = nullptr)](#ResultsModel)
- [ResultsModel(const KConfigGroup &configGroup, const KConfigGroup &stateConfigGroup, QObject \*parent = nullptr)](#ResultsModel-1)
- [void clear()](#clear)
- [QMimeData \*getMimeData(const QModelIndex &idx) const](#getMimeData)
- [KRunner::QueryMatch getQueryMatch(const QModelIndex &idx) const](#getQueryMatch)
- [bool run(const QModelIndex &idx)](#run)
- [bool runAction(const QModelIndex &idx, int actionNumber)](#runAction)
- [void setFavoriteIds(const QStringList &ids)](#setFavoriteIds)
- [void setRunnerManager(KRunner::RunnerManager \*manager)](#setRunnerManager) (since 6.9)

## Signals

- [void queryStringChangeRequested(const QString &queryString, int pos)](#queryStringChangeRequested)
- [void runnerManagerChanged()](#runnerManagerChanged) (since 6.9)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum ResultsModel::Roles {#Roles-enum}

| Constant |   |
| --- | --- |
| `KRunner::ResultsModel::IdRole` | `Qt::UserRole + 1` |
| `KRunner::ResultsModel::CategoryRelevanceRole` | `258` |
| `KRunner::ResultsModel::RelevanceRole` | `259` |
| `KRunner::ResultsModel::EnabledRole` | `260` |
| `KRunner::ResultsModel::CategoryRole` | `261` |
| `KRunner::ResultsModel::SubtextRole` | `262` |
| `KRunner::ResultsModel::ActionsRole` | `263` |
| `KRunner::ResultsModel::MultiLineRole` | `264` |
| `KRunner::ResultsModel::UrlsRole` | `265` |

## Property Documentation {#property-documentation}

### favoriteIds : QStringList {#favoriteIds-prop}

**Access functions:**

- `QStringList` **favoriteIds**() const
- `void` **[setFavoriteIds](krunner-resultsmodel.md#setFavoriteIds)**(const `QStringList` &*ids*)

**Notifier signal:**

- `void` **favoriteIdsChanged**()

### limit : int {#limit-prop}

The preferred maximum number of matches in the model

If there are lots of results from different categories, the limit can be slightly exceeded.

Default is 0, which means no limit.

**Access functions:**

- `int` **limit**() const
- `void` **setLimit**(`int` *limit*)
- `void` **resetLimit**()

**Notifier signal:**

- `void` **limitChanged**()

### queryString : QString {#queryString-prop}

The query string to run

**Access functions:**

- `QString` **queryString**() const
- `void` **setQueryString**(const `QString` &*queryString*)

**Notifier signal:**

- `void` **queryStringChanged**(const `QString` &*queryString*)

### \[read-only\] querying : bool {#querying-prop}

Whether the query is currently being run

This can be used to show a busy indicator

**Access functions:**

- `bool` **querying**() const

**Notifier signal:**

- `void` **queryingChanged**()

### runnerManager : KRunner::RunnerManager\* {#runnerManager-prop}

**Access functions:**

- `KRunner::RunnerManager` \***runnerManager**() const
- `void` **[setRunnerManager](krunner-resultsmodel.md#setRunnerManager)**(`KRunner::RunnerManager` \**manager*)

**Notifier signal:**

- `void` **[runnerManagerChanged](krunner-resultsmodel.md#runnerManagerChanged)**()

### singleRunner : QString {#singleRunner-prop}

The single runner to use for querying in single runner mode

Defaults to empty string which means all runners

**Access functions:**

- `QString` **singleRunner**() const
- `void` **setSingleRunner**(const `QString` &*runner*)

**Notifier signal:**

- `void` **singleRunnerChanged**()

### \[read-only\] singleRunnerMetaData : KPluginMetaData {#singleRunnerMetaData-prop}

**Access functions:**

- `KPluginMetaData` **singleRunnerMetaData**() const

**Notifier signal:**

- `void` **[singleRunnerChanged](krunner-resultsmodel.md#singleRunner-prop)**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ResultsModel::ResultsModel(QObject \**parent* = nullptr) {#ResultsModel}

### \[explicit\] ResultsModel::ResultsModel(const KConfigGroup &*configGroup*, const KConfigGroup &*stateConfigGroup*, QObject \**parent* = nullptr) {#ResultsModel-1}

### \[invokable\] void ResultsModel::clear() {#clear}

Clears the model content and resets the runner context, i.e. no new items will appear.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] QMimeData \*ResultsModel::getMimeData(const QModelIndex &*idx*) const {#getMimeData}

Get mime data for the result at given model index `idx`

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### KRunner::QueryMatch ResultsModel::getQueryMatch(const QModelIndex &*idx*) const {#getQueryMatch}

Get match for the result at given model index `idx`

### \[signal\] void ResultsModel::queryStringChangeRequested(const QString &*queryString*, int *pos*) {#queryStringChangeRequested}

This signal is emitted when a an InformationalMatch is run, and it is advised to update the search term, e.g. used for calculator runner results

### \[invokable\] bool ResultsModel::run(const QModelIndex &*idx*) {#run}

Run the result at the given model index `idx`

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] bool ResultsModel::runAction(const QModelIndex &*idx*, int *actionNumber*) {#runAction}

Run the action `actionNumber` at given model index `idx`

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[signal, since 6.9\] void ResultsModel::runnerManagerChanged() {#runnerManagerChanged}

> **Note:** Notifier signal for property [runnerManager](krunner-resultsmodel.md#runnerManager-prop).

This function was introduced in Qt 6.9.

### void ResultsModel::setFavoriteIds(const QStringList &*ids*) {#setFavoriteIds}

IDs of favorite plugins. Those plugins are always in a fixed order before the other ones.

`ids` KPluginMetaData::pluginId values of plugins

> **Note:** Setter function for property [favoriteIds](krunner-resultsmodel.md#favoriteIds-prop).

*See also* [favoriteIds](krunner-resultsmodel.md#favoriteIds-prop)()

### \[since 6.9\] void ResultsModel::setRunnerManager(KRunner::RunnerManager \**manager*) {#setRunnerManager}

> **Note:** Setter function for property [runnerManager](krunner-resultsmodel.md#runnerManager-prop).

This function was introduced in Qt 6.9.

*See also* [runnerManager](krunner-resultsmodel.md#runnerManager-prop)()
