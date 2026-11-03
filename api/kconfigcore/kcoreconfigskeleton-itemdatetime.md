---
title: "KCoreConfigSkeleton::ItemDateTime Class"
description: "Class for handling a QDateTime preferences item."
---

# KCoreConfigSkeleton::ItemDateTime Class

Class for handling a [QDateTime](https://doc.qt.io/qt-6/qdatetime.html) preferences item.

- **Header:** `#include <ItemDateTime>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md)

## Public Functions

- [ItemDateTime(const QString &\_group, const QString &\_key, QDateTime &reference, const QDateTime &defaultValue = QDateTime())](#ItemDateTime)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemDateTime::ItemDateTime(const QString &*\_group*, const QString &*\_key*, QDateTime &*reference*, const QDateTime &*defaultValue* = QDateTime()) {#ItemDateTime}

Constructs a [QDateTime](https://doc.qt.io/qt-6/qdatetime.html) item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.
