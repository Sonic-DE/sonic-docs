---
title: "KCoreConfigSkeleton::ItemProperty Class"
description: "Class for handling a QVariant preferences item."
---

# KCoreConfigSkeleton::ItemProperty Class

Class for handling a [QVariant](https://doc.qt.io/qt-6/qvariant.html) preferences item. [More...](#details)

- **Header:** `#include <ItemProperty>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md)

[List of all members, including inherited members](kcoreconfigskeleton-itemproperty-members.md)

## Public Functions

- [ItemProperty(const QString &\_group, const QString &\_key, QVariant &reference, const QVariant &defaultValue = QVariant())](#ItemProperty)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemProperty::ItemProperty(const QString &*\_group*, const QString &*\_key*, QVariant &*reference*, const QVariant &*defaultValue* = QVariant()) {#ItemProperty}

Constructs a property item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.
