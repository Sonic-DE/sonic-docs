---
title: "KColumnHeadersModel Class"
description: "A model that converts a model's headers into a list model."
---

# KColumnHeadersModel Class

A model that converts a model's headers into a list model. [More...](#details)

- **Header:** `#include <KColumnHeadersModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ItemModels)`  
  `target_link_libraries(mytarget PRIVATE KF6::ItemModels)`
- **Inherits:** [QAbstractListModel](https://doc.qt.io/qt-6/qabstractlistmodel.html)

[List of all members, including inherited members](kcolumnheadersmodel-members.md)

## Public Types

- [enum KColumnHeadersModel::ExtraRoles](#ExtraRoles-enum)

## Properties

- [sortColumn : int](#sortColumn-prop)
- [sortOrder : Qt::SortOrder](#sortOrder-prop)
- [sourceModel : QAbstractItemModel\*](#sourceModel-prop)

## Public Functions

- [KColumnHeadersModel(QObject \*parent = nullptr)](#KColumnHeadersModel)

## Detailed Description {#details}

This model will expose the source model's headers as a simple list. This is mostly useful as a helper for QML applications that want to display a model's headers.

Each columns's header will be presented as a row in this model. Roles are forwarded directly to the source model's [headerData](https://doc.qt.io/qt-6/qabstractitemmodel.html#headerData)() method.

## Member Type Documentation {#member-type-documentation}

### enum KColumnHeadersModel::ExtraRoles {#ExtraRoles-enum}

| Constant |   |
| --- | --- |
| `KColumnHeadersModel::SortRole` | `0x011D910E` |

## Property Documentation {#property-documentation}

### sortColumn : int {#sortColumn-prop}

**Access functions:**

- `int` **sortColumn**() const
- `void` **setSortColumn**(`int` *newSortColumn*)

**Notifier signal:**

- `void` **sortColumnChanged**()

### sortOrder : Qt::SortOrder {#sortOrder-prop}

**Access functions:**

- `Qt::SortOrder` **sortOrder**() const
- `void` **setSortOrder**(`Qt::SortOrder` *newSortOrder*)

**Notifier signal:**

- `void` **sortOrderChanged**()

### sourceModel : QAbstractItemModel\* {#sourceModel-prop}

**Access functions:**

- `QAbstractItemModel` \***sourceModel**() const
- `void` **setSourceModel**(`QAbstractItemModel` \**newSourceModel*)

**Notifier signal:**

- `void` **sourceModelChanged**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KColumnHeadersModel::KColumnHeadersModel(QObject \**parent* = nullptr) {#KColumnHeadersModel}
