---
title: "KCoreConfigSkeleton::ItemPassword Class"
description: "Class for handling a password preferences item."
---

# KCoreConfigSkeleton::ItemPassword Class

Class for handling a password preferences item.

- **Header:** `#include <ItemPassword>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KCoreConfigSkeleton::ItemString](kcoreconfigskeleton-itemstring.md)

## Public Functions

- [ItemPassword(const QString &\_group, const QString &\_key, QString &reference, const QString &defaultValue = QLatin1String(""))](#ItemPassword)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemPassword::ItemPassword(const QString &*\_group*, const QString &*\_key*, QString &*reference*, const QString &*defaultValue* = QLatin1String("")) {#ItemPassword}

Constructs a password item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.
