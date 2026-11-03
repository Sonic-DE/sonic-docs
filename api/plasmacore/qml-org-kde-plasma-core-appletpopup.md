---
title: "AppletPopup QML Type"
description: "Shows a popup for an applet either in the panel or on the desktop."
---

# AppletPopup QML Type

Shows a popup for an applet either in the panel or on the desktop. [More...](#details)

- Import Statement: import org.kde.plasma.core
- In C++: [AppletPopup](../plasmaquick/plasmaquick-appletpopup.md)
- Inherits: [PopupPlasmaWindow](qml-org-kde-plasma-core-popupplasmawindow.md)

## Detailed Description {#details}

In addition to the new API this class is resizable and can forward any input events received on the margin to the main item

Size hints are transferred from the mainItem's size hints.

## Property Documentation {#property-documentation}

### appletInterface : Item {#appletInterface-prop}

This property holds a pointer to the AppletInterface used by

### hideOnWindowDeactivate : bool {#hideOnWindowDeactivate-prop}

Whether the dialog should be hidden when the dialog loses focus.

The default value is `false`.
