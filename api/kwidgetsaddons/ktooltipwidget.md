---
title: "KToolTipWidget Class"
description: "A tooltip that contains a QWidget."
---

# KToolTipWidget Class

A tooltip that contains a [QWidget](https://doc.qt.io/qt-6/qwidget.html). [More...](#details)

- **Header:** `#include <KToolTipWidget>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](ktooltipwidget-members.md)

## Properties

- [hideDelay : int](#hideDelay-prop)

## Public Functions

- [KToolTipWidget(QWidget \*parent = nullptr)](#KToolTipWidget)
- [int hideDelay() const](#hideDelay)
- [void showAt(const QPoint &pos, QWidget \*content, QWindow \*transientParent)](#showAt)
- [void showBelow(const QRect &rect, QWidget \*content, QWindow \*transientParent)](#showBelow)

## Public Slots

- [void hideLater()](#hideLater)
- [void setHideDelay(int delay)](#setHideDelay)

## Signals

- [void hidden()](#hidden)

## Detailed Description {#details}

This widget allows to show a tooltip that contains another widget.

If you only need to show text inside the tooltip, just use [QWidget::setToolTip](https://doc.qt.io/qt-6/qwidget.html#toolTip-prop)();

To show the tooltip, you need to choose a position on the screen and also pass a transient parent window (recommended on X11 and required on Wayland). Use [showAt](ktooltipwidget.md#showAt)() if you want to show the tooltip from a specific point. Use showUnder() if you want to show it under a given rectangle.

You can use a single instance of this class to show as many tooltips as you want.

The tooltip does not take ownership of the content widget if the latter already has a parent. While the tooltip is set as parent of the widget (by the layout), the old parent is restored when the widget is replaced by another widget and also when the tooltip is deleted.

## Property Documentation {#property-documentation}

### hideDelay : int {#hideDelay-prop}

**Access functions:**

- `int` **[hideDelay](ktooltipwidget.md#hideDelay)**() const
- `void` **[setHideDelay](ktooltipwidget.md#setHideDelay)**(`int` *delay*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KToolTipWidget::KToolTipWidget(QWidget \**parent* = nullptr) {#KToolTipWidget}

### \[signal\] void KToolTipWidget::hidden() {#hidden}

The tooltip has been hidden and the tooltip's widget is no longer visible.

This signal can be used to delete the tooltip's widget.

### int KToolTipWidget::hideDelay() const {#hideDelay}

Returns the delay (in ms) after which [hideLater](ktooltipwidget.md#hideLater)() will hide the tooltip.

Default is 500.

> **Note:** Getter function for property [hideDelay](ktooltipwidget.md#hideDelay-prop).

*See also* [hideLater](ktooltipwidget.md#hideLater)(), [setHideDelay](ktooltipwidget.md#setHideDelay)()

### \[slot\] void KToolTipWidget::hideLater() {#hideLater}

Hide the tooltip after a delay of [hideDelay](ktooltipwidget.md#hideDelay)() ms (to allow interaction with the tooltip's widget).

If [hideDelay](ktooltipwidget.md#hideDelay)() is 0, this is equivalent to [hide](https://doc.qt.io/qt-6/qwidget.html#hide)().

*See also* [hideDelay](ktooltipwidget.md#hideDelay)()

### \[slot\] void KToolTipWidget::setHideDelay(int *delay*) {#setHideDelay}

Set after how many ms [hideLater](ktooltipwidget.md#hideLater)() will hide the tooltip.

> **Note:** Setter function for property [hideDelay](ktooltipwidget.md#hideDelay-prop).

*See also* [hideLater](ktooltipwidget.md#hideLater)(), [hideDelay](ktooltipwidget.md#hideDelay)()

### void KToolTipWidget::showAt(const QPoint &*pos*, QWidget \**content*, QWindow \**transientParent*) {#showAt}

Show a tooltip containing `content`. The [pos](https://doc.qt.io/qt-6/qwidget.html#pos-prop)() of the tooltip will be `pos`.

You can call this method multiple times over the same [KToolTipWidget](ktooltipwidget.md) instance (previously shown widgets will be removed from the tooltip's layout).

`transientParent` will be set as the transient parent of the tooltip.

> **Note:** The transient parent is required to show the tooltip on Wayland platforms.

### void KToolTipWidget::showBelow(const QRect &*rect*, QWidget \**content*, QWindow \**transientParent*) {#showBelow}

Show a tooltip containing `content` centered below `rect`. If there is not enough space in the screen below `rect`, the tooltip will be shown above `rect`, if possible, or at the bottom of the screen otherwise. You can call this method multiple times over the same [KToolTipWidget](ktooltipwidget.md) instance (previously shown widgets will be removed from the tooltip's layout).

Typically `rect` is the visualRect() of a [QAbstractItemView](https://doc.qt.io/qt-6/qabstractitemview.html):

TODO qdoc @snippet ktooltipwidget\_test.cpp show\_tooltip\_widget

`transientParent` will be set as the transient parent of the tooltip.

> **Note:** The transient parent is required to show the tooltip on Wayland platforms.
