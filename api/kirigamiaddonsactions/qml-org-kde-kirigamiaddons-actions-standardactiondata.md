---
title: "StandardActionData QML Type"
description: "A declarative action based on a KDE standard action."
---

# StandardActionData QML Type

A declarative action based on a KDE standard action. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.actions

## Detailed Description {#details}

[StandardActionData](qml-org-kde-kirigamiaddons-actions-standardactiondata.md) provides the conventional name, label, icon and default shortcut for the selected StandardAction. It must be declared as a child of [ActionCollection](qml-org-kde-kirigamiaddons-actions-actioncollection.md).

```qml
KirigamiActions.ActionCollection {
    application: root.application
    KirigamiActions.StandardActionData {
        standardAction: KirigamiActions.StandardActionData.Copy
    }
}
```

*See also* [ActionCollection](qml-org-kde-kirigamiaddons-actions-actioncollection.md), [ActionData](qml-org-kde-kirigamiaddons-actions-actiondata.md)

## Property Documentation {#property-documentation}

### standardAction : StandardAction {#standardAction-prop}

The KDE standard action represented by this object.
