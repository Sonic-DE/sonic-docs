---
title: "KCoreConfigSkeleton::ItemDouble Class"
description: "Class for handling a floating point preference item."
---

# KCoreConfigSkeleton::ItemDouble Class

Class for handling a floating point preference item.

- **Header:** `#include <ItemDouble>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md)

## Public Functions

- [ItemDouble(const QString &\_group, const QString &\_key, double &reference, double defaultValue = 0)](#ItemDouble)
- [void setMaxValue(double)](#setMaxValue)
- [void setMinValue(double)](#setMinValue)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemDouble::ItemDouble(const QString &*\_group*, const QString &*\_key*, double &*reference*, double *defaultValue* = 0) {#ItemDouble}

Constructs a double item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.

### void ItemDouble::setMaxValue(*double*) {#setMaxValue}

Sets the maximum value for the item.

*See also* [maxValue](kconfigskeletonitem.md#maxValue)()

### void ItemDouble::setMinValue(*double*) {#setMinValue}

Sets the minimum value for the item.

*See also* [minValue](kconfigskeletonitem.md#minValue)()
