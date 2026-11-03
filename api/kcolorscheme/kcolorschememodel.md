---
title: "KColorSchemeModel Class"
description: "A model listing the KColorSchemes available in the system."
---

# KColorSchemeModel Class

A model listing the KColorSchemes available in the system. [More...](#details)

- **Header:** `#include <KColorSchemeModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ColorScheme)`  
  `target_link_libraries(mytarget PRIVATE KF6::ColorScheme)`
- **Inherits:** [QAbstractListModel](https://doc.qt.io/qt-6/qabstractlistmodel.html)

[List of all members, including inherited members](kcolorschememodel-members.md)

## Public Types

- [enum KColorSchemeModel::Roles](#Roles-enum)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum KColorSchemeModel::Roles {#Roles-enum}

| Constant |   |
| --- | --- |
| `KColorSchemeModel::NameRole` | `Qt::DisplayRole` |
| `KColorSchemeModel::IconRole` | `Qt::DecorationRole` |
| `KColorSchemeModel::PathRole` | `Qt::UserRole` |
| `KColorSchemeModel::IdRole` | `257` |
