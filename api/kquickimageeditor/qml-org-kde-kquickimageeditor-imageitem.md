---
title: "ImageItem QML Type"
description: "QML components providing basic image editing capabilities."
---

# ImageItem QML Type

QML components providing basic image editing capabilities. [More...](#details)

- Import Statement: import org.kde.kquickimageeditor

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### fillMode : FillMode {#fillMode-prop}

| Constant | Description |
| --- | --- |
| ImageItem.Stretch | The image is scaled to fit. |
| ImageItem.PreserveAspectFit | The image is scaled uniformly to fit without cropping. |
| ImageItem.PreserveAspectCrop | The image is scaled uniformly to fill, cropping if necessary. |
| ImageItem.Tile | The image is duplicated horizontally and vertically. |
| ImageItem.TileVertically | The image is stretched horizontally and tiled vertically. |
| ImageItem.TileHorizontally | The image is stretched vertically and tiled horizontally. |

### horizontalPadding : int {#horizontalPadding-prop}

### image : image {#image-prop}

### nativeHeight : int {#nativeHeight-prop}

### nativeWidth : int {#nativeWidth-prop}

### null : bool {#null-prop}

### paintedHeight : int {#paintedHeight-prop}

### paintedWidth : int {#paintedWidth-prop}

### verticalPadding : int {#verticalPadding-prop}
