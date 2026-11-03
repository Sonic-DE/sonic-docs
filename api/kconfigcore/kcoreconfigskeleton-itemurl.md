---
title: "KCoreConfigSkeleton::ItemUrl Class"
description: "Class for handling a url preferences item."
---

# KCoreConfigSkeleton::ItemUrl Class

Class for handling a url preferences item.

- **Header:** `#include <ItemUrl>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md)

## Public Functions

- [ItemUrl(const QString &\_group, const QString &\_key, QUrl &reference, const QUrl &defaultValue = QUrl())](#ItemUrl)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemUrl::ItemUrl(const QString &*\_group*, const QString &*\_key*, QUrl &*reference*, const QUrl &*defaultValue* = QUrl()) {#ItemUrl}

Constructs an url item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.
