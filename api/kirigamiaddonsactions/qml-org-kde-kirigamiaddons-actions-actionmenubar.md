---
title: "ActionMenuBar QML Type"
description: "Presents all ActionCollections belonging to an application as a menu bar."
---

# ActionMenuBar QML Type

Presents all ActionCollections belonging to an application as a menu bar. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.actions
- Inherits: [MenuBar](https://doc.qt.io/qt-6/qml-qtquick-controls-menubar.html)

## Detailed Description {#details}

The menu bar uses the [ActionMenu](qml-org-kde-kirigamiaddons-actions-actionmenu.md) declarations from an [ActionCollection](qml-org-kde-kirigamiaddons-actions-actioncollection.md). Contributions with the same menu name are merged, and named actions keep their original [QAction](https://doc.qt.io/qt-6/qaction.html) state and trigger handlers.

```qml
KirigamiActions.ActionMenuBar {
    application: root.application
}
```
