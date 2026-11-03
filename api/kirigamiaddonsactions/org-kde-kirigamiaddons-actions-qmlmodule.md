---
title: "Kirigami Addons Actions QML Types"
description: "Declarative actions, menus, and application-window support for Kirigami applications."
---

# Kirigami Addons Actions QML Types

Declarative actions, menus, and application-window support for Kirigami applications.

The actions module connects Qt and KDE actions to a Kirigami user interface. It provides [StatefulWindow](qml-org-kde-kirigamiaddons-actions-statefulwindow.md), which restores window state and integrates standard application actions, as well as [ActionCollection](qml-org-kde-kirigamiaddons-actions-actioncollection.md), [ActionData](qml-org-kde-kirigamiaddons-actions-actiondata.md) and [StandardActionData](qml-org-kde-kirigamiaddons-actions-standardactiondata.md) for declaring named, configurable actions in QML.

The module is intended for applications that want one action definition to be reusable in several places, such as a command bar, a menu bar, a mobile menu popup, and keyboard shortcuts.

To use the module, import it in the QML files that declare or present actions:

```qml
import org.kde.kirigamiaddons.actions as KirigamiActions
```

## Application setup {#application-setup}

Use [StatefulWindow](qml-org-kde-kirigamiaddons-actions-statefulwindow.md) as the application's main window and assign an [AbstractKirigamiApplication](abstractkirigamiapplication.md) (or a subclass) to its `application` property. The default application supplies common actions such as Quit, About, the command bar, and the shortcut editor. Applications can subclass [AbstractKirigamiApplication](abstractkirigamiapplication.md) and reimplement [AbstractKirigamiApplication::setupActions](abstractkirigamiapplication.md#setupActions)() to add their own C++ actions.

The following example declares a QML action collection. Each action has a unique name within its collection. Its name, label, icon, shortcut, and trigger handler can then be shared by different presenters:

```qml
import org.kde.kirigami as Kirigami
import org.kde.kirigamiaddons.actions as KirigamiActions

KirigamiActions.StatefulWindow {
    id: root
    windowName: "MainWindow"

    KirigamiActions.ActionCollection {
        application: root.application
        name: "document"
        text: i18nc("@title:menu", "Document")

        KirigamiActions.ActionData {
            name: "document_save"
            text: i18nc("@action", "Save")
            toolTip: i18nc("@info:tooltip", "Save the current document")
            icon.name: "document-save"
            defaultShortcut: "Ctrl+S"
            onTriggered: document.save()
        }
    }
}
```

## Presenting actions {#presenting-actions}

A QML action can be connected to a named [ActionData](qml-org-kde-kirigamiaddons-actions-actiondata.md) object with the [ActionCollection](qml-org-kde-kirigamiaddons-actions-actioncollection.md) attached properties. This keeps the action's state and trigger handler in one place:

```qml
Kirigami.Action {
    ActionCollection.collection: "document"
    ActionCollection.action: "document_save"
}
```

[ActionMenu](qml-org-kde-kirigamiaddons-actions-actionmenu.md) describes a menu using action names. Use [ActionMenuBar](qml-org-kde-kirigamiaddons-actions-actionmenubar.md) to present all menus from an application on desktop, or [ActionMenuPopup](qml-org-kde-kirigamiaddons-actions-actionmenupopup.md) to present one menu with Kirigami's convergent desktop/mobile behavior. Menu contributions with the same name are merged, which lets separate pages or collections contribute items to a shared menu.

For example, a collection can declare a menu containing the actions from the previous example, including a separator:

```qml
KirigamiActions.ActionMenu {
    id: fileMenu
    name: "file"
    text: i18nc("@title:menu", "File")

    ActionMenu.Action { name: "document_save" }
    ActionMenu.Separator {}
    ActionMenu.Action { name: "quit" }
}
```

Put an [ActionMenuBar](qml-org-kde-kirigamiaddons-actions-actionmenubar.md) in the window to present the menus from all of the application's collections:

```qml
KirigamiActions.ActionMenuBar {
    application: root.application
}
```

For a menu opened from a button or another control, use [ActionMenuPopup](qml-org-kde-kirigamiaddons-actions-actionmenupopup.md) instead. Its popup adapts to the platform, using a traditional menu on desktop and a bottom drawer on mobile:

```qml
KirigamiActions.ActionMenuPopup {
    id: fileMenuPopup
    menu: fileMenu
}

Kirigami.Icon {
    source: "document-open"
    MouseArea {
        anchors.fill: parent
        onClicked: fileMenuPopup.popup()
    }
}
```

## Context-sensitive actions {#context-sensitive-actions}

[ActionContext](qml-org-kde-kirigamiaddons-actions-actioncontext.md) limits an action to a page, document, or tool. Set its `active` property according to the current UI state and assign it to an [ActionData](qml-org-kde-kirigamiaddons-actions-actiondata.md) object's `contexts` property. When several contexts are active, the context with the highest priority is used.

```qml
KirigamiActions.ActionContext {
    id: editorContext
    active: root.pageStack.currentItem === editorPage
}

KirigamiActions.ActionData {
    name: "document_save"
    contexts: editorContext
}
```

## Standard actions and shortcuts {#standard-actions-and-shortcuts}

[StandardActionData](qml-org-kde-kirigamiaddons-actions-standardactiondata.md) creates a KDE standard action with its conventional name, label, icon, and default shortcut. Put it alongside [ActionData](qml-org-kde-kirigamiaddons-actions-actiondata.md) as a child of [ActionCollection](qml-org-kde-kirigamiaddons-actions-actioncollection.md). Once a collection is registered with the application, its configurable shortcuts are available through the standard shortcut editor and its actions are available to the command bar.

```qml
KirigamiActions.StandardActionData {
    standardAction: KirigamiActions.StandardActionData.Copy
}
```

*See also* [StatefulWindow](qml-org-kde-kirigamiaddons-actions-statefulwindow.md), [AbstractKirigamiApplication](abstractkirigamiapplication.md), [ActionCollection](qml-org-kde-kirigamiaddons-actions-actioncollection.md), [ActionData](qml-org-kde-kirigamiaddons-actions-actiondata.md), [ActionContext](qml-org-kde-kirigamiaddons-actions-actioncontext.md), [ActionMenu](qml-org-kde-kirigamiaddons-actions-actionmenu.md), [ActionMenuBar](qml-org-kde-kirigamiaddons-actions-actionmenubar.md), [ActionMenuPopup](qml-org-kde-kirigamiaddons-actions-actionmenupopup.md), [StandardActionData](qml-org-kde-kirigamiaddons-actions-standardactiondata.md)

## Contents

- [ActionCollection](qml-org-kde-kirigamiaddons-actions-actioncollection.md): A container for a set of QAction objects.
- [ActionContext](qml-org-kde-kirigamiaddons-actions-actioncontext.md): An activation scope for declarative actions.
- [ActionData](qml-org-kde-kirigamiaddons-actions-actiondata.md): A declarative action with a configurable shortcut.
- [ActionGroup](qml-org-kde-kirigamiaddons-actions-actiongroup.md): A group of actions with automatic exclusivity.
- [ActionMenu](qml-org-kde-kirigamiaddons-actions-actionmenu.md): A declarative menu containing named actions and separators.
- [ActionMenuBar](qml-org-kde-kirigamiaddons-actions-actionmenubar.md): Presents all ActionCollections belonging to an application as a menu bar.
- [ActionMenuPopup](qml-org-kde-kirigamiaddons-actions-actionmenupopup.md): Presents an ActionMenu as a convergent menu popup.
- [IconGroup](qml-org-kde-kirigamiaddons-actions-icongroup.md): Grouped icon properties for ActionData.
- [StandardActionData](qml-org-kde-kirigamiaddons-actions-standardactiondata.md): A declarative action based on a KDE standard action.
- [StatefulWindow](qml-org-kde-kirigamiaddons-actions-statefulwindow.md): StatefulWindow takes care of providing standard functionalities for your application main window.
