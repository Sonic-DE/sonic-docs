---
title: "KCoreConfigSkeleton::ItemUInt Class"
description: "Class for handling an unsigned 32-bit integer preferences item."
---

# KCoreConfigSkeleton::ItemUInt Class

Class for handling an unsigned 32-bit integer preferences item.

- **Header:** `#include <ItemUInt>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md)

## Public Functions

- [ItemUInt(const QString &\_group, const QString &\_key, quint32 &reference, quint32 defaultValue = 0)](#ItemUInt)
- [void setMaxValue(quint32)](#setMaxValue)
- [void setMinValue(quint32)](#setMinValue)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemUInt::ItemUInt(const QString &*\_group*, const QString &*\_key*, quint32 &*reference*, quint32 *defaultValue* = 0) {#ItemUInt}

Constructs an uint item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.

### void ItemUInt::setMaxValue(*quint32*) {#setMaxValue}

Sets the maximum value for the item.

*See also* [maxValue](kconfigskeletonitem.md#maxValue)()

### void ItemUInt::setMinValue(*quint32*) {#setMinValue}

Sets the minimum value for the item.

*See also* [minValue](kconfigskeletonitem.md#minValue)()
