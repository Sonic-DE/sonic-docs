---
title: "KCoreConfigSkeleton::ItemRect Class"
description: "Class for handling a QRect preferences item."
---

# KCoreConfigSkeleton::ItemRect Class

Class for handling a [QRect](https://doc.qt.io/qt-6/qrect.html) preferences item. [More...](#details)

- **Header:** `#include <ItemRect>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md)

[List of all members, including inherited members](kcoreconfigskeleton-itemrect-members.md)

## Public Functions

- [ItemRect(const QString &\_group, const QString &\_key, QRect &reference, const QRect &defaultValue = QRect())](#ItemRect)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemRect::ItemRect(const QString &*\_group*, const QString &*\_key*, QRect &*reference*, const QRect &*defaultValue* = QRect()) {#ItemRect}

Constructs a [QRect](https://doc.qt.io/qt-6/qrect.html) item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.
