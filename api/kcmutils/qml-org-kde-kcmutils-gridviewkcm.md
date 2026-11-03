---
title: "GridViewKCM QML Type"
description: "This component is intended to be used as the root item for KCMs that are based upon a grid view of thumbnails, such as the theme or wallpaper selectors."
---

# GridViewKCM QML Type

This component is intended to be used as the root item for KCMs that are based upon a grid view of thumbnails, such as the theme or wallpaper selectors. [More...](#details)

- Import Statement: import org.kde.kcmutils
- Inherits: [AbstractKCM](qml-org-kde-kcmutils-abstractkcm.md)

## Detailed Description {#details}

It contains a [GridView](qml-org-kde-kcmutils-gridview.md) as its main item.

It is possible to specify a header and footer component.

```qml
import org.kde.kcmutils as KCMutils

KCMutils.GridViewKCM {
    header: Item { }
    view.model: kcm.model
    view.delegate: KCMutils.GridDelegate { }
    footer: Item { }
}
```

## Property Documentation {#property-documentation}

### view : GridView {#view-prop}

Exposes the internal [KCMUtils](kcmutils-module.md).[GridView](qml-org-kde-kcmutils-gridview.md).

In order to set a model or a delegate to it, use the following code:

```cpp
import org.kde.kcmutils as KCMutils

KCMutils.GridViewKCM {
    view.model: kcm.model
    view.delegate: KCMutils.GridDelegate { }
}
```
