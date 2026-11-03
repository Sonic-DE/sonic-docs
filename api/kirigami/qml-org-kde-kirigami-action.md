---
title: "Action QML Type"
description: "An item that represents an abstract Action."
---

# Action QML Type

An item that represents an abstract Action. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [Action](https://doc.qt.io/qt-6/qml-qtquick-controls-action.html)
- Inherited By: [PagePoolAction](qml-org-kde-kirigami-pagepoolaction.md)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### autoExclusive : bool {#autoExclusive-prop}

This property holds whether auto-exclusivity is enabled.

If auto-exclusivity is enabled, checkable actions that belong to the same parent item behave as if they were part of the same [ButtonGroup](https://doc.qt.io/qt-6/qml-qtquick-controls-buttongroup.html). Only one action can be checked at any time; checking another action automatically unchecks the previously checked one.

default: `false`

### \[default\] children : list\<Action\> {#children-prop}

This property holds a list of child actions.

This is useful for tree-like menus, such as the [GlobalDrawer](qml-org-kde-kirigami-globaldrawer.md).

Example usage:

```cpp
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami

Kirigami.Action {
   text: "Tools"

   QQC2.Action {
       text: "Action1"
   }
   Kirigami.Action {
       text: "Action2"
   }
}
```

### displayComponent : Component {#displayComponent-prop}

This property holds the component that should be used for displaying this action.

> **Note:** This can be used to display custom components in the toolbar.

### displayHint : enumeration {#displayHint-prop}

This property sets this action's display type.

These are provided to implementations to indicate a preference for certain display styles.

default: `Kirigami.DisplayHint.NoPreference`

> **Note:** This property contains only preferences, implementations may choose to disregard them.

*See also* [DisplayHint](qml-org-kde-kirigami-layouts-displayhint.md)

### expandible : bool {#expandible-prop}

This property sets whether this action becomes a title displaying its child actions as sub-items in GlobalDrawers and ContextDrawers.

default: `false`

### \[since Kirigami 6.4\] fromQAction : QtObject {#fromQAction-prop}

This property holds a QAction.

When provided Kirigami.Action will be initialized from the given QAction.

This property was introduced in Kirigami 6.4.

### parent : Action {#parent-prop}

This property holds the parent action.

### separator : bool {#separator-prop}

This property sets whether this action is a separator action.

default: `false`

### tooltip : string {#tooltip-prop}

This property holds the tooltip text that is shown when the cursor is hovering over the control.

Leaving this undefined or setting it to an empty string means that no tooltip will be shown when the cursor is hovering over the control that triggers the tooltip.

> **Warning:** Tooltips may not be supported on all platforms.

### visible : bool {#visible-prop}

This property holds whether the graphic representation of the action is supposed to be visible.

It's up to the action representation to honor this property.

default: `true`

### \[read-only\] visibleChildren : list\<Action\> {#visibleChildren-prop}

This property holds the action's visible child actions.
