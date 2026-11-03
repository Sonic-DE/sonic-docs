---
title: "ImageMaximizeDelegate QML Type"
description: "Reusable controls and visual components for Kirigami applications.."
---

# ImageMaximizeDelegate QML Type

Reusable controls and visual components for Kirigami applications.. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.labs.components
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### \[required\] caption : string {#caption-prop}

The caption for the item.

Typically set to the filename if no caption is available.

> **Note:** Declared here so that parent components can access this parameter when used as a [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html) delegate.

### \[default: Kirigami.Units.largeSpacing\] padding : var {#padding-prop}

The padding around the content image.

The padding is factored in when calculating the maximum size of the content image.

### \[default: 0\] rotationAngle : int {#rotationAngle-prop}

The angle by which the content image is rotated.

### \[default: 1\] scaleFactor : var {#scaleFactor-prop}

Multiple by which the image is scaled.

### \[required\] source : string {#source-prop}

The source for the image to be viewed.

### \[required\] sourceHeight : real {#sourceHeight-prop}

The size of the source image.

This is used to calculate the maximum size of the content and temporary image.

### \[required\] sourceWidth : real {#sourceWidth-prop}

The size of the source image.

This is used to calculate the maximum size of the content and temporary image.

### \[required\] tempSource : string {#tempSource-prop}

Source for the temporary content.

Typically used when downloading the image to show a thumbnail or other temporary image while the main image downloads.

### \[read-only\] type : int {#type-prop}

The delegate type for this item.

> **Note:** Declared here so that parent components can access this parameter when used as a [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html) delegate.

## Signal Documentation {#signal-documentation}

### backgroundClicked() {#backgroundClicked-signal}

Emitted when the background space around the content item is clicked.

> **Note:** The corresponding handler is `onBackgroundClicked`.

### itemRightClicked() {#itemRightClicked-signal}

Emitted when the content image is right clicked.

> **Note:** The corresponding handler is `onItemRightClicked`.

## Method Documentation {#method-documentation}

### pause() {#pause-method}

Pause media playback.

### play() {#play-method}

Start media playback.
