---
title: "KNSCore::TagsFilterChecker Class"
description: "Apply simple filtering logic to a list of tags."
---

# KNSCore::TagsFilterChecker Class

Apply simple filtering logic to a list of tags. [More...](#details)

- **Header:** `#include <TagsFilterChecker>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NewStuff)`  
  `target_link_libraries(mytarget PRIVATE KF6::NewStuff)`

[List of all members, including inherited members](knscore-tagsfilterchecker-members.md)

## Public Functions

- [TagsFilterChecker(const QStringList &tagFilter)](#TagsFilterChecker)
- [bool filterAccepts(const QStringList &tags)](#filterAccepts)

## Detailed Description {#details}

== Examples of specifying tag filters == Value for tag "tagname" must be exactly "tagdata": tagname==tagdata

Value for tag "tagname" must be different from "tagdata": tagname!=tagdata

== Tag filter list == A tag filter list is a string list of filters as shown above, and a combination of which might look like:

- ghns\_excluded!=1 - data\#\#mimetype==application/cbr+zip - data\#\#mimetype==application/cbr+rar

which would filter out anything which has ghns\_excluded set to 1, and anything where the value of data\#\#mimetype does not equal either "application/cbr+zip" or "application/cbr+rar". Notice in particular the two data\#\#mimetype entries. Use this for when a tag may have multiple values.

The value does not current support wildcards. The list should be considered a binary AND operation (that is, all filter entries must match for the data entry to be included in the return data)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] TagsFilterChecker::TagsFilterChecker(const QStringList &*tagFilter*) {#TagsFilterChecker}

Constructs an instance of the tags filter checker, prepopulated with the list of tag filters in the tagFilter parameter.

`tagFilter` The list of tag filters

### bool TagsFilterChecker::filterAccepts(const QStringList &*tags*) {#filterAccepts}

Check whether the filter list accepts the passed list of tags

`tags` A list of tags in the form of key=value strings

Returns True if the filter accepts the list, false if not
