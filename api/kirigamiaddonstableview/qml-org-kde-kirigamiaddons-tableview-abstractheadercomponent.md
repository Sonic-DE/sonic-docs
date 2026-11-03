---
title: "AbstractHeaderComponent QML Type"
description: "Abstract header component."
---

# AbstractHeaderComponent QML Type

Abstract header component. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.tableview

## Detailed Description {#details}

Designed to form a set of properties that will be used in the implementation.

## Property Documentation {#property-documentation}

### draggable : bool {#draggable-prop}

The flag reflects the ability to move the current column to another place in the table.

### headerDelegate : Component {#headerDelegate-prop}

This property holds an item that will be displayed as the main component of the column.

It can be customized to put any kind of [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html) in there.

### itemDelegate : Component {#itemDelegate-prop}

The element that will be used as the base element to display in all delegates of this column.

It can be customized to put any kind of [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html) in there.

### leading : Component {#leading-prop}

This property holds an item that will be displayed to the left of the [headerDelegate](qml-org-kde-kirigamiaddons-tableview-abstractheadercomponent.md#headerDelegate-prop) contents.

It can be customized to put any kind of [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html) in there.

*See also* [headerDelegate](qml-org-kde-kirigamiaddons-tableview-abstractheadercomponent.md#headerDelegate-prop)

### minimumWidth : real {#minimumWidth-prop}

Stores the minimum allowed width of the entire column

### \[default: true\] resizable : bool {#resizable-prop}

This flag reflects the ability to change the original column size.

### role : int {#role-prop}

The role value from the model for the current column.

By default, used to indicate the column by which the table is sorted.

### textRole : string {#textRole-prop}

The name of the role from the model for the current column.

Used to access the value that is stored in the model for that role.

### title : string {#title-prop}

Column title.

Used in the default [headerDelegate](qml-org-kde-kirigamiaddons-tableview-abstractheadercomponent.md#headerDelegate-prop).

*See also* [headerDelegate](qml-org-kde-kirigamiaddons-tableview-abstractheadercomponent.md#headerDelegate-prop)

### \[default: true\] visible : bool {#visible-prop}

The property is responsible for displaying the entire column in the table.

### width : real {#width-prop}

Stores the current width of an entire table column.
