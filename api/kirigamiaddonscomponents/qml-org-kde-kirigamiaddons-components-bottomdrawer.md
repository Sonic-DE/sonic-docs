---
title: "BottomDrawer QML Type"
description: "A bottom drawer component with a drag indicator."
---

# BottomDrawer QML Type

A bottom drawer component with a drag indicator. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.components
- Inherits: [Drawer](https://doc.qt.io/qt-6/qml-qtquick-controls-drawer.html)

## Detailed Description {#details}

Example:

```qml
import org.kde.kirigamiaddons.delegates as Delegates
import org.kde.kirigamiaddons.components as Components

Components.BottomDrawer {
    id: drawer

    headerContentItem: Kirigami.Heading {
        text: "Drawer"
    }

    Delegates.RoundedItemDelegate {
        text: "Action 1"
        icon.name: "list-add"
        onClicked: {
            doSomething()
            drawer.close()
        }
    }

    Delegates.RoundedItemDelegate {
        text: "Action 1"
        icon.name: "list-add"
        onClicked: {
            doSomething()
            drawer.close()
        }
    }
}
```

## Property Documentation {#property-documentation}

### \[default\] drawerContentItem : Item {#drawerContentItem-prop}

This property holds the content item of the drawer.

### headerContentItem : Item {#headerContentItem-prop}

This property holds the content item of the drawer header.

When no headerContentItem is set, the header will not be displayed.
