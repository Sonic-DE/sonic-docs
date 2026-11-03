---
title: "AbstractTable QML Type"
description: "Table views with configurable columns, headers, sorting, and selection.."
---

# AbstractTable QML Type

Table views with configurable columns, headers, sorting, and selection.. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.tableview
- Inherits: [Flickable](https://doc.qt.io/qt-6/qml-qtquick-flickable.html)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### actions : alias {#actions-prop}

A link to a list of context menu items.

*See also* [Menu](https://doc.qt.io/qt-6/qml-qtquick-controls-menu.html)

### \[default: true\] alternatingRows : bool {#alternatingRows-prop}

This property controls whether the background color of the rows should alternate.

### \[read-only\] columnCount : int {#columnCount-prop}

This property holds the number of columns in the component include invisibles.

### \[default: true\] compact : bool {#compact-prop}

If this property is enabled, the table will be displayed in a compact form.

### headerComponents : list\<AbstractHeaderComponent\> {#headerComponents-prop}

The default property that stores the components for forming the columns of this table.

*See also* [AbstractHeaderComponent](qml-org-kde-kirigamiaddons-tableview-abstractheadercomponent.md)

### model : var {#model-prop}

This property holds the model that provides data for the table.

The model provides the set of data that is used to create the items in the view.

### \[read-only\] rowCount : int {#rowCount-prop}

This property holds the number of rows in the view.

### \[default: TableView.SelectRows\] selectionBehavior : int {#selectionBehavior-prop}

This property holds whether the user can select cells, rows or columns.

*See also* [TableView.selectionBehavior](https://doc.qt.io/qt-6/qml-qtquick-tableview.html#selectionBehavior-prop)

### \[default: TableView.ExtendedSelection\] selectionMode : int {#selectionMode-prop}

The selection mode.

| Constant | Description |
| --- | --- |
| TableView.SelectCells | Whether the user can select one cell at a time, or multiple cells. |
| TableView.SelectRows | Whether the user can select one row at a time, or multiple rows. |
| TableView.SelectColumns | Whether the user can select one column at a time, or multiple columns. |

*See also* [TableView.selectionMode](https://doc.qt.io/qt-6/qml-qtquick-tableview.html#selectionMode-prop)

### selectionModel : ItemSelectionModel {#selectionModel-prop}

This property can be set to control which delegate items should be shown as selected, and which item should be shown as current.

Using the selectionType and [selectionMode](qml-org-kde-kirigamiaddons-tableview-abstracttable.md#selectionMode-prop) properties you can adjust the selection behavior.

*See also* selectionType, [selectionMode](qml-org-kde-kirigamiaddons-tableview-abstracttable.md#selectionMode-prop)

### sortOrder : Qt.SortOrder {#sortOrder-prop}

The property is responsible for the direction in which sorting will be performed.

> **Note:** You must implement sorting yourself for this property to be valid.

*See also* [sortRole](qml-org-kde-kirigamiaddons-tableview-abstracttable.md#sortRole-prop), [Qt.SortOrder](https://doc.qt.io/qt-6/qt.html#SortOrder-enum)

### sortRole : int {#sortRole-prop}

This property specifies based on which role the table will be sorted.

> **Note:** You must implement sorting yourself for this property to be valid.

*See also* [sortOrder](qml-org-kde-kirigamiaddons-tableview-abstracttable.md#sortOrder-prop)

## Signal Documentation {#signal-documentation}

### columnClicked(int *column*, var *headerComponent*) {#columnClicked-signal}

> **Note:** The corresponding handler is `onColumnClicked`.

### columnDoubleClicked(int *column*, var *headerComponent*) {#columnDoubleClicked-signal}

> **Note:** The corresponding handler is `onColumnDoubleClicked`.

### rowClicked(int *row*) {#rowClicked-signal}

> **Note:** The corresponding handler is `onRowClicked`.

### rowDoubleClicked(int *row*) {#rowDoubleClicked-signal}

> **Note:** The corresponding handler is `onRowDoubleClicked`.
