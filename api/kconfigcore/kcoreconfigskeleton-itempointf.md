---
title: "KCoreConfigSkeleton::ItemPointF Class"
description: "Class for handling a QPointF preferences item."
---

# KCoreConfigSkeleton::ItemPointF Class

Class for handling a [QPointF](https://doc.qt.io/qt-6/qpointf.html) preferences item. [More...](#details)

- **Header:** `#include <ItemPointF>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md)

[List of all members, including inherited members](kcoreconfigskeleton-itempointf-members.md)

## Public Functions

- [ItemPointF(const QString &\_group, const QString &\_key, QPointF &reference, const QPointF &defaultValue = QPointF())](#ItemPointF)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemPointF::ItemPointF(const QString &*\_group*, const QString &*\_key*, QPointF &*reference*, const QPointF &*defaultValue* = QPointF()) {#ItemPointF}

Constructs a [QPointF](https://doc.qt.io/qt-6/qpointf.html) item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.
