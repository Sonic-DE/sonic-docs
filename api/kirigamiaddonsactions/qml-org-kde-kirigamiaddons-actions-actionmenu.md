---
title: "ActionMenu QML Type"
description: "A declarative menu containing named actions and separators."
---

# ActionMenu QML Type

A declarative menu containing named actions and separators. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.actions

## Detailed Description {#details}

The compact `actions` property can be used for menus containing only actions. Use the ordered default property when separators or explicit ordering are needed.

Each entry in `mergedItems` contains `type` and `name`. Action entries also contain the resolved `action` object used by menu presenters.

```qml
KirigamiActions.ActionMenu {
    name: "file"
    text: i18nc("@title:menu", "File")

    ActionMenu.Action { name: "open_pdf" }
    ActionMenu.Separator {}
    ActionMenu.Action { name: "quit" }
}

// Set \c menuBarVisible to false for menus presented only by ActionMenuPopup.
```
