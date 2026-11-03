---
title: "KCoreConfigSkeleton::ItemSize Class"
description: "Class for handling a QSize preferences item."
---

# KCoreConfigSkeleton::ItemSize Class

Class for handling a [QSize](https://doc.qt.io/qt-6/qsize.html) preferences item. [More...](#details)

- **Header:** `#include <ItemSize>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md)

[List of all members, including inherited members](kcoreconfigskeleton-itemsize-members.md)

## Public Functions

- [ItemSize(const QString &\_group, const QString &\_key, QSize &reference, const QSize &defaultValue = QSize())](#ItemSize)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemSize::ItemSize(const QString &*\_group*, const QString &*\_key*, QSize &*reference*, const QSize &*defaultValue* = QSize()) {#ItemSize}

Constructs a [QSize](https://doc.qt.io/qt-6/qsize.html) item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.
