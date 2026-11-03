---
title: "WindowThumbnail QML Type"
description: "Renders a thumbnail for the window specified by the winId property."
---

# WindowThumbnail QML Type

Renders a thumbnail for the window specified by the `winId` property. [More...](#details)

- Import Statement: import org.kde.plasma.core
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

This declarative item is able to render a live updating thumbnail for the window specified by the given `winId` property. If it is not possible to get the thumbnail, the window's icon is rendered instead or in case that the window Id is invalid a generic fallback icon is used.

The thumbnail does not necessarily fill out the complete geometry as the thumbnail gets scaled keeping the aspect ratio. This means the thumbnail gets rendered into the center of the item's geometry.

> **Note:** live updating thumbnails are only implemented on the X11 platform. On X11 a running compositor is not required as this item takes care of redirecting the window. For technical reasons the window's frame is not included on X11.

If the window closes, the thumbnail does not get destroyed, which allows to have a window close animation.

Example usage:

```qml
WindowThumbnail {
    winId: 102760466
}
```

## Property Documentation {#property-documentation}

### paintedHeight : real {#paintedHeight-prop}

### paintedWidth : real {#paintedWidth-prop}

### thumbnailAvailable : bool {#thumbnailAvailable-prop}

### winId : int {#winId-prop}
