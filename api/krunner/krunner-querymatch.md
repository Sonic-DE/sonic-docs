---
title: "KRunner::QueryMatch Class"
description: "A match returned by an AbstractRunner in response to a given RunnerContext."
---

# KRunner::QueryMatch Class

A match returned by an [AbstractRunner](krunner-abstractrunner.md) in response to a given [RunnerContext](krunner-runnercontext.md). [More...](#details)

- **Header:** `#include <KRunner/QueryMatch>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Runner)`  
  `target_link_libraries(mytarget PRIVATE KF6::Runner)`

[List of all members, including inherited members](krunner-querymatch-members.md)

## Public Types

- [enum QueryMatch::CategoryRelevance](#CategoryRelevance-enum)

## Public Functions

- [QueryMatch(KRunner::AbstractRunner \*runner = nullptr)](#QueryMatch)
- [QList\<KRunner::Action\> actions() const](#actions)
- [void addAction(const KRunner::Action &action)](#addAction)
- [qreal categoryRelevance() const](#categoryRelevance) (since 6.0)
- [QVariant data() const](#data)
- [QIcon icon() const](#icon)
- [QString iconName() const](#iconName)
- [QString id() const](#id)
- [bool isEnabled() const](#isEnabled)
- [bool isMultiLine() const](#isMultiLine)
- [bool isValid() const](#isValid)
- [QString matchCategory() const](#matchCategory)
- [qreal relevance() const](#relevance)
- [KRunner::AbstractRunner \*runner() const](#runner)
- [KRunner::Action selectedAction() const](#selectedAction)
- [void setActions(const QList\<KRunner::Action\> &actions)](#setActions)
- [void setCategoryRelevance(KRunner::QueryMatch::CategoryRelevance relevance)](#setCategoryRelevance) (since 6.0)
- [void setData(const QVariant &data)](#setData)
- [void setEnabled(bool enable)](#setEnabled)
- [void setIcon(const QIcon &icon)](#setIcon)
- [void setIconName(const QString &iconName)](#setIconName)
- [void setId(const QString &id)](#setId)
- [void setMatchCategory(const QString &category)](#setMatchCategory)
- [void setMultiLine(bool multiLine)](#setMultiLine)
- [void setRelevance(qreal relevance)](#setRelevance)
- [void setSubtext(const QString &text)](#setSubtext)
- [void setText(const QString &text)](#setText)
- [void setUrls(const QList\<QUrl\> &urls)](#setUrls)
- [QString subtext() const](#subtext)
- [QString text() const](#text)
- [QList\<QUrl\> urls() const](#urls)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum QueryMatch::CategoryRelevance {#CategoryRelevance-enum}

Helper for reading standardized category relevance values

| Constant |   |
| --- | --- |
| `KRunner::QueryMatch::CategoryRelevance::Lowest` | `0` |
| `KRunner::QueryMatch::CategoryRelevance::Low` | `30` |
| `KRunner::QueryMatch::CategoryRelevance::Moderate` | `50` |
| `KRunner::QueryMatch::CategoryRelevance::High` | `70` |
| `KRunner::QueryMatch::CategoryRelevance::Highest` | `100` |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] QueryMatch::QueryMatch(KRunner::AbstractRunner \**runner* = nullptr) {#QueryMatch}

Constructs a PossibleMatch associated with a given [RunnerContext](krunner-runnercontext.md) and runner.

`runner` the runner this match belongs to

### QList\<KRunner::Action\> QueryMatch::actions() const {#actions}

List of actions set for this match Returns actions

*See also* [setActions](krunner-querymatch.md#setActions)()

### void QueryMatch::addAction(const KRunner::Action &*action*) {#addAction}

Adds an action to this match

*See also* [setActions](krunner-querymatch.md#setActions)

### \[since 6.0\] qreal QueryMatch::categoryRelevance() const {#categoryRelevance}

Category relevance for this match

This function was introduced in Qt 6.0.

*See also* [setCategoryRelevance](krunner-querymatch.md#setCategoryRelevance)()

### QVariant QueryMatch::data() const {#data}

Returns the data associated with this match; usually runner-specific

*See also* [setData](krunner-querymatch.md#setData)()

### QIcon QueryMatch::icon() const {#icon}

Returns the icon for this match

*See also* [setIcon](krunner-querymatch.md#setIcon)()

### QString QueryMatch::iconName() const {#iconName}

Returns the name of the icon for this match

*See also* [setIconName](krunner-querymatch.md#setIconName)()

### QString QueryMatch::id() const {#id}

Returns a string that can be used as an ID for this match, even between different queries. It is based in part on the source of the match (the [AbstractRunner](krunner-abstractrunner.md)) and distinguishing information provided by the runner, ensuring global uniqueness as well as consistency between query matches.

*See also* [setId](krunner-querymatch.md#setId)()

### bool QueryMatch::isEnabled() const {#isEnabled}

Returns true if the match is enabled and therefore runnable, otherwise false

### bool QueryMatch::isMultiLine() const {#isMultiLine}

If the text should be displayed as a multiLine string If no explicit value is set set using setMultiline it will default to false Returns bool

### bool QueryMatch::isValid() const {#isValid}

Returns true if the match is valid and can therefore be run, an invalid match does not have an associated [AbstractRunner](krunner-abstractrunner.md)

### QString QueryMatch::matchCategory() const {#matchCategory}

Extra information about the match which can be used to categorize the type.

The default is [AbstractRunner::name](krunner-abstractrunner.md#name)

*See also* [setMatchCategory](krunner-querymatch.md#setMatchCategory)()

### qreal QueryMatch::relevance() const {#relevance}

The relevance of this action to the search. By default, the relevance is 1.

Returns a number between 0 and 1

*See also* [setRelevance](krunner-querymatch.md#setRelevance)()

### KRunner::AbstractRunner \*QueryMatch::runner() const {#runner}

Returns the runner associated with this action

### KRunner::Action QueryMatch::selectedAction() const {#selectedAction}

The action that the user has selected when running the match. This returns a nullptr if no action was selected.

### void QueryMatch::setActions(const QList\<KRunner::Action\> &*actions*) {#setActions}

Set the actions for this match. This method allows you to set the actions inside of the [AbstractRunner::match](krunner-abstractrunner.md#match) method

*See also* RunnerManager::actionsForMatch

### \[since 6.0\] void QueryMatch::setCategoryRelevance(KRunner::QueryMatch::CategoryRelevance *relevance*) {#setCategoryRelevance}

Relevance for matches in the category. The match with the highest relevance is respected for the entire category. This value only affects the sorting of categories and not the sorting within the category. Use [setRelevance](krunner-querymatch.md#setRelevance) for this. The value should be from 0 to 100.

This function was introduced in Qt 6.0.

*See also* [categoryRelevance](krunner-querymatch.md#categoryRelevance)()

### void QueryMatch::setData(const QVariant &*data*) {#setData}

Sets data to be used internally by the runner's [AbstractRunner::run](krunner-abstractrunner.md#run) implementation.

When set, it is also used to form part of the id for this match. If that is inappropriate as an id, the runner may generate its own id and set that with [setId](krunner-querymatch.md#setId)

*See also* [data](krunner-querymatch.md#data)()

### void QueryMatch::setEnabled(bool *enable*) {#setEnabled}

Sets whether or not this match can be activited

`enable` true if the match is enabled and therefore runnable

*See also* [isEnabled](krunner-querymatch.md#isEnabled)()

### void QueryMatch::setIcon(const QIcon &*icon*) {#setIcon}

Sets the icon associated with this match

Prefer using [setIconName](krunner-querymatch.md#setIconName).

`icon` the icon to show along with the match

*See also* [icon](krunner-querymatch.md#icon)()

### void QueryMatch::setIconName(const QString &*iconName*) {#setIconName}

Sets the icon name associated with this match

`icon` the name of the icon to show along with the match

*See also* [iconName](krunner-querymatch.md#iconName)()

### void QueryMatch::setId(const QString &*id*) {#setId}

Sets the id for this match; useful if the id does not match [data](krunner-querymatch.md#data)().toString(). The id must be unique to all matches from this runner, and should remain constant for the same query for best results.

If the "X-Plasma-Runner-Unique-Results" property from the metadata is set to true, the runnerId will not be prepended to the ID. This allows [KRunner](krunner-module.md) to de-duplicate results from different runners. In case the runner's matches are less specific than ones from other runners, the "X-Plasma-Runner-Weak-Results" property can be set so that duplicates from this runner are removed.

`id` the new identifying string to use to refer to this entry

*See also* [id](krunner-querymatch.md#id)()

### void QueryMatch::setMatchCategory(const QString &*category*) {#setMatchCategory}

Sets information about the type of the match which is used to group the matches.

This string should be translated as it is displayed in an UI. The default is [AbstractRunner::name](krunner-abstractrunner.md#name)

*See also* [matchCategory](krunner-querymatch.md#matchCategory)()

### void QueryMatch::setMultiLine(bool *multiLine*) {#setMultiLine}

Set if the text should be displayed as a multiLine string

`multiLine`

*See also* [isMultiLine](krunner-querymatch.md#isMultiLine)()

### void QueryMatch::setRelevance(qreal *relevance*) {#setRelevance}

Sets the relevance of this action for the search it was created for.

`relevance` a number between 0 and 1.

*See also* [relevance](krunner-querymatch.md#relevance)()

### void QueryMatch::setSubtext(const QString &*text*) {#setSubtext}

Sets the descriptive text for this match; can be longer than the main title text

`text` the text to use as the description

*See also* [subtext](krunner-querymatch.md#subtext)()

### void QueryMatch::setText(const QString &*text*) {#setText}

Sets the main title text for this match; should be short enough to fit nicely on one line in a user interface For styled and multiline text, [setMultiLine](krunner-querymatch.md#setMultiLine) should be set to true

`text` the text to use as the title

*See also* [text](krunner-querymatch.md#text)()

### void QueryMatch::setUrls(const QList\<QUrl\> &*urls*) {#setUrls}

Sets the urls, if any, associated with this match

*See also* [urls](krunner-querymatch.md#urls)()

### QString QueryMatch::subtext() const {#subtext}

Returns the descriptive text for this match

*See also* [setSubtext](krunner-querymatch.md#setSubtext)()

### QString QueryMatch::text() const {#text}

Returns the title text for this match

*See also* [setText](krunner-querymatch.md#setText)()

### QList\<QUrl\> QueryMatch::urls() const {#urls}

Returns the urls for this match, empty list if none These will be used in the default implementation of [AbstractRunner::mimeDataForMatch](krunner-abstractrunner.md#mimeDataForMatch)

*See also* [setUrls](krunner-querymatch.md#setUrls)()
