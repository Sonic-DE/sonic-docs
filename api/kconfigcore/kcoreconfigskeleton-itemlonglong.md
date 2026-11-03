---
title: "KCoreConfigSkeleton::ItemLongLong Class"
description: "Class for handling a 64-bit integer preferences item."
---

# KCoreConfigSkeleton::ItemLongLong Class

Class for handling a 64-bit integer preferences item.

- **Header:** `#include <ItemLongLong>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md)

## Public Functions

- [ItemLongLong(const QString &\_group, const QString &\_key, qint64 &reference, qint64 defaultValue = 0)](#ItemLongLong)
- [void setMaxValue(qint64)](#setMaxValue)
- [void setMinValue(qint64)](#setMinValue)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemLongLong::ItemLongLong(const QString &*\_group*, const QString &*\_key*, qint64 &*reference*, qint64 *defaultValue* = 0) {#ItemLongLong}

Constructs a long long item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.

### void ItemLongLong::setMaxValue(*qint64*) {#setMaxValue}

Sets the maximum value for the item.

*See also* [maxValue](kconfigskeletonitem.md#maxValue)()

### void ItemLongLong::setMinValue(*qint64*) {#setMinValue}

Sets the minimum value for the item.

*See also* [minValue](kconfigskeletonitem.md#minValue)()
