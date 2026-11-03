---
title: "KNSCore::ProvidersModel Class"
description: "A model which holds information on all known Providers for a specific Engine."
---

# KNSCore::ProvidersModel Class

A model which holds information on all known Providers for a specific Engine. [More...](#details)

- **Header:** `#include <ProvidersModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NewStuff)`  
  `target_link_libraries(mytarget PRIVATE KF6::NewStuff)`
- **Inherits:** [QAbstractListModel](https://doc.qt.io/qt-6/qabstractlistmodel.html)

[List of all members, including inherited members](knscore-providersmodel-members.md)

## Public Types

- [enum ProvidersModel::Roles](#Roles-enum)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum ProvidersModel::Roles {#Roles-enum}

| Constant | Value |   |
| --- | --- | --- |
| `KNSCore::ProvidersModel::IdRole` | `Qt::UserRole + 1` |   |
| `KNSCore::ProvidersModel::NameRole` | `258` | , |
| `KNSCore::ProvidersModel::VersionRole` | `259` | , |
| `KNSCore::ProvidersModel::WebsiteRole` | `260` | , |
| `KNSCore::ProvidersModel::HostRole` | `261` | , |
| `KNSCore::ProvidersModel::ContactEmailRole` | `262` | , |
| `KNSCore::ProvidersModel::SupportsSslRole` | `263` | , |
| `KNSCore::ProvidersModel::IconRole` | `264` | , |
| `KNSCore::ProvidersModel::ObjectRole` | `265` | The actual Provider object. Do not hold this locally and expect it to disappear at a moment's notice. |
