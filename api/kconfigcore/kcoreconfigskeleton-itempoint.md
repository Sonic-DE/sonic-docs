---
title: "KCoreConfigSkeleton::ItemPoint Class"
description: "Class for handling a QPoint preferences item."
---

# KCoreConfigSkeleton::ItemPoint Class

Class for handling a [QPoint](https://doc.qt.io/qt-6/qpoint.html) preferences item. [More...](#details)

- **Header:** `#include <ItemPoint>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md)

[List of all members, including inherited members](kcoreconfigskeleton-itempoint-members.md)

## Public Functions

- [ItemPoint(const QString &\_group, const QString &\_key, QPoint &reference, const QPoint &defaultValue = QPoint())](#ItemPoint)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemPoint::ItemPoint(const QString &*\_group*, const QString &*\_key*, QPoint &*reference*, const QPoint &*defaultValue* = QPoint()) {#ItemPoint}

Constructs a [QPoint](https://doc.qt.io/qt-6/qpoint.html) item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.
