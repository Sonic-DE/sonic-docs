---
title: "ActionCollection QML Type"
description: "A container for a set of QAction objects."
---

# ActionCollection QML Type

A container for a set of [QAction](https://doc.qt.io/qt-6/qaction.html) objects. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.actions

## Detailed Description {#details}

[KirigamiActionCollection](kirigamiactioncollection.md) manages a set of [QAction](https://doc.qt.io/qt-6/qaction.html) objects. It allows them to be grouped for organized presentation of configuration to the user, saving + loading of configuration, and optionally for automatic plugging into specified widget(s).

Additionally, [KirigamiActionCollection](kirigamiactioncollection.md) provides several convenience functions for locating named actions, and actions grouped by [QActionGroup](https://doc.qt.io/qt-6/qactiongroup.html).

In QML, declare [ActionData](qml-org-kde-kirigamiaddons-actions-actiondata.md) and [StandardActionData](qml-org-kde-kirigamiaddons-actions-standardactiondata.md) as children. They are registered with the supplied [AbstractKirigamiApplication](abstractkirigamiapplication.md) and become available to its command bar and configurable shortcut editor.

```qml
import org.kde.kirigamiaddons.actions as KirigamiActions

KirigamiActions.StatefulWindow {
    id: root
    application: MyApplication {}

    KirigamiActions.ActionCollection {
        application: root.application
        name: "main"
        text: i18n("Main Actions")

        KirigamiActions.ActionData {
            name: "open_search"
            text: i18n("Search")
            icon.name: "search"
            defaultShortcut: "Ctrl+F"
        }
    }
}
```

A QML action can refer to an action in a collection with the attached properties `ActionCollection.collection` and `ActionCollection.action`:

```cpp
Kirigami.Action {
    ActionCollection.collection: "main"
    ActionCollection.action: "open_search"
    onTriggered: search.open()
}
```

## Property Documentation {#property-documentation}

### action : string {#action-prop}

The name of the action in the collection.

### \[read-only\] actions : list\<ActionData\> {#actions-prop}

The [ActionData](qml-org-kde-kirigamiaddons-actions-actiondata.md) and [StandardActionData](qml-org-kde-kirigamiaddons-actions-standardactiondata.md) children in this collection.

### application : AbstractKirigamiApplication {#application-prop}

The application to which the declared actions are added.

### collection : string {#collection-prop}

The name of the action collection.

### configGroup : string {#configGroup-prop}

### configIsGlobal : bool {#configIsGlobal-prop}

### \[read-only\] menus : list\<ActionMenu\> {#menus-prop}

Declarative menus contributed by this collection.

### name : string {#name-prop}

The unique name of the collection.

### text : string {#text-prop}

The user-visible name shown for the collection in shortcut configuration.
