---
title: "KCoreConfigSkeleton::ItemUrlList Class"
description: "Class for handling a url list preferences item."
---

# KCoreConfigSkeleton::ItemUrlList Class

Class for handling a url list preferences item.

- **Header:** `#include <ItemUrlList>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md)

## Public Functions

- [ItemUrlList(const QString &\_group, const QString &\_key, QList\<QUrl\> &reference, const QList\<QUrl\> &defaultValue = QList\<QUrl\>())](#ItemUrlList)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### ItemUrlList::ItemUrlList(const QString &*\_group*, const QString &*\_key*, QList\<QUrl\> &*reference*, const QList\<QUrl\> &*defaultValue* = QList\<QUrl\>()) {#ItemUrlList}

Constructs a url list item with the given `_group`, `_key`, the initial value `reference` to hold in the item, and the `defaultValue` for the item.
