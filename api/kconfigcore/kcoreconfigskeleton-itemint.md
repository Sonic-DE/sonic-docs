---
title: "KCoreConfigSkeleton::ItemInt Class"
description: "Class for handling a 32-bit integer preferences item."
---

# KCoreConfigSkeleton::ItemInt Class

Class for handling a 32-bit integer preferences item. [More...](#details)

- **Header:** `#include <ItemInt>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md)
- **Inherited By:** [KCoreConfigSkeleton::ItemEnum](kcoreconfigskeleton-itemenum.md)

[List of all members, including inherited members](kcoreconfigskeleton-itemint-members.md)

## Public Functions

- [ItemInt(const QString &\_group, const QString &\_key, qint32 &reference, qint32 defaultValue = 0)](#ItemInt)
- [void setMaxValue(qint32)](#setMaxValue)
- [void setMinValue(qint32)](#setMinValue)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemInt::ItemInt(const QString &*\_group*, const QString &*\_key*, qint32 &*reference*, qint32 *defaultValue* = 0) {#ItemInt}

Constructs an int item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.

### void ItemInt::setMaxValue(*qint32*) {#setMaxValue}

Sets the maximum value for the item.

*See also* [maxValue](kconfigskeletonitem.md#maxValue)

### void ItemInt::setMinValue(*qint32*) {#setMinValue}

Sets the minimum value for the item.

*See also* [minValue](kconfigskeletonitem.md#minValue)()
