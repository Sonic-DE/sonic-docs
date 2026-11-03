---
title: "ColumnView QML Type"
description: "A container that lays out items horizontally in a row."
---

# ColumnView QML Type

A container that lays out items horizontally in a row. [More...](#details)

- Import Statement: import org.kde.kirigami.layouts
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

When not all items fit in the [ColumnView](qml-org-kde-kirigami-layouts-columnview.md), it will behave like a Flickable and will be a scrollable view which shows only a determined number of columns.

The columns can either all have the same fixed size (recommended), size themselves with implicitWidth, or automatically expand to take all the available width: by default the last column will always be the expanding one.

Items inside the [ColumnView](qml-org-kde-kirigami-layouts-columnview.md) can access info of the view and set layouting hints via the [ColumnView](qml-org-kde-kirigami-layouts-columnview.md) attached property.

This is the base for the implementation of [PageRow](qml-org-kde-kirigami-pagerow.md).

## Property Documentation {#property-documentation}

### bottomPadding : real {#bottomPadding-prop}

The padding this will have at the bottom

### columnResizeMode : enumeration {#columnResizeMode-prop}

The strategy to follow while automatically resizing the columns

The default is FixedColumns.

| Constant | Description |
| --- | --- |
| ColumnView.FixedColumns | Every column is fixed at the same width of the [columnWidth](qml-org-kde-kirigami-layouts-columnview.md#columnWidth-prop) property |
| ColumnView.DynamicColumns | Columns take their width from their implicitWidth |
| ColumnView.SingleColumn | Only one column at a time is shown, as wide as the viewport, eventual [reservedSpace](qml-org-kde-kirigami-layouts-columnview.md#reservedSpace-attached-prop) on the column's attached property is ignored |

### columnWidth : real {#columnWidth-prop}

The width of all columns when [columnResizeMode](qml-org-kde-kirigami-layouts-columnview.md#columnResizeMode-prop) is FixedColumns

### contentChildren : list\<Item\> {#contentChildren-prop}

Every column item the view contains

### \[default\] contentData : list\<QtObject\> {#contentData-prop}

every item declared inside the view, both visual and non-visual items

### \[read-only\] contentItem : Item {#contentItem-prop}

The main content item of this view: it's the parent of the column items

### \[read-only\] contentWidth : real {#contentWidth-prop}

The compound width of all columns in the view

### contentX : real {#contentX-prop}

The value of the horizontal scroll of the view, in pixels

### \[read-only\] count : int {#count-prop}

How many columns this view contains

### currentIndex : int {#currentIndex-prop}

The position of the currently active column. The current column will also have keyboard focus

### \[read-only\] currentItem : Item {#currentItem-prop}

The currently active column. The current column will also have keyboard focus

### \[read-only\] dragging : bool {#dragging-prop}

True when the user is dragging around with touch gestures the view contents

### interactive : bool {#interactive-prop}

True if it supports moving the contents by dragging

### \[read-only\] leadingVisibleItem : Item {#leadingVisibleItem-prop}

The first of [visibleItems](qml-org-kde-kirigami-layouts-columnview.md#visibleItems-prop) provided from convenience

### \[read-only\] moving : bool {#moving-prop}

True both when the user is dragging around with touch gestures the view contents or the view is animating

### savedState : string {#savedState-prop}

A JSon serialization of the columns widths. When [columnResizeMode](qml-org-kde-kirigami-layouts-columnview.md#columnResizeMode-prop) is DynamicColumns, columns can be resized via mouse. When this is the case, the sizes should be saved and restored on application startup.

Example code for saving and restore, assuming that the application exposes a singleton called App that has a "columnViewState" property that reads and writes to the config file:

```qml
Component.onCompleted: pageStack.columnView.savedState = App.columnViewState;
columnView.onSavedStateChanged: {
    App.columnViewState = pageStack.columnView.savedState;
}
```

### scrollDuration : int {#scrollDuration-prop}

The duration for scrolling animations

### separatorVisible : bool {#separatorVisible-prop}

True if columns should be visually separated by a separator line

### topPadding : real {#topPadding-prop}

The padding this will have at the top

### \[read-only\] trailingVisibleItem : Item {#trailingVisibleItem-prop}

The last of [visibleItems](qml-org-kde-kirigami-layouts-columnview.md#visibleItems-prop) provided from convenience

### \[read-only\] visibleItems : list\<QtObject\> {#visibleItems-prop}

The list of all visible column items that are at least partially in the viewport at any given moment

## Attached Property Documentation {#attached-property-documentation}

### ColumnView.fillWidth : bool {#fillWidth-attached-prop}

If true, the column will expand to take the whole viewport space minus [reservedSpace](qml-org-kde-kirigami-layouts-columnview.md#reservedSpace-attached-prop)

### ColumnView.globalFooter : Item {#globalFooter-attached-prop}

### ColumnView.globalHeader : Item {#globalHeader-attached-prop}

### \[read-only\] ColumnView.inViewport : bool {#inViewport-attached-prop}

True if this column is at least partly visible in the [ColumnView](qml-org-kde-kirigami-layouts-columnview.md)'s viewport.

### ColumnView.index : int {#index-attached-prop}

The index position of the column in the view, starting from 0

### \[since 6.16\] ColumnView.interactiveResizeEnabled : bool {#interactiveResizeEnabled-attached-prop}

True if this column supports interactive resize with mouse.

If the sizes should be saved and restored on application startup, it is the application responsibility to implement this, for instance exposing and object with properties for the desired column widths which reads and writes to the config. at the main Component.onCompleted of the [ApplicationWindow](qml-org-kde-kirigami-applicationwindow.md) root Item it will apply the preferred sizes of the desired pages.

The property will be written at interactiveResizingChanged signal handler.

This property was introduced in Qt 6.16.

### \[since 6.16\] ColumnView.interactiveResizing : bool {#interactiveResizing-attached-prop}

True when the user is actively resizing a column with the mouse. If the application wants to write the column sizes to config, it can sync to some global object property at interactiveResizingChanged:

```qml
Kirigami.ColumnView.onInteractiveResizingChanged: {
    if (!Kirigami.ColumnView.interactiveResizing) {
        myAppObject.leftColumnWidth = page.implicitWidth;
    }
}
```

This property was introduced in Qt 6.16.

### \[since 6.16\] ColumnView.maximumWidth : real {#maximumWidth-attached-prop}

When a column is [interactiveResizeEnabled](qml-org-kde-kirigami-layouts-columnview.md#interactiveResizeEnabled-attached-prop), when resizing manually it will bound the column size between [minimumWidth](qml-org-kde-kirigami-layouts-columnview.md#minimumWidth-attached-prop) and maximumWidth

This property was introduced in Qt 6.16.

### \[since 6.16\] ColumnView.minimumWidth : real {#minimumWidth-attached-prop}

When a column is [interactiveResizeEnabled](qml-org-kde-kirigami-layouts-columnview.md#interactiveResizeEnabled-attached-prop), when resizing manually it will bound the column size between minimumWidth and [maximumWidth](qml-org-kde-kirigami-layouts-columnview.md#maximumWidth-attached-prop)

This property was introduced in Qt 6.16.

### ColumnView.pinned : bool {#pinned-attached-prop}

If true the page will never go out of view, but will stay either at the right or left side of the [ColumnView](qml-org-kde-kirigami-layouts-columnview.md)

### \[since 6.16\] ColumnView.preferredWidth : real {#preferredWidth-attached-prop}

When we are in DynamicColumns mode, the columns will be resized to preferredWidth. When the column is resized with the mouse, this property will be updated by the drag And will always be between [minimumWidth](qml-org-kde-kirigami-layouts-columnview.md#minimumWidth-attached-prop) and [maximumWidth](qml-org-kde-kirigami-layouts-columnview.md#maximumWidth-attached-prop)

This property was introduced in Qt 6.16.

### ColumnView.preventStealing : bool {#preventStealing-attached-prop}

Like the same property of [MouseArea](https://doc.qt.io/qt-6/qml-qtquick-mousearea.html), when this is true, the column view won't try to manage events by itself when filtering from a child, not disturbing user interaction

### ColumnView.reservedSpace : real {#reservedSpace-attached-prop}

When a column is [fillWidth](qml-org-kde-kirigami-layouts-columnview.md#fillWidth-attached-prop), it will keep reservedSpace amount of pixels from going to fill the full viewport width

### \[read-only\] ColumnView.view : ColumnView {#view-attached-prop}

The view this column belongs to

## Signal Documentation {#signal-documentation}

### itemInserted(int *position*, Item *item*) {#itemInserted-signal}

A new item has been inserted

`position` where the page has been inserted

`item` a pointer to the new item

> **Note:** The corresponding handler is `onItemInserted`.

### itemRemoved(Item *item*) {#itemRemoved-signal}

An item has just been removed from the view

`item` a pointer to the item that has just been removed

> **Note:** The corresponding handler is `onItemRemoved`.

## Method Documentation {#method-documentation}

### \[since 6.16\] Item get(int *index*) {#get-method}

This method gets the item at index, if available

Note that if an invalid index is passed (either negative or greater then depth - 1) nullptr will be returned

`index` The index of the item to get.

This method was introduced in Qt 6.16.

### Item pop() {#pop-method}

This method removes the last item from the view and returns it.

This method calls [removeItem](qml-org-kde-kirigami-layouts-columnview.md#removeItem-method)() on the last item.

Returns the removed item

*See also* [removeItem](qml-org-kde-kirigami-layouts-columnview.md#removeItem-method)()

### Item pop(var *item*) {#pop-method-1}

This method removes all the items after the specified item or index from the view and returns the last item that was removed.

Note that if the passed value is neither of the values said below, it will return a nullptr.

`item` the item to remove. It can be an item, index or not defined in which case it will pop the last item.

### Item removeItem(var *item*) {#removeItem-method}

This method removes an item from the view.

If the argument is a number, this method dispatches to removeItem(int index) to remove an item by its index. Otherwise the argument should be the item itself to be removed itself, and this method will dispatch to removeItem([QQuickItem](https://doc.qt.io/qt-6/qquickitem.html) \*item).

`item` the item which should be removed

Returns the removed item
