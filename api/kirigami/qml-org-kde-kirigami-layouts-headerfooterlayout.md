---
title: "HeaderFooterLayout QML Type"
description: "Replicates a little part of what Page does."
---

# HeaderFooterLayout QML Type

Replicates a little part of what Page does. [More...](#details)

- Import Statement: import org.kde.kirigami.layouts
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

It's a container with 3 properties, header, [contentItem](qml-org-kde-kirigami-layouts-headerfooterlayout.md#contentItem-prop) and footer which will be laid out oone on top of each other.

It works better than a [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html) when the elements are to be defined by properties by the user, which would require ugly reparenting dances and container items to maintain the layout well behaving.

## Property Documentation {#property-documentation}

### contentItem : Item {#contentItem-prop}

This property holds the visual content Item.

It will be resized both in width and height with the layout resizing. Its height will be resized to still have room for the header and footer

### footer : Item {#footer-prop}

This property holds the page footer item.

The footer item is positioned to the bottom, and resized to the width of the page. The default value is null.

### header : Item {#header-prop}

This property holds the page header item.

The header item is positioned to the top, and resized to the width of the page. The default value is null.

### \[since 6.13\] spacing : real {#spacing-prop}

Space between [contentItem](qml-org-kde-kirigami-layouts-headerfooterlayout.md#contentItem-prop) and the header and footer items.

The content Item of the page will be positioned at this distance in pixels from the header and footer Items. The default value is zero.

This property was introduced in Qt 6.13.

## Method Documentation {#method-documentation}

### void forceLayout() {#forceLayout-method}

[HeaderFooterLayout](qml-org-kde-kirigami-layouts-headerfooterlayout.md) normally positions its header, footer and [contentItem](qml-org-kde-kirigami-layouts-headerfooterlayout.md#contentItem-prop) once per frame (at polish event). This method forces the it to recalculate the layout immediately.
