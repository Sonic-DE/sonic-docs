---
title: "KRunner::RunnerContext Class"
description: "The RunnerContext class provides information related to a search, including the search term and collected matches."
---

# KRunner::RunnerContext Class

The [RunnerContext](krunner-runnercontext.md) class provides information related to a search, including the search term and collected matches. [More...](#details)

- **Header:** `#include <KRunner/RunnerContext>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Runner)`  
  `target_link_libraries(mytarget PRIVATE KF6::Runner)`

[List of all members, including inherited members](krunner-runnercontext-members.md)

## Public Functions

- [RunnerContext(KRunner::RunnerManager \*manager = nullptr)](#RunnerContext)
- [bool addMatch(const KRunner::QueryMatch &match)](#addMatch)
- [bool addMatches(const QList\<KRunner::QueryMatch\> &matches)](#addMatches)
- [void ignoreCurrentMatchForHistory() const](#ignoreCurrentMatchForHistory)
- [bool isValid() const](#isValid)
- [QList\<KRunner::QueryMatch\> matches() const](#matches)
- [QString query() const](#query)
- [void requestQueryStringUpdate(const QString &text, int cursorPosition) const](#requestQueryStringUpdate)
- [void setQuery(const QString &term)](#setQuery)
- [bool singleRunnerQueryMode() const](#singleRunnerQueryMode)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] RunnerContext::RunnerContext(KRunner::RunnerManager \**manager* = nullptr) {#RunnerContext}

### bool RunnerContext::addMatch(const KRunner::QueryMatch &*match*) {#addMatch}

Appends a match to the existing list of matches.

If you are going to be adding multiple matches, it is more performant to use [addMatches](krunner-runnercontext.md#addMatches) instead.

`match` the match to add

Returns true if the match was added, false otherwise.

### bool RunnerContext::addMatches(const QList\<KRunner::QueryMatch\> &*matches*) {#addMatches}

Appends lists of matches to the list of matches.

`matches` the matches to add

Returns true if matches were added, false if matches were e.g. outdated

### void RunnerContext::ignoreCurrentMatchForHistory() const {#ignoreCurrentMatchForHistory}

Set this to true in the [AbstractRunner::run](krunner-abstractrunner.md#run) method to prevent the entry from being saved to the history.

### bool RunnerContext::isValid() const {#isValid}

Returnss true if this context is no longer valid and therefore matching using it should abort. While not required to be used within runners, it provides a nice way to avoid unnecessary processing in runners that may run for an extended period (as measured in 10s of ms) and therefore improve the user experience.

### QList\<KRunner::QueryMatch\> RunnerContext::matches() const {#matches}

Retrieves all available matches for the current search term.

Returns a list of matches

### QString RunnerContext::query() const {#query}

Returns the current search query term.

*See also* [setQuery](krunner-runnercontext.md#setQuery)()

### void RunnerContext::requestQueryStringUpdate(const QString &*text*, int *cursorPosition*) const {#requestQueryStringUpdate}

Request that [KRunner](krunner-module.md) updates the query string and stasy open, even after running a match. This method is const so it can be called in a const context.

`text` Text that will be displayed in the search field

`cursorPosition` Position of the cursor, if this is different than the length of the text, the characters between the position and text will be selected

### void RunnerContext::setQuery(const QString &*term*) {#setQuery}

Sets the query term for this object and attempts to determine the type of the search.

*See also* [query](krunner-runnercontext.md#query)()

### bool RunnerContext::singleRunnerQueryMode() const {#singleRunnerQueryMode}

Returns true if the current query is a single runner query
