---
title: "KColumnHeadersModel QML Type"
description: "Exposes a model's horizontal column headers as a list."
---

# KColumnHeadersModel QML Type

Exposes a model's horizontal column headers as a list. [More...](#details)

- Import Statement: import org.kde.kitemmodels
- In C++: [KColumnHeadersModel](../kitemmodels/kcolumnheadersmodel.md)

## Detailed Description {#details}

Each row represents one column of [sourceModel](qml-org-kde-kitemmodels-kcolumnheadersmodel.md#sourceModel-prop). Its roles return the corresponding horizontal header data from the source model. The additional `sort` role reports [sortOrder](qml-org-kde-kitemmodels-kcolumnheadersmodel.md#sortOrder-prop) for the row selected by [sortColumn](qml-org-kde-kitemmodels-kcolumnheadersmodel.md#sortColumn-prop); it is empty for other rows. Setting these properties does not sort the source model.

## Property Documentation {#property-documentation}

### \[default: -1\] sortColumn : int {#sortColumn-prop}

The column whose `sort` role reports [sortOrder](qml-org-kde-kitemmodels-kcolumnheadersmodel.md#sortOrder-prop). A value of -1 leaves the `sort` role empty for every row.

### \[default: Qt.AscendingOrder\] sortOrder : Qt::SortOrder {#sortOrder-prop}

The order reported by the `sort` role for [sortColumn](qml-org-kde-kitemmodels-kcolumnheadersmodel.md#sortColumn-prop).

### sourceModel : var {#sourceModel-prop}

The model whose horizontal column headers are exposed as rows.
