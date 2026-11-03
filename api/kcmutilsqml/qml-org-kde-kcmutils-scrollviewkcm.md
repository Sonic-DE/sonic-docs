---
title: "ScrollViewKCM QML Type"
description: "This component is intended to be used as the root item for KCMs that are based upon a list view or another vertical flickable."
---

# ScrollViewKCM QML Type

This component is intended to be used as the root item for KCMs that are based upon a list view or another vertical flickable. [More...](#details)

- Import Statement: import org.kde.kcmutils
- Inherits: [AbstractKCM](qml-org-kde-kcmutils-abstractkcm.md)

## Detailed Description {#details}

It contains a [ScrollView](qml-org-kde-kcmutils-scrollview.md) as its main item.

It is possible to specify a header and footer component.

```cpp
import org.kde.kcmutils as KCMUtils

KCMUtils.ScrollViewKCM {
    header: Item { }
    view: ListView { }
    footer: Item { }
}
```

## Property Documentation {#property-documentation}

### view : ScrollView {#view-prop}

Exposes the internal flickable.
