---
title: "PlasmaQuick::AppletPopup Class"
description: "The AppletPopup class shows a popup for an applet either in the panel or on the desktop."
---

# PlasmaQuick::AppletPopup Class

The [AppletPopup](plasmaquick-appletpopup.md) class shows a popup for an applet either in the panel or on the desktop. [More...](#details)

- **Header:** `#include <PlasmaQuick/AppletPopup>`
- **CMake:** `find_package(PlasmaQuick REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Plasma::PlasmaQuick)`
- **Inherits:** [PlasmaQuick::PopupPlasmaWindow](plasmaquick-popupplasmawindow.md)

[List of all members, including inherited members](plasmaquick-appletpopup-members.md)

## Properties

- [appletInterface : QQuickItem\*](#appletInterface-prop)
- [hideOnWindowDeactivate : bool](#hideOnWindowDeactivate-prop)

## Detailed Description {#details}

In addition to the new API this class is resizable and can forward any input events received on the margin to the main item

Size hints are transferred from the mainItem's size hints.

## Property Documentation {#property-documentation}

### appletInterface : QQuickItem\* {#appletInterface-prop}

This property holds a pointer to the AppletInterface used by

**Access functions:**

- `QQuickItem` \***appletInterface**() const
- `void` **setAppletInterface**(`QQuickItem` \**appletInterface*)

**Notifier signal:**

- `void` **appletInterfaceChanged**()

### hideOnWindowDeactivate : bool {#hideOnWindowDeactivate-prop}

Whether the dialog should be hidden when the dialog loses focus.

The default value is `false`.

**Access functions:**

- `bool` **hideOnWindowDeactivate**() const
- `void` **setHideOnWindowDeactivate**(`bool` *hideOnWindowDeactivate*)

**Notifier signal:**

- `void` **hideOnWindowDeactivateChanged**()
