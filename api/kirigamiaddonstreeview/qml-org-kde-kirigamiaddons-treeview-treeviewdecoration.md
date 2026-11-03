---
title: "TreeViewDecoration QML Type"
description: "The tree expander decorator for item views."
---

# TreeViewDecoration QML Type

The tree expander decorator for item views. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.treeview
- Inherits: [RowLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-rowlayout.html)

## Detailed Description {#details}

It will have a `> v` expander button graphics, and will have indentation on the left depending on the level of the tree the item is in.

It is recommended to use RoundedTreeDelegate directly instead of this component.

## Property Documentation {#property-documentation}

### decorationHighlightColor : color {#decorationHighlightColor-prop}

This property holds the color of the decoration highlight.

### \[required\] index : int {#index-prop}

This property holds the index of the item.

Provided by the model/[ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html).

### \[required\] kDescendantExpandable : bool {#kDescendantExpandable-prop}

This property holds whether the item is expandable.

Provided by the model/[ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html).

### \[required\] kDescendantExpanded : bool {#kDescendantExpanded-prop}

This property holds whether the item is expanded.

Provided by the model/[ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html).

### \[required\] kDescendantHasSiblings : var {#kDescendantHasSiblings-prop}

This property holds whether this item has siblings.

Provided by the model/[ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html).

### \[required\] kDescendantLevel : int {#kDescendantLevel-prop}

This property holds the descendant level of the item.

Provided by the model/[ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html).

### \[required\] model : KDescendantsProxyModel {#model-prop}

This property holds the [KDescendantsProxyModel](../kitemmodels/kdescendantsproxymodel.md) the view is showing.

It needs to be assigned explicitly by the developer.

### \[required\] parentDelegate : ItemDelegate {#parentDelegate-prop}

This property holds the delegate there this decoration will live in.

It needs to be assigned explicitly by the developer.
