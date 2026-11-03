---
title: "NativeMenuBar QML Type"
description: "An experimental native menu bar generated from all action collections."
---

# NativeMenuBar QML Type

An experimental native menu bar generated from all action collections. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.actions.labs

## Detailed Description {#details}

This API is experimental and may change without notice.

[NativeMenuBar](qml-org-kde-kirigamiaddons-actions-labs-nativemenubar.md) combines menus with the same name from all action collections belonging to the application. Actions retain their state, icons, shortcuts, and trigger handlers.

```qml
import org.kde.kirigamiaddons.actions as KirigamiActions
import org.kde.kirigamiaddons.actions.labs as KirigamiActionsLabs

KirigamiActionsLabs.NativeMenuBar {
    application: root.application
}
```
