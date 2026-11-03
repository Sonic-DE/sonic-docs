---
title: "ScrollView QML Type"
description: "A ScrollView containing a GridView, with the default behavior about sizing and background as recommended by the user interface guidelines."
---

# ScrollView QML Type

A [ScrollView](qml-org-kde-kcmutils-scrollview.md) containing a [GridView](qml-org-kde-kcmutils-gridview.md), with the default behavior about sizing and background as recommended by the user interface guidelines. [More...](#details)

- Import Statement: import org.kde.kcmutils
- Inherits: [ScrollView](https://doc.qt.io/qt-6/qml-qtquick-controls-scrollview.html)

## Detailed Description {#details}

For most KControl modules, it's recommended to use instead the [GridViewKCM](qml-org-kde-kcmutils-gridviewkcm.md) component as the root element of your module.

```cpp
import org.kde.kcmutils as KCMUtils

KCMUtils.ScrollView {
    view: ListView { }
}
```

*See also* [GridViewKCM](qml-org-kde-kcmutils-gridviewkcm.md)

## Property Documentation {#property-documentation}

### framedView : bool {#framedView-prop}

### view : Flickable {#view-prop}

Exposes the internal flickable.
