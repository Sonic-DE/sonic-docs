---
title: "KCoreConfigSkeleton::ItemBool Class"
description: "Class for handling a bool preferences item."
---

# KCoreConfigSkeleton::ItemBool Class

Class for handling a bool preferences item. [More...](#details)

- **Header:** `#include <ItemBool>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md)

[List of all members, including inherited members](kcoreconfigskeleton-itembool-members.md)

## Public Functions

- [ItemBool(const QString &\_group, const QString &\_key, bool &reference, bool defaultValue = true)](#ItemBool)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemBool::ItemBool(const QString &*\_group*, const QString &*\_key*, bool &*reference*, bool *defaultValue* = true) {#ItemBool}

Constructs a bool item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.
