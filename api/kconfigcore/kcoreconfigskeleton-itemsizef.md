---
title: "KCoreConfigSkeleton::ItemSizeF Class"
description: "Class for handling a QSizeF preferences item."
---

# KCoreConfigSkeleton::ItemSizeF Class

Class for handling a [QSizeF](https://doc.qt.io/qt-6/qsizef.html) preferences item.

- **Header:** `#include <ItemSizeF>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md)

## Public Functions

- [ItemSizeF(const QString &\_group, const QString &\_key, QSizeF &reference, const QSizeF &defaultValue = QSizeF())](#ItemSizeF)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemSizeF::ItemSizeF(const QString &*\_group*, const QString &*\_key*, QSizeF &*reference*, const QSizeF &*defaultValue* = QSizeF()) {#ItemSizeF}

Constructs a [QSizeF](https://doc.qt.io/qt-6/qsizef.html) item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.
