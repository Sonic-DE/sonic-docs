---
title: "CardsLayout QML Type"
description: "A GridLayout optimized for showing one or two columns of cards, depending on the available space."
---

# CardsLayout QML Type

A [GridLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-gridlayout.html) optimized for showing one or two columns of cards, depending on the available space. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [GridLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-gridlayout.html)

## Detailed Description {#details}

It Should be used when the cards are not instantiated by a model or by a model which has always very few items.

They are presented as a grid of two columns which will remain centered if the application is really wide, or become a single column if there is not enough space for two columns, such as a mobile phone screen.

A [CardsLayout](qml-org-kde-kirigami-cardslayout.md) should always be contained within a [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html).

## Property Documentation {#property-documentation}

### maximumColumnWidth : int {#maximumColumnWidth-prop}

This property holds the maximum width the columns may have.

The cards will never become wider than this size; when the [GridLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-gridlayout.html) is wider than maximumColumnWidth, it will switch from one to two columns.

If the default needs to be overridden for some reason, it is advised to express this unit as a multiple of Kirigami.Units.gridUnit.

default: 20 \* Kirigami.Units.gridUnit

### maximumColumns : int {#maximumColumns-prop}

This property holds the maximum number of columns.

This layout will never lay out the items in more columns than maximumColumns

default: 2

### minimumColumnWidth : int {#minimumColumnWidth-prop}

This property holds the minimum width the columns may have.

The layout will try to dispose of items in a number of columns that will respect this size constraint.

default: 12 \* Kirigami.Units.gridUnit
