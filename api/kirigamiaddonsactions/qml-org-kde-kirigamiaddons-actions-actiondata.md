---
title: "ActionData QML Type"
description: "A declarative action with a configurable shortcut."
---

# ActionData QML Type

A declarative action with a configurable shortcut. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.actions
- In C++: [QAction](https://doc.qt.io/qt-6/qaction.html)

## Detailed Description {#details}

This element needs to always be declared as a child of [ActionCollection](qml-org-kde-kirigamiaddons-actions-actioncollection.md). It is the declarative representation of a named action within the application with a user-configurable shortcut.

This element can be assigned to one or more [ActionContext](qml-org-kde-kirigamiaddons-actions-actioncontext.md) objects through the `contexts` property. An inactive context disables and hides the action by default. When multiple contexts are active, [activeContext](qml-org-kde-kirigamiaddons-actions-actiondata.md#activeContext-prop) refers to the active context with the highest priority.

```qml
KirigamiActions.ActionContext {
    id: documentContext
    active: pageStack.currentItem === editorPage
}
KirigamiActions.ActionData {
    name: "save"
    contexts: documentContext
}
```

The regular [QAction](https://doc.qt.io/qt-6/qaction.html) properties, such as text, toolTip, enabled, checkable and checked, can be assigned directly in QML. Its name must be unique within the containing collection.

The action is registered with the [AbstractKirigamiApplication](abstractkirigamiapplication.md) when its collection is complete. It is therefore available to the command bar and its shortcut can be configured by the user in the standard shortcut editor.

```cpp
import org.kde.kirigamiaddons.actions as KirigamiActions

KirigamiActions.StatefulWindow {
    id: root
    application: MyApplication {}

    KirigamiActions.ActionCollection {
        application: root.application
        name: "document"
        text: i18n("Document Actions")

        KirigamiActions.ActionData {
            name: "document_save"
            text: i18n("Save")
            toolTip: i18n("Save the current document")
            icon.name: "document-save"
            defaultShortcut: "Ctrl+S"
            onTriggered: document.save()
        }
    }
}
```

*See also* [ActionCollection](qml-org-kde-kirigamiaddons-actions-actioncollection.md), [StandardActionData](qml-org-kde-kirigamiaddons-actions-standardactiondata.md)

## Property Documentation {#property-documentation}

### action : QtQuick.Controls::Action {#action-prop}

This property holds the QML Action this [ActionData](qml-org-kde-kirigamiaddons-actions-actiondata.md) is associated to, if any. Since [ActionData](qml-org-kde-kirigamiaddons-actions-actiondata.md) is just a description of an action, in order to be an active working action it has to be associated with a QML Action instance, preferably a Kirigami.Action specialization.

It can be associated either here by binding this property to the id of an Action instance or from the Action instance using the [ActionCollection](qml-org-kde-kirigamiaddons-actions-actioncollection.md) attached property.

Direct example:

```cpp
KirigamiActions.ActionCollection {
    application: root.application
    KirigamiActions.ActionData {
        name: "copy"
        icon.name: "edit-copy"
        text: i18n("Copy")
        action: copyAction
    }
}

Kirigami.Action {
    id: copyAction
    onTriggered: document.copy()
}
```

Attached property example:

```cpp
KirigamiActions.ActionCollection {
    application: root.application
    name: "EditActions"
    KirigamiActions.ActionData {
        name: "copy"
        icon.name: "edit-copy"
        text: i18n("Copy")
    }
}

Kirigami.Action {
    KirigamiActions.ActionCollection.collection: "EditActions"
    KirigamiActions.ActionCollection.action: "copy"
    onTriggered: document.copy()
}
```

### actionGroup : ActionGroup {#actionGroup-prop}

The optional group used to make related actions mutually exclusive.

Set `checkable` to true on the grouped actions. The group can be declared as a sibling of the actions in an [ActionCollection](qml-org-kde-kirigamiaddons-actions-actioncollection.md).

```qml
KirigamiActions.ActionGroup {
    id: modes
    exclusive: true
}
KirigamiActions.ActionData {
    name: "mode_one"
    checkable: true
    actionGroup: modes
}
```

### activeContext : ActionContext {#activeContext-prop}

The highest-priority active context, or null when no context is active.

### contextActive : bool {#contextActive-prop}

Whether at least one of this action's contexts is active.

### contextEnabled : bool {#contextEnabled-prop}

Whether an inactive context disables this action. Defaults to true.

### contextVisible : bool {#contextVisible-prop}

Whether an inactive context hides this action. Defaults to true.

### contexts : list\<ActionContext\> {#contexts-prop}

The contexts that control this action.

### data : var {#data-prop}

Additional data associated with the action.

### defaultAlternateShortcut : keysequence {#defaultAlternateShortcut-prop}

The alternate shortcut assigned when no user-configured shortcut exists.

### defaultShortcut : keysequence {#defaultShortcut-prop}

The shortcut assigned when no user-configured shortcut exists.

The value can be a string containing one or more key presses, such as `"Ctrl+E,Ctrl+W"`, or a Qt standard key sequence. The user's configured shortcut takes precedence over this value.

```qml
ActionData {
    name: "close_document"
    defaultShortcut: "Ctrl+W"
}
```

### icon group {#icon-prop}

**icon.cache : bool**

**icon.color : color**

**icon.height : real**

**icon.name : string**

**icon.source : string**

**icon.width : real**

Description for the icon to use, which can be specified by name or path.

### name : string {#name-prop}

The unique name of the action within its collection. It should be set only once.
