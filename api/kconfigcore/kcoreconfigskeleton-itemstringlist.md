---
title: "KCoreConfigSkeleton::ItemStringList Class"
description: "Class for handling a string list preferences item."
---

# KCoreConfigSkeleton::ItemStringList Class

Class for handling a string list preferences item. [More...](#details)

- **Header:** `#include <ItemStringList>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md)
- **Inherited By:** [KCoreConfigSkeleton::ItemPathList](kcoreconfigskeleton-itempathlist.md)

[List of all members, including inherited members](kcoreconfigskeleton-itemstringlist-members.md)

## Public Functions

- [ItemStringList(const QString &\_group, const QString &\_key, QStringList &reference, const QStringList &defaultValue = QStringList())](#ItemStringList)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemStringList::ItemStringList(const QString &*\_group*, const QString &*\_key*, QStringList &*reference*, const QStringList &*defaultValue* = QStringList()) {#ItemStringList}

Constructs a string list item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.
