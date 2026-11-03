---
title: "AlbumModelItem QML Type"
description: "An object container for defining content items to show in an AlbumMaximizeComponent."
---

# AlbumModelItem QML Type

An object container for defining content items to show in an [AlbumMaximizeComponent](qml-org-kde-kirigamiaddons-labs-components-albummaximizecomponent.md). [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.labs.components

## Detailed Description {#details}

The intended use is that a list of these can be used as the [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html) model for a [AlbumMaximizeComponent](qml-org-kde-kirigamiaddons-labs-components-albummaximizecomponent.md).

Example definition:

```qml
property list<AlbumModelItem> model: [
     AlbumModelItem {
         type: AlbumModelItem.Image
         source: "path/to/source"
         tempSource: "path/to/tempSource"
     },
     AlbumModelItem {
         type: AlbumModelItem.Video
         source: "path/to/source"
         tempSource: "path/to/tempSource"
     }
]
```

## Property Documentation {#property-documentation}

### \[default: ""\] caption : string {#caption-prop}

The caption for the item.

Typically set to the filename if no caption is available.

### source : string {#source-prop}

The source for the item.

### \[default: 0\] sourceHeight : real {#sourceHeight-prop}

The height of the source image.

Used to calculate the aspect ratio of the image.

### \[default: 0\] sourceWidth : real {#sourceWidth-prop}

The width of the source image.

Used to calculate the aspect ratio of the image.

### \[default: ""\] tempSource : string {#tempSource-prop}

Source for the temporary content.

Typically used when downloading the image to show a thumbnail or other temporary image while the main image downloads.

### type : int {#type-prop}

The delegate type that should be shown for this item.

Possible values:

| Constant | Description |
| --- | --- |
| AlbumModelItem.Image | Show an image delegate (including GIFs). |
| AlbumModelItem.Video | Show a video delegate. |
