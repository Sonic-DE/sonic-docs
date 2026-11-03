---
title: "KCoreConfigSkeleton::ItemRectF Class"
description: "Class for handling a QRectF preferences item."
---

# KCoreConfigSkeleton::ItemRectF Class

Class for handling a [QRectF](https://doc.qt.io/qt-6/qrectf.html) preferences item.

- **Header:** `#include <ItemRectF>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md)

## Public Functions

- [ItemRectF(const QString &\_group, const QString &\_key, QRectF &reference, const QRectF &defaultValue = QRectF())](#ItemRectF)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemRectF::ItemRectF(const QString &*\_group*, const QString &*\_key*, QRectF &*reference*, const QRectF &*defaultValue* = QRectF()) {#ItemRectF}

Constructs a [QRectF](https://doc.qt.io/qt-6/qrectf.html) item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.
