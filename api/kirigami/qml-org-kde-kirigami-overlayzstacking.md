---
title: "OverlayZStacking QML Type"
description: "An attached property that manages z-index for stacking overlays relative to each other. This type was introduced in Qt 6.0."
---

# OverlayZStacking QML Type

An attached property that manages z-index for stacking overlays relative to each other. This type was introduced in Qt 6.0. [More...](#details)

- Import Statement: import org.kde.kirigami
- Since: Qt 6.0

## Detailed Description {#details}

When a popup is about to show, [OverlayZStacking](qml-org-kde-kirigami-overlayzstacking.md) object kicks in, searches for the next nearest popup in the [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) hierarchy of items, and sets its z value to the biggest of two: current stacking value for its layer, or parent's z index + 1.

This way [OverlayZStacking](qml-org-kde-kirigami-overlayzstacking.md) algorithm ensures that a popup is always stacked higher than its logical parent popup, but also no lower than its siblings on the same logical layer.

```cpp
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami

QQC2.Popup {
    Kirigami.OverlayZStacking.layer: Kirigami.OverlayZStacking.ToolTip
    z: Kirigami.OverlayZStacking.z
}
```

## Attached Property Documentation {#attached-property-documentation}

### OverlayZStacking.layer : enumeration {#layer-attached-prop}

The logical stacking layer of attachee popup, akin to window manager's layers.

| Constant |
| --- |
| OverlayZStacking.DefaultLowest |
| OverlayZStacking.Drawer |
| OverlayZStacking.FullScreen |
| OverlayZStacking.Dialog |
| OverlayZStacking.Menu |
| OverlayZStacking.Notification |
| OverlayZStacking.ToolTip |

### OverlayZStacking.z : real {#z-attached-prop}

An optimal z-index that attachee popup should bind to.
