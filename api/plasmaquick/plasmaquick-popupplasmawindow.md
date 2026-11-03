---
title: "PlasmaQuick::PopupPlasmaWindow Class"
description: "Styled Plasma window that can be positioned relative to an existing Item on another window."
---

# PlasmaQuick::PopupPlasmaWindow Class

Styled Plasma window that can be positioned relative to an existing Item on another window. [More...](#details)

- **Header:** `#include <PlasmaQuick/PopupPlasmaWindow>`
- **CMake:** `find_package(PlasmaQuick REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Plasma::PlasmaQuick)`
- **Inherits:** [PlasmaQuick::PlasmaWindow](plasmaquick-plasmawindow.md)
- **Inherited By:** [PlasmaQuick::AppletPopup](plasmaquick-appletpopup.md)

[List of all members, including inherited members](plasmaquick-popupplasmawindow-members.md)

## Properties

- [animated : bool](#animated-prop)
- [\[read-only\] effectivePopupDirection : Qt::Edge](#effectivePopupDirection-prop)
- [floating : bool](#floating-prop)
- [margin : int](#margin-prop)
- [popupDirection : Qt::Edge](#popupDirection-prop)
- [removeBorderStrategy : RemoveBorders](#removeBorderStrategy-prop)
- [visualParent : QQuickItem\*](#visualParent-prop)

## Public Functions

- [PopupPlasmaWindow(const QString &svgPrefix = QStringLiteral("dialogs/background"))](#PopupPlasmaWindow)

## Detailed Description {#details}

When shown the popup is placed correctly.

On Wayland this is currently an XdgTopLevel with the PlasmaShellSurface used on top. Do not rely on that implementation detail

## Property Documentation {#property-documentation}

### animated : bool {#animated-prop}

Defines whether the popup is animated on show and close. The default is false.

**Access functions:**

- `bool` **animated**() const
- `void` **setAnimated**(`bool` *animated*)

**Notifier signal:**

- `void` **animatedChanged**()

### \[read-only\] effectivePopupDirection : Qt::Edge {#effectivePopupDirection-prop}

Defines the direction the popup was placed relative to the [visualParent](plasmaquick-popupplasmawindow.md#visualParent-prop). This property is read-only and is updated when the popup is shown. The value whilst the popup is hidden is undefined.

**Access functions:**

- `Qt::Edge` **effectivePopupDirection**() const

**Notifier signal:**

- `void` **effectivePopupDirectionChanged**()

### floating : bool {#floating-prop}

Defines whether the popup can appear (float) over the parent window. The default is false.

**Access functions:**

- `bool` **floating**() const
- `void` **setFloating**(`bool` *floating*)

**Notifier signal:**

- `void` **floatingChanged**()

### margin : int {#margin-prop}

If set provides a gap between the parent window and all screen edges

**Access functions:**

- `int` **margin**() const
- `void` **setMargin**(`int` *margin*)

**Notifier signal:**

- `void` **marginChanged**()

### popupDirection : Qt::Edge {#popupDirection-prop}

Defines the default direction to place the popup relative to the [visualParent](plasmaquick-popupplasmawindow.md#visualParent-prop).

**Access functions:**

- `Qt::Edge` **popupDirection**() const
- `void` **setPopupDirection**(`Qt::Edge` *popupDirection*)

**Notifier signal:**

- `void` **popupDirectionChanged**()

### removeBorderStrategy : RemoveBorders {#removeBorderStrategy-prop}

Defines which borders should be enabled/disabled when the popup is shown. The default is to show all borders

**Access functions:**

- `PlasmaQuick::PopupPlasmaWindow::RemoveBorders` **removeBorderStrategy**() const
- `void` **setRemoveBorderStrategy**(`PlasmaQuick::PopupPlasmaWindow::RemoveBorders` *borders*)

**Notifier signal:**

- `void` **removeBorderStrategyChanged**()

### visualParent : QQuickItem\* {#visualParent-prop}

The anchor item to place the popup relative to.

**Access functions:**

- `QQuickItem` \***visualParent**() const
- `void` **setVisualParent**(`QQuickItem` \**parent*)

**Notifier signal:**

- `void` **visualParentChanged**()

## Member Function Documentation {#member-function-documentation}

### PopupPlasmaWindow::PopupPlasmaWindow(const QString &*svgPrefix* = QStringLiteral("dialogs/background")) {#PopupPlasmaWindow}

Constructor
