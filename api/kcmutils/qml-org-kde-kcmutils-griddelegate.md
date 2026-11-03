---
title: "GridDelegate QML Type"
description: "Base delegate for KControlmodules based on Grid views of thumbnails."
---

# GridDelegate QML Type

Base delegate for KControlmodules based on Grid views of thumbnails. [More...](#details)

- Import Statement: import org.kde.kcmutils
- Inherits: [ItemDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-itemdelegate.html)

## Detailed Description {#details}

Use the onClicked signal handler for managing the main action when the user clicks on the thumbnail.

## Property Documentation {#property-documentation}

### actions : list\<Kirigami.Action\> {#actions-prop}

A list of extra actions for the thumbnails.

They will be shown as icons on the bottom-right corner of the thumbnail on mouse hover.

### subtitle : string {#subtitle-prop}

Optional string for the text to show below the main label.

### thumbnail : Item {#thumbnail-prop}

The item actually implementing the thumbnail: the visualization is up to the implementation.

### thumbnailAvailable : bool {#thumbnailAvailable-prop}

Set it to true when a thumbnail is actually available.

When false, only an icon will be shown instead of the actual thumbnail ("edit-none" if pluginName is "None", otherwise it uses "view-preview").

### toolTip : string {#toolTip-prop}

String for a tooltip for the whole delegate.
