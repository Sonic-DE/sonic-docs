---
title: "Highlight QML Type"
description: "Highlight for a list or grid item."
---

# Highlight QML Type

Highlight for a list or grid item. [More...](#details)

- Import Statement: import org.kde.plasma.extras
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

Highlight provides the highlight used to indicate the active item in a model view. It is typically used in conjunction with the [ListView::highlight](https://doc.qt.io/qt-6/qml-qtquick-listview.html#highlight-prop) or the [GridView::highlight](https://doc.qt.io/qt-6/qml-qtquick-gridview.html#highlight-prop) properties.

Provides built-in animation of Behavior on opacity Easing.OutQuad for a duration of 50ms (defined in Kirigami.Units.veryShortDuration).

```qml
import QtQuick
import org.kde.plasma.extras as PlasmaExtras

ListView {
    highlightFollowsCurrentItem: true
    highlight: PlasmaExtras.Highlight { }
    highlightMoveDuration: 0
    highlightResizeDuration: 0
    currentIndex: -1
}
```

## Property Documentation {#property-documentation}

### active : bool {#active-prop}

This property holds whether the item is active. True by default. Set it to false to visually mark an item that's in the "current item" or "selected" state but is not currently being hovered.

### hovered : bool {#hovered-prop}

This property holds whether the control is hovered.

This is set automatically when used in a [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html) and [GridView](https://doc.qt.io/qt-6/qml-qtquick-gridview.html).

### marginHints : int {#marginHints-prop}

This property holds the margin hints used by the background.

### pressed : bool {#pressed-prop}

This property holds whether the highlight has a pressed appearance.
