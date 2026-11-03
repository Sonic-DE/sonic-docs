---
title: "AbstractApplicationHeader QML Type"
description: "An item that can be used as a title for the application."
---

# AbstractApplicationHeader QML Type

An item that can be used as a title for the application. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

Scrolling the main page will make it taller or shorter (through the point of going away) It's a behavior similar to the typical mobile web browser addressbar the minimum, preferred and maximum heights of the item can be controlled with:

- [minimumHeight](qml-org-kde-kirigami-abstractapplicationheader.md#minimumHeight-prop): default is 0, i.e. hidden
- [preferredHeight](qml-org-kde-kirigami-abstractapplicationheader.md#preferredHeight-prop): default is Units.gridUnit \* 1.6
- [maximumHeight](qml-org-kde-kirigami-abstractapplicationheader.md#maximumHeight-prop): default is Units.gridUnit \* 3

To achieve a titlebar that stays completely fixed just set the 3 sizes as the same.

## Property Documentation {#property-documentation}

### background : Item {#background-prop}

This property holds the background item.

> **Note:** The background will be automatically sized to fill the whole control.

### bottomPadding : int {#bottomPadding-prop}

### \[default\] contentItem : alias {#contentItem-prop}

### hideWhenTouchScrolling : bool {#hideWhenTouchScrolling-prop}

This property specifies whether the header should be pushed back when scrolling using the touch screen.

### leftPadding : int {#leftPadding-prop}

### maximumHeight : real {#maximumHeight-prop}

### minimumHeight : real {#minimumHeight-prop}

### page : KirigamiControls.Page {#page-prop}

### pageRow : KirigamiControls.PageRow {#pageRow-prop}

### \[read-only\] paintedHeight : int {#paintedHeight-prop}

### position : int {#position-prop}

### preferredHeight : real {#preferredHeight-prop}

### rightPadding : int {#rightPadding-prop}

### separatorVisible : bool {#separatorVisible-prop}

### topPadding : int {#topPadding-prop}
