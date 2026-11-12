---
title: "FloatingToolBar QML Type"
description: "A floating toolbar to use for example in a canvas."
---

# FloatingToolBar QML Type

A floating toolbar to use for example in a canvas. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.components
- Inherits: [FloatingToolBar](qml-org-kde-kirigamiaddons-components-templates-floatingtoolbar.md)

## Detailed Description {#details}

The toolbar should be positioned with [Kirigami.Units.largeSpacing](../kirigamiplatform/qml-org-kde-kirigami-platform-units.md#largeSpacing-prop) from the border of the page.

```qml
import org.kde.kirigamiaddons.components
import org.kde.kirigami as Kirigami

FloatingToolBar {
    contentItem: Kirigami.ActionToolBar {
        actions: [
            Kirigami.Action {
                ...
            }
        ]
    }
}
```
