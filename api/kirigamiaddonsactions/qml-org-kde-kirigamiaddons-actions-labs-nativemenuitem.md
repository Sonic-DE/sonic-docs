---
title: "NativeMenuItem QML Type"
description: "An experimental Qt.labs.platform.MenuItem defined by a QAction."
---

# NativeMenuItem QML Type

An experimental Qt.labs.platform.[MenuItem](https://doc.qt.io/qt-6/qml-qtquick-controls-menuitem.html) defined by a [QAction](https://doc.qt.io/qt-6/qaction.html). [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.actions.labs
- Inherits: [MenuItem](https://doc.qt.io/qt-6/qml-qtquick-controls-menuitem.html)

## Detailed Description {#details}

This API is experimental and may change without notice.

```qml
import Qt.labs.platform as Labs
import org.kde.kirigamiaddons.actions as KirigamiActions
import org.kde.kirigamiaddons.actions.labs as KirigamiActionsLabs

KirigamiActions.StatefulWindow {
    application: MyKoolApp

    Labs.MenuBar {
        Labs.Menu {
            KirigamiActionsLabs.NativeMenuItem {
                actionName: 'add_notebook'
                application: MyKoolApp
            }
        }
    }
}
```

## Property Documentation {#property-documentation}

### actionName : string {#actionName-prop}

This property holds the action name defined in your [AbstractKirigamiApplication](abstractkirigamiapplication.md) implementation.

### actionObject : QtObject {#actionObject-prop}

This property can be used by generated menus to provide the resolved action directly when actions with the same name exist in multiple collections.

### \[read-only\] alternateShortcut : Shortcut {#alternateShortcut-prop}

### application : AbstractKirigamiApplication {#application-prop}

This property holds the [AbstractKirigamiApplication](abstractkirigamiapplication.md) where the action is defined.
