---
title: "KCoreConfigSkeleton::ItemString Class"
description: "Class for handling a string preferences item."
---

# KCoreConfigSkeleton::ItemString Class

Class for handling a string preferences item. [More...](#details)

- **Header:** `#include <ItemString>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfigSkeletonGenericItem](kconfigskeletongenericitem.md)
- **Inherited By:** [KCoreConfigSkeleton::ItemPassword](kcoreconfigskeleton-itempassword.md) and [KCoreConfigSkeleton::ItemPath](kcoreconfigskeleton-itempath.md)

[List of all members, including inherited members](kcoreconfigskeleton-itemstring-members.md)

## Public Types

- [enum ItemString::Type](#Type-enum)

## Public Functions

- [ItemString(const QString &\_group, const QString &\_key, QString &reference, const QString &defaultValue = QLatin1String(""), KCoreConfigSkeleton::ItemString::Type type = Normal)](#ItemString)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum ItemString::Type {#Type-enum}

The type of string that is held in this item.

| Constant | Value | Description |
| --- | --- | --- |
| `KCoreConfigSkeleton::ItemString::Normal` | `0` | A normal string |
| `KCoreConfigSkeleton::ItemString::Password` | `1` | A password string |
| `KCoreConfigSkeleton::ItemString::Path` | `2` | A path to a file or directory |

## Member Function Documentation {#member-function-documentation}

### ItemString::ItemString(const QString &*\_group*, const QString &*\_key*, QString &*reference*, const QString &*defaultValue* = QLatin1String(""), KCoreConfigSkeleton::ItemString::Type *type* = Normal) {#ItemString}

Constructs a string item with the given `_group`, `_key`, the initial value `reference` to hold in the item, the `defaultValue` for the item, and the `type` of string held by the item.
