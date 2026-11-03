---
title: "KCoreConfigSkeleton::ItemULongLong Class"
description: "Class for handling unsigned 64-bit integer preferences item."
---

# KCoreConfigSkeleton::ItemULongLong Class

Class for handling unsigned 64-bit integer preferences item.

- **Header:** `#include <ItemULongLong>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md)

## Public Functions

- [ItemULongLong(const QString &\_group, const QString &\_key, quint64 &reference, quint64 defaultValue = 0)](#ItemULongLong)
- [void setMaxValue(quint64)](#setMaxValue)
- [void setMinValue(quint64)](#setMinValue)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemULongLong::ItemULongLong(const QString &*\_group*, const QString &*\_key*, quint64 &*reference*, quint64 *defaultValue* = 0) {#ItemULongLong}

Constructs an unsigned long long item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.

### void ItemULongLong::setMaxValue(*quint64*) {#setMaxValue}

Sets the maximum value for the item.

*See also* [maxValue](kconfigskeletonitem.md#maxValue)()

### void ItemULongLong::setMinValue(*quint64*) {#setMinValue}

Sets the minimum value for the item.

*See also* [minValue](kconfigskeletonitem.md#minValue)()
