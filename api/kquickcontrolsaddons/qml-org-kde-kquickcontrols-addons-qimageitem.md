---
title: "QImageItem QML Type"
description: "Extensions to Qt Quick Controls."
---

# QImageItem QML Type

Extensions to Qt Quick Controls. [More...](#details)

- Import Statement: import org.kde.kquickcontrols.addons

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### fillMode : FillMode {#fillMode-prop}

| Constant | Description |
| --- | --- |
| Stretch | The image is scaled to fit. |
| PreserveAspectFit | the image is scaled uniformly to fit without cropping. |
| PreserveAspectCrop | The image is scaled uniformly to fill, cropping if necessary. |
| Tile | The image is duplicated horizontally and vertically. |
| TileVertically | The image is stretched horizontally and tiled vertically. |
| TileHorizontally | The image is stretched vertically and tiled horizontally. |
| Pad (since Qt 5.96) | The image is not transformed. |

### image : QImage {#image-prop}

### nativeHeight : int {#nativeHeight-prop}

### nativeWidth : int {#nativeWidth-prop}

### null : bool {#null-prop}

### paintedHeight : int {#paintedHeight-prop}

### paintedWidth : int {#paintedWidth-prop}

## Signal Documentation {#signal-documentation}

### fillModeChanged() {#fillModeChanged-signal}

> **Note:** The corresponding handler is `onFillModeChanged`.

### imageChanged() {#imageChanged-signal}

> **Note:** The corresponding handler is `onImageChanged`.

### nativeHeightChanged() {#nativeHeightChanged-signal}

> **Note:** The corresponding handler is `onNativeHeightChanged`.

### nativeWidthChanged() {#nativeWidthChanged-signal}

> **Note:** The corresponding handler is `onNativeWidthChanged`.

### nullChanged() {#nullChanged-signal}

> **Note:** The corresponding handler is `onNullChanged`.

### paintedHeightChanged() {#paintedHeightChanged-signal}

> **Note:** The corresponding handler is `onPaintedHeightChanged`.

### paintedWidthChanged() {#paintedWidthChanged-signal}

> **Note:** The corresponding handler is `onPaintedWidthChanged`.
