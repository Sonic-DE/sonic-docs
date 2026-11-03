---
title: "KCoreConfigSkeleton::ItemPath Class"
description: "Class for handling a path preferences item."
---

# KCoreConfigSkeleton::ItemPath Class

Class for handling a path preferences item.

- **Header:** `#include <ItemPath>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KCoreConfigSkeleton::ItemString](kcoreconfigskeleton-itemstring.md)

## Public Functions

- [ItemPath(const QString &\_group, const QString &\_key, QString &reference, const QString &defaultValue = QString())](#ItemPath)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemPath::ItemPath(const QString &*\_group*, const QString &*\_key*, QString &*reference*, const QString &*defaultValue* = QString()) {#ItemPath}

Constructs a path item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.
