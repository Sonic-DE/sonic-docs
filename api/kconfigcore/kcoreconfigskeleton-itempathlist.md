---
title: "KCoreConfigSkeleton::ItemPathList Class"
description: "Class for handling a path list preferences item."
---

# KCoreConfigSkeleton::ItemPathList Class

Class for handling a path list preferences item. [More...](#details)

- **Header:** `#include <ItemPathList>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KCoreConfigSkeleton::ItemStringList](kcoreconfigskeleton-itemstringlist.md)

[List of all members, including inherited members](kcoreconfigskeleton-itempathlist-members.md)

## Public Functions

- [ItemPathList(const QString &\_group, const QString &\_key, QStringList &reference, const QStringList &defaultValue = QStringList())](#ItemPathList)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemPathList::ItemPathList(const QString &*\_group*, const QString &*\_key*, QStringList &*reference*, const QStringList &*defaultValue* = QStringList()) {#ItemPathList}

Constructs a path string list item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.
