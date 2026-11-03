---
title: "ToolBarLayout QML Type"
description: "An item that creates delegates for actions and lays them out in a row."
---

# ToolBarLayout QML Type

An item that creates delegates for actions and lays them out in a row. [More...](#details)

- Import Statement: import org.kde.kirigami.layouts
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

This effectively combines [RowLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-rowlayout.html) and Repeater in a single item, with the addition of some extra performance enhancing tweaks. It will create instances of [fullDelegate](qml-org-kde-kirigami-layouts-toolbarlayout.md#fullDelegate-prop) and itemDelegate for each action in actions. These are then positioned horizontally. Any action that ends up being placed outside the width of the item is hidden and will be part of [hiddenActions](qml-org-kde-kirigami-layouts-toolbarlayout.md#hiddenActions-prop).

The items created as delegates are always created asynchronously, to avoid creation lag spikes. Each delegate has access to the action it was created for through the action attached property.

## Property Documentation {#property-documentation}

### actions : list\<QtObject\> {#actions-prop}

The actions this layout should create delegates for.

### alignment : Qt.Alignment {#alignment-prop}

How to align the delegates within this layout.

When there is more space available than required by the visible delegates, we need to determine how to place the delegates. This property determines how to do that. Note that the [moreButton](qml-org-kde-kirigami-layouts-toolbarlayout.md#moreButton-prop), if visible, will always be placed at the end of the layout.

### fullDelegate : Component {#fullDelegate-prop}

A component that is used to create full-size delegates from.

Each delegate has three states, it can be full-size, icon-only or hidden. By default, the full-size delegate is used. When the action has the [DisplayHint](qml-org-kde-kirigami-layouts-displayhint.md).IconOnly hint set, it will always use the [iconDelegate](qml-org-kde-kirigami-layouts-toolbarlayout.md#iconDelegate-prop). When it has the [DisplayHint](qml-org-kde-kirigami-layouts-displayhint.md).KeepVisible hint set, it will use the full-size delegate when it fits. If not, it will use the [iconDelegate](qml-org-kde-kirigami-layouts-toolbarlayout.md#iconDelegate-prop), unless even that does not fit, in which case it will still be hidden.

### heightMode : enumeration {#heightMode-prop}

How to handle items that do not match the toolbar's height.

When toolbar items do not match the height of the toolbar, there are several ways we can deal with this. This property sets the preferred way.

Available are:

- AlwaysCenter Always center items, allowing them to go outside the bounds of the layout if they are larger
- AlwaysFill Always match the height of the layout. Larger items will be reduced in height, smaller items will be increased
- ConstrainIfLarger If the item is larger than the toolbar, reduce its height. Otherwise center it in the toolbar

The default is HeightMode::ConstrainIfLarger .

### hiddenActions : list\<QtObject\> {#hiddenActions-prop}

A list of actions that do not fit in the current view and are thus hidden.

### iconDelegate : Component {#iconDelegate-prop}

A component that is used to create icon-only delegates from.

*See also* [fullDelegate](qml-org-kde-kirigami-layouts-toolbarlayout.md#fullDelegate-prop)

### layoutDirection : Qt.LayoutDirection {#layoutDirection-prop}

Which direction to layout in.

This is primarily intended to support right-to-left layouts. When set to LeftToRight, delegates will be layout with the first item on the left and following items to the right of that. The more button will be placed at the rightmost position. Alignment flags work normally.

When set to RightToLeft, delegates will be layout with the first item on the right and following items to the left of that. The more button will be placed at the leftmost position. Alignment flags are inverted, so AlignLeft will align items to the right, and vice-versa.

### minimumWidth : real {#minimumWidth-prop}

The minimum width this layout can have.

This is equal to the width of the [moreButton](qml-org-kde-kirigami-layouts-toolbarlayout.md#moreButton-prop).

### moreButton : Component {#moreButton-prop}

A component that is used to create the "more button" item from.

The more button is shown when there are actions that do not fit the current view. It is intended to have functionality to show these hidden actions, like popup a menu with them showing.

### \[since 6.7\] separatorDelegate : Component {#separatorDelegate-prop}

A component that is used to create separator delegates from.

This property was introduced in Qt 6.7.

*See also* [fullDelegate](qml-org-kde-kirigami-layouts-toolbarlayout.md#fullDelegate-prop)

### spacing : real {#spacing-prop}

The amount of spacing between individual delegates.

### visibleWidth : real {#visibleWidth-prop}

The combined width of visible delegates in this layout.

## Attached Property Documentation {#attached-property-documentation}

### ToolBarLayout.action : QtObject {#action-attached-prop}

The action this delegate was created for.

## Method Documentation {#method-documentation}

### void relayout() {#relayout-method}

Queue a relayout of this layout.

> **Note:** The layouting happens during the next scene graph polishing phase.
