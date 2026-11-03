---
title: "PopupPlasmaWindow QML Type"
description: "Styled Plasma window that can be positioned relative to an existing Item on another window."
---

# PopupPlasmaWindow QML Type

Styled Plasma window that can be positioned relative to an existing Item on another window. [More...](#details)

- Import Statement: import org.kde.plasma.core
- In C++: [PopupPlasmaWindow](../plasmaquick/plasmaquick-popupplasmawindow.md)
- Inherited By: [AppletPopup](qml-org-kde-plasma-core-appletpopup.md)

## Detailed Description {#details}

When shown the popup is placed correctly.

On Wayland this is currently an XdgTopLevel with the PlasmaShellSurface used on top. Do not rely on that implementation detail.

## Property Documentation {#property-documentation}

### animated : bool {#animated-prop}

Defines whether the popup is animated on show and close. The default is false.

### \[read-only\] effectivePopupDirection : Qt.Edge {#effectivePopupDirection-prop}

Defines the direction the popup was placed relative to the [visualParent](qml-org-kde-plasma-core-popupplasmawindow.md#visualParent-prop). This property is read-only and is updated when the popup is shown. The value whilst the popup is hidden is undefined.

### floating : bool {#floating-prop}

Defines whether the popup can appear (float) over the parent window. The default is false.

### margin : int {#margin-prop}

If set provides a gap between the parent window and all screen edges

### popupDirection : Qt.Edge {#popupDirection-prop}

Defines the default direction to place the popup relative to the [visualParent](qml-org-kde-plasma-core-popupplasmawindow.md#visualParent-prop).

### removeBorderStrategy : RemoveBorders {#removeBorderStrategy-prop}

Defines which borders should be enabled/disabled when the popup is shown. The default is to show all borders

### visualParent : Item {#visualParent-prop}

The anchor item to place the popup relative to.
