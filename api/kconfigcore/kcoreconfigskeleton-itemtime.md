---
title: "KCoreConfigSkeleton::ItemTime Class"
description: "Class for handling a QTime preferences item. This class was introduced in Qt 6.16."
---

# KCoreConfigSkeleton::ItemTime Class

Class for handling a [QTime](https://doc.qt.io/qt-6/qtime.html) preferences item. This class was introduced in Qt 6.16. [More...](#details)

- **Header:** `#include <ItemTime>`
- **Since:** Qt 6.16
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md)

[List of all members, including inherited members](kcoreconfigskeleton-itemtime-members.md)

## Public Functions

- [ItemTime(const QString &\_group, const QString &\_key, QTime &reference, QTime defaultValue = QTime())](#ItemTime)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemTime::ItemTime(const QString &*\_group*, const QString &*\_key*, QTime &*reference*, QTime *defaultValue* = QTime()) {#ItemTime}

Constructs a [QTime](https://doc.qt.io/qt-6/qtime.html) item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.
