---
title: "ConvergentContextMenu QML Type"
description: "A context menu that can appear as a standard menu, bottom drawer, or dialog."
---

# ConvergentContextMenu QML Type

A context menu that can appear as a standard menu, bottom drawer, or dialog. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.components
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

Add [QtQuick Controls actions](https://doc.qt.io/qt-6/qml-qtquick-controls-action.html) or [Kirigami actions](../kirigami/qml-org-kde-kirigami-action.md) as child items. Kirigami actions can contain nested actions. By default, the menu uses a standard context menu on desktop and a bottom drawer on mobile. A Kirigami action's `displayComponent` can provide a custom delegate in [BottomDrawer](qml-org-kde-kirigamiaddons-components-bottomdrawer.md) and Dialog modes.

```qml
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami
import org.kde.kirigamiaddons.components as Components
import org.kde.kirigamiaddons.formcard as FormCard

Components.ConvergentContextMenu {
    id: root

    headerContentItem: RowLayout {
        spacing: Kirigami.Units.smallSpacing
        Kirigami.Avatar { ... }

        Kirigami.Heading {
            level: 2
            text: "Room Name"
        }
    }

    Controls.Action {
        text: i18nc("@action:inmenu", "Simple Action")
    }

    Kirigami.Action {
        text: i18nc("@action:inmenu", "Nested Action")

        Controls.Action { ... }

        Controls.Action { ... }

        Controls.Action { ... }
    }

    Kirigami.Action {
        text: i18nc("@action:inmenu", "Nested Action with Multiple Choices")

        Kirigami.Action {
            text: i18nc("@action:inmenu", "Follow Global Settings")
            checkable: true
            autoExclusive: true // Since KF 6.10
        }

        Kirigami.Action {
            text: i18nc("@action:inmenu", "Enabled")
            checkable: true
            autoExclusive: true // Since KF 6.10
        }

        Kirigami.Action {
            text: i18nc("@action:inmenu", "Disabled")
            checkable: true
            autoExclusive: true // Since KF 6.10
        }
    }

    // A custom FormCard delegate is used in BottomDrawer and Dialog modes.
    Kirigami.Action {
        displayComponent: FormCard.FormButtonDelegate { ... }
    }
}
```

For a `ListView`, avoid creating a separate menu instance for every delegate. Keep one menu for the view, or define a `Component` and create a menu when it is needed. The example below creates a menu on demand and passes the current delegate's index to it:

```qml
import QtQuick
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami
import org.kde.kirigamiaddons.components as Addons

ListView {
    model: 10
    delegate: Controls.ItemDelegate {
        text: index

        function openContextMenu(): void {
            const item = menu.createObject(Controls.Overlay.overlay, {
                index,
            });
            item.popup();
        }

        onPressAndHold: openContextMenu()

        // Open the menu for a platform context-menu request.
        Controls.ContextMenu.onRequested: (position) => openContextMenu()
    }

    Component {
        id: menu

        Addons.ConvergentContextMenu {
            required property int index

            Controls.Action {
                text: i18nc("@action:inmenu", "Action 1")
            }

            Kirigami.Action {
                text: i18nc("@action:inmenu", "Action 2")

                Controls.Action {
                    text: i18nc("@action:inmenu", "Sub-action")
                }
            }
        }
    }
}
```

## Property Documentation {#property-documentation}

### \[default\] actions : list\<Action\> {#actions-prop}

The actions displayed in the menu. This is the default property, so add actions as child items.

Each item can be a [QtQuick Controls action](https://doc.qt.io/qt-6/qml-qtquick-controls-action.html) or a [Kirigami action](../kirigami/qml-org-kde-kirigami-action.md). Kirigami actions can contain subactions.

### displayMode : int {#displayMode-prop}

The presentation used to display the context menu.

By default, this is [ContextMenu](https://doc.qt.io/qt-6/qml-qtquick-controls-contextmenu.html) on desktop and [BottomDrawer](qml-org-kde-kirigamiaddons-components-bottomdrawer.md) on mobile.

| Constant | Description |
| --- | --- |
| ConvergentContextMenu.ContextMenu | A standard context menu, typically used on desktop platforms. |
| ConvergentContextMenu.BottomDrawer | A bottom drawer that displays nested actions on separate pages. |
| ConvergentContextMenu.Dialog | A dialog that displays nested actions on separate pages. |

### headerContentItem : Item {#headerContentItem-prop}

Optional item displayed above the actions in the menu.

> **Note:** This item is shown only at the top level in [BottomDrawer](qml-org-kde-kirigamiaddons-components-bottomdrawer.md) and Dialog display modes. It is not shown in [ContextMenu](https://doc.qt.io/qt-6/qml-qtquick-controls-contextmenu.html) mode.

### opened : bool {#opened-prop}

Whether the context menu is open.

> **Note:** Changing this property does not open or close the menu. Use [popup](qml-org-kde-kirigamiaddons-components-convergentcontextmenu.md#popup-method)() and [close](qml-org-kde-kirigamiaddons-components-convergentcontextmenu.md#close-method)() to control it.

## Signal Documentation {#signal-documentation}

### closed() {#closed-signal}

Emitted when the context menu is closed.

> **Note:** The corresponding handler is `onClosed`.

## Method Documentation {#method-documentation}

### close() {#close-method}

Close the currently open context menu.

### popup(*parent* = null, *position* = null) {#popup-method}

Open the context menu.

`parent` The item that owns the menu and, in [ContextMenu](https://doc.qt.io/qt-6/qml-qtquick-controls-contextmenu.html) mode, the item it is positioned relative to. If omitted, the menu uses this component as its parent.

`position` The location in `parent`'s coordinate system where a [ContextMenu](https://doc.qt.io/qt-6/qml-qtquick-controls-contextmenu.html) should open. This argument is used only in [ContextMenu](https://doc.qt.io/qt-6/qml-qtquick-controls-contextmenu.html) mode.
