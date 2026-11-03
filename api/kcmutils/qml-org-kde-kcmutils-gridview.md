---
title: "GridView QML Type"
description: "A ScrollView containing a GridView, with the default behavior about sizing and background as recommended by the user interface guidelines."
---

# GridView QML Type

A [ScrollView](qml-org-kde-kcmutils-scrollview.md) containing a [GridView](qml-org-kde-kcmutils-gridview.md), with the default behavior about sizing and background as recommended by the user interface guidelines. [More...](#details)

- Import Statement: import org.kde.kcmutils
- Inherits: [ScrollView](https://doc.qt.io/qt-6/qml-qtquick-controls-scrollview.html)

## Detailed Description {#details}

For most KControl modules, it's recommended to use [GridViewKCM](qml-org-kde-kcmutils-gridviewkcm.md) as the root element of your module instead.

*See also* [GridViewKCM](qml-org-kde-kcmutils-gridviewkcm.md)

## Property Documentation {#property-documentation}

### framedView : bool {#framedView-prop}

### view : GridView {#view-prop}

Exposes the internal [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html).[GridView](qml-org-kde-kcmutils-gridview.md).

In order to set a model or a delegate to it, use the following code:

```cpp
import org.kde.kcmutils as KCMUtils

KCMUtils.GridView {
    view.model: kcm.model
    view.delegate: KCMUtils.GridDelegate { }
}
```
