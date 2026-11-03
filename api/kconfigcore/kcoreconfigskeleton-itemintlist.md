---
title: "KCoreConfigSkeleton::ItemIntList Class"
description: "Class for handling an integer list preferences item."
---

# KCoreConfigSkeleton::ItemIntList Class

Class for handling an integer list preferences item. [More...](#details)

- **Header:** `#include <ItemIntList>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md)

[List of all members, including inherited members](kcoreconfigskeleton-itemintlist-members.md)

## Public Functions

- [ItemIntList(const QString &\_group, const QString &\_key, QList\<int\> &reference, const QList\<int\> &defaultValue = QList\<int\>())](#ItemIntList)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemIntList::ItemIntList(const QString &*\_group*, const QString &*\_key*, QList\<int\> &*reference*, const QList\<int\> &*defaultValue* = QList\<int\>()) {#ItemIntList}

Constructs an int list item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.
