---
title: "KCompletionMatches Class"
description: "List for keeping matches returned from KCompletion."
---

# KCompletionMatches Class

List for keeping matches returned from [KCompletion](kcompletion-module.md). [More...](#details)

- **Header:** `#include <KCompletionMatches>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Completion)`  
  `target_link_libraries(mytarget PRIVATE KF6::Completion)`

[List of all members, including inherited members](kcompletionmatches-members.md)

## Public Functions

- [KCompletionMatches(bool sort)](#KCompletionMatches)
- [QStringList list(bool sort = true) const](#list)
- [void removeDuplicates()](#removeDuplicates)
- [bool sorting() const](#sorting)

## Detailed Description {#details}

This structure is returned by KCompletion::allWeightedMatches(). It also keeps the weight of the matches, allowing you to modify some matches or merge them with matches from another call to allWeightedMatches(), and sort the matches after that in order to have the matches ordered correctly.

Example (a simplified example of what Konqueror's completion does):

```cpp
KCompletionMatches matches = completion->allWeightedMatches(location);
if(!location.startsWith("www."))
    matches += completion->allWeightedmatches("www." + location");
matches.removeDuplicates();
QStringList list = matches.list();
```

## Member Function Documentation {#member-function-documentation}

### KCompletionMatches::KCompletionMatches(bool *sort*) {#KCompletionMatches}

Default constructor.

`sort` if false, the matches won't be sorted before the conversion, use only if you're sure the sorting is not needed

### QStringList KCompletionMatches::list(bool *sort* = true) const {#list}

Returns the matches as a [QStringList](https://doc.qt.io/qt-6/qstringlist.html).

`sort` if false, the matches won't be sorted before the conversion, use only if you're sure the sorting is not needed

Returns the list of matches

### void KCompletionMatches::removeDuplicates() {#removeDuplicates}

Removes duplicate matches. Needed only when you merged several matches results and there's a possibility of duplicates.

### bool KCompletionMatches::sorting() const {#sorting}

If sorting() returns `false`, the matches aren't sorted by their weight, even if `true` is passed to [list](kcompletionmatches.md#list)().

`true` if the matches won't be sorted

## Related Non-Members {#related-non-members}

### KCompletionMatchesList {#KCompletionMatchesList-typedef}
