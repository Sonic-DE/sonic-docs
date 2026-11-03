---
title: "ActionToolBar QML Type"
description: "A toolbar built from a list of actions."
---

# ActionToolBar QML Type

A toolbar built from a list of actions. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [Control](https://doc.qt.io/qt-6/qml-qtquick-controls-control.html)

## Detailed Description {#details}

Creates a toolbar out of a list of [actions](qml-org-kde-kirigami-actiontoolbar.md#actions-prop). Each item is a [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html).Controls.[ToolButton](https://doc.qt.io/qt-6/qml-qtquick-controls-toolbutton.html) by default, but this can be overridden by setting the Action.displayComponent property on that item's Action.

The default behavior of [ActionToolBar](qml-org-kde-kirigami-actiontoolbar.md) is to display as many items as possible, placing the ones that don't fit into an overflow menu. You can control this behavior by setting the displayHint property on an item's Action. For example, when setting the [DisplayHint](qml-org-kde-kirigami-layouts-displayhint.md).KeepVisible display hint, [ActionToolBar](qml-org-kde-kirigami-actiontoolbar.md) will try to keep that action's item in view as long as possible, transforming it into an icon-only button if a button with an icon and text doesn't fit.

## Property Documentation {#property-documentation}

### \[read-only\] actions : Action {#actions-prop}

This property holds a list of visible actions.

The [ActionToolBar](qml-org-kde-kirigami-actiontoolbar.md) will try to display as many actions as possible. The ones that don't fit will go into an overflow menu.

### alignment : Qt::Alignment {#alignment-prop}

This property holds the alignment of the buttons.

When there is more space available than required by the visible delegates, we need to determine how to place the delegates.

When there is more space available than required by the visible action delegates, we need to determine where to position them.

default: `Qt.AlignLeft`

*See also* [Qt::AlignmentFlag](https://doc.qt.io/qt-6/qt.html#AlignmentFlag-enum)

### display : int {#display-prop}

This property determines how the icon and text are displayed within the button.

Permitted values are:

- Button.IconOnly
- Button.TextOnly
- Button.TextBesideIcon
- Button.TextUnderIcon

default: `Controls.Button.TextBesideIcon`

*See also* [AbstractButton](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html)

### flat : bool {#flat-prop}

This property holds whether the buttons will have a flat/[ToolButton](https://doc.qt.io/qt-6/qml-qtquick-controls-toolbutton.html) style appearance.

default: `true`

### heightMode : enumeration {#heightMode-prop}

This property determines how to handle items that do not match the [ActionToolBar](qml-org-kde-kirigami-actiontoolbar.md)'s height.

Permitted values are:

- HeightMode.AlwaysCenter
- HeightMode.AlwaysFill
- HeightMode.ConstrainIfLarger

default: `HeightMode::ConstrainIfLarger`

### \[read-only\] maximumContentWidth : int {#maximumContentWidth-prop}

This property holds the maximum width of the content.

If the [ActionToolBar](qml-org-kde-kirigami-actiontoolbar.md)'s width is larger than this value, empty space will be added on the sides, according to the Alignment property.

The value of this property is derived from the [ActionToolBar](qml-org-kde-kirigami-actiontoolbar.md)'s actions and their properties.

### overflowIconName : string {#overflowIconName-prop}

This property holds the name of the icon to use for the overflow menu button.

default: `overflow-menu`

### position : int {#position-prop}

This property holds the position of the toolbar.

If this [ActionToolBar](qml-org-kde-kirigami-actiontoolbar.md) is the contentItem of a QQC2 [ToolBar](https://doc.qt.io/qt-6/qml-qtquick-controls-toolbar.html), the position is automatically bound to the [ToolBar](https://doc.qt.io/qt-6/qml-qtquick-controls-toolbar.html)'s position.

Permitted values are:

- [ToolBar](https://doc.qt.io/qt-6/qml-qtquick-controls-toolbar.html).Header: The toolbar is at the top, as a window or page header.
- [ToolBar](https://doc.qt.io/qt-6/qml-qtquick-controls-toolbar.html).Footer: The toolbar is at the bottom, as a window or page footer.

default: `QQC2.ToolBar.Header`

### \[read-only\] visibleWidth : int {#visibleWidth-prop}

This property holds the combined width of all visible delegates.
