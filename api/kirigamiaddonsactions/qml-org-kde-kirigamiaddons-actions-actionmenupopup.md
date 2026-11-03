---
title: "ActionMenuPopup QML Type"
description: "Presents an ActionMenu as a convergent menu popup."
---

# ActionMenuPopup QML Type

Presents an [ActionMenu](qml-org-kde-kirigamiaddons-actions-actionmenu.md) as a convergent menu popup. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.actions
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

The menu keeps its items backed by the original [QAction](https://doc.qt.io/qt-6/qaction.html) instances. Consequently action state, shortcuts and trigger handlers remain owned by [ActionData](qml-org-kde-kirigamiaddons-actions-actiondata.md).

Menus with the same name contribute to the same logical menu through [ActionMenu](qml-org-kde-kirigamiaddons-actions-actionmenu.md).mergedActions. Nested [ActionMenu](qml-org-kde-kirigamiaddons-actions-actionmenu.md) objects become submenus. On desktop this is a traditional menu; on mobile it is a bottom drawer.

```qml
KirigamiActions.ActionMenu {
    id: fileMenu
    name: "file"
    text: i18nc("@title:menu", "File")
    actions: ["open", "save"]
}

KirigamiActions.ActionMenuPopup {
    menu: fileMenu
}
```
