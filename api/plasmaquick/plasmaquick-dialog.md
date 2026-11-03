---
title: "PlasmaQuick::Dialog Class"
description: "Creates a Plasma themed top level window that can contain any QML component."
---

# PlasmaQuick::Dialog Class

Creates a Plasma themed top level window that can contain any QML component. [More...](#details)

- **Header:** `#include <PlasmaQuick::Dialog>`
- **CMake:** `find_package(PlasmaQuick REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Plasma::PlasmaQuick)`
- **Inherits:** [QQuickWindow](https://doc.qt.io/qt-6/qquickwindow.html) and

[List of all members, including inherited members](plasmaquick-dialog-members.md)

## Properties

- [appletInterface : QQuickItem\*](#appletInterface-prop)
- [backgroundHints : BackgroundHints](#backgroundHints-prop)
- [flags : Qt::WindowFlags](#flags-prop)
- [floating : int](#floating-prop)
- [hideOnWindowDeactivate : bool](#hideOnWindowDeactivate-prop)
- [\[read-only\] inset : QObject\* const](#inset-prop)
- [location : Plasma::Types::Location](#location-prop)
- [mainItem : QQuickItem\*](#mainItem-prop)
- [\[read-only\] margins : QObject\* const](#margins-prop)
- [outputOnly : bool](#outputOnly-prop)
- [type : WindowType](#type-prop)
- [visible : bool](#visible-prop)
- [visualParent : QQuickItem\*](#visualParent-prop)

## Public Functions

- [QPoint popupPosition(QQuickItem \*item, const QSize &size)](#popupPosition)

## Signals

- [void windowDeactivated()](#windowDeactivated)

## Protected Functions

- [void adjustGeometry(const QRect &geom)](#adjustGeometry)

## Detailed Description {#details}

It can be automatically positioned relative to a visual parent The dialog will resize to the size of the main item

## Property Documentation {#property-documentation}

### appletInterface : QQuickItem\* {#appletInterface-prop}

This property holds a pointer to the AppletInterface used by an applet. It is null when the dialog is not used for an applet.

**Access functions:**

- `QQuickItem` \***appletInterface**() const
- `void` **setAppletInterface**(`QQuickItem` \**appletInterface*)

**Notifier signal:**

- `void` **appletInterfaceChanged**()

### backgroundHints : BackgroundHints {#backgroundHints-prop}

This property holds how (and if at all) the dialog should draw its own background or if it is complete responsibility of the content item to render a background. Note that in case of NoBackground it loses kwin side shadows and blur

**Access functions:**

- `PlasmaQuick::Dialog::BackgroundHints` **backgroundHints**() const
- `void` **setBackgroundHints**(`PlasmaQuick::Dialog::BackgroundHints` *hints*)

**Notifier signal:**

- `void` **backgroundHintsChanged**()

### flags : Qt::WindowFlags {#flags-prop}

This property holds the window flags of the window. The window flags control the window's appearance in the windowing system, whether it's a dialog, popup, or a regular window, and whether it should have a title bar, etc. Regardless to what the user sets, the flags will always have the FramelessWindowHint flag set

**Access functions:**

- `void` **setFramelessFlags**(`Qt::WindowFlags` *flags*)

**Notifier signal:**

- `void` **flagsChanged**()

### floating : int {#floating-prop}

This property holds by how much the applet should be floating even if the location is set to a certain screen side; if this value is positive, the dialog will draw all four sides and maintain the required distance from the screen borders.

**Access functions:**

- `int` **floating**() const
- `void` **setFloating**(`int` *floating*)

**Notifier signal:**

- `void` **floatingChanged**()

### hideOnWindowDeactivate : bool {#hideOnWindowDeactivate-prop}

Whether the dialog should be hidden when the dialog loses focus.

The default value is `false`.

**Access functions:**

- `bool` **hideOnWindowDeactivate**() const
- `void` **setHideOnWindowDeactivate**(`bool` *hide*)

**Notifier signal:**

- `void` **hideOnWindowDeactivateChanged**()

### \[read-only\] inset : QObject\* const {#inset-prop}

Margins where the dialog background actually starts, excluiding things like shadows or borders

**Access functions:**

- `QObject` \***inset**() const

*See also* DialogMargins

### location : Plasma::Types::Location {#location-prop}

Plasma Location of the dialog window.

Useful if this dialog is a popup for a panel.

**Access functions:**

- `Plasma::Types::Location` **location**() const
- `void` **setLocation**(`Plasma::Types::Location` *location*)

**Notifier signal:**

- `void` **locationChanged**()

### mainItem : QQuickItem\* {#mainItem-prop}

The main QML item that will be displayed in the Dialog

**Access functions:**

- `QQuickItem` \***mainItem**() const
- `void` **setMainItem**(`QQuickItem` \**mainItem*)

**Notifier signal:**

- `void` **mainItemChanged**()

### \[read-only\] margins : QObject\* const {#margins-prop}

Margins of the dialog around the [mainItem](plasmaquick-dialog.md#mainItem-prop).

**Access functions:**

- `QObject` \***margins**() const

*See also* DialogMargins

### outputOnly : bool {#outputOnly-prop}

Whether the dialog is output only. Default value is `false`. If it is `true` the dialog does not accept input and all pointer events are not accepted, thus the dialog is click through.

This property is currently only supported on the X11 platform. On any other platform the property has no effect.

**Access functions:**

- `bool` **isOutputOnly**() const
- `void` **setOutputOnly**(`bool` *outputOnly*)

**Notifier signal:**

- `void` **outputOnlyChanged**()

### type : WindowType {#type-prop}

Type of the window

**Access functions:**

- `PlasmaQuick::Dialog::WindowType` **type**() const
- `void` **setType**(`PlasmaQuick::Dialog::WindowType` *type*)

**Notifier signal:**

- `void` **typeChanged**()

### visible : bool {#visible-prop}

**Access functions:**

- `bool` **isVisible**() const
- `void` **setVisible**(`bool` *visible*)

**Notifier signal:**

- `void` **visibleChangedProxy**()

### visualParent : QQuickItem\* {#visualParent-prop}

The main QML item that will be displayed in the Dialog

**Access functions:**

- `QQuickItem` \***visualParent**() const
- `void` **setVisualParent**(`QQuickItem` \**visualParent*)

**Notifier signal:**

- `void` **visualParentChanged**()

## Member Function Documentation {#member-function-documentation}

### \[virtual protected\] void Dialog::adjustGeometry(const QRect &*geom*) {#adjustGeometry}

Sets the dialog position.

Subclasses may change it. [ToolTipDialog](../plasmacore/tooltipdialog.md) adjusts the position in an animated way.

### \[virtual\] QPoint Dialog::popupPosition(QQuickItem \**item*, const QSize &*size*) {#popupPosition}

Returns the suggested screen position for the popup.

`item` The item the popup has to be positioned relatively to. If null, the popup will be positioned in the center of the window.

`size` The size that the popup will have, which influences the final position.

### \[signal\] void Dialog::windowDeactivated() {#windowDeactivated}

Emitted when the [hideOnWindowDeactivate](plasmaquick-dialog.md#hideOnWindowDeactivate-prop) property is `true` and this dialog lost focus to a window that is neither a parent dialog to nor a child dialog of this dialog.
