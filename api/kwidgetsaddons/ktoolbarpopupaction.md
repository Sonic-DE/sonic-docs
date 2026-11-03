---
title: "KToolBarPopupAction Class"
description: "This action is a normal action everywhere, except in a toolbar where it also has a popupmenu (optionally delayed)."
---

# KToolBarPopupAction Class

This action is a normal action everywhere, except in a toolbar where it also has a popupmenu (optionally delayed). [More...](#details)

- **Header:** `#include <KToolBarPopupAction>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidgetAction](https://doc.qt.io/qt-6/qwidgetaction.html)

[List of all members, including inherited members](ktoolbarpopupaction-members.md)

## Public Types

- [\[since 6.0\] enum KToolBarPopupAction::PopupMode](#PopupMode-enum)

## Properties

- [popupMode : PopupMode](#popupMode-prop)

## Public Functions

- [KToolBarPopupAction(const QIcon &icon, const QString &text, QObject \*parent)](#KToolBarPopupAction)
- [QMenu \*popupMenu() const](#popupMenu) (since 6.0)
- [KToolBarPopupAction::PopupMode popupMode() const](#popupMode) (since 6.0)
- [void setPopupMode(KToolBarPopupAction::PopupMode popupMode)](#setPopupMode) (since 6.0)

## Detailed Description {#details}

This action is designed for history actions (back/forward, undo/redo) and for any other action that has more detail in a toolbar than in a menu (e.g. tool chooser with "Other" leading to a dialog...).

In contrast to [KActionMenu](kactionmenu.md), this action is a *simple* menuitem when plugged into a menu, and has a popup only in a toolbar.

Use cases include Back/Forward, and Undo/Redo. Simple click is what's most commonly used, and enough for menus, but in toolbars there is *also* an optional popup to go back N steps or undo N steps.

> **Note:** Add actions to the [popupMenu](ktoolbarpopupaction.md#popupMenu)(), don't use [setMenu](https://doc.qt.io/qt-6/qaction.html#setMenu)().

## Member Type Documentation {#member-type-documentation}

### \[since 6.0\] enum KToolBarPopupAction::PopupMode {#PopupMode-enum}

The menu popup mode.

Default is MenuButtonPopup.

| Constant | Value | Description |
| --- | --- | --- |
| `KToolBarPopupAction::NoPopup` | `-1` | Behave as if the button had no menu. |
| `KToolBarPopupAction::DelayedPopup` | `QToolButton::DelayedPopup` | Clicking anywhere on the toolbar button triggers the default action. Clicking and holding the toolbar button opens the popup menu instead. |
| `KToolBarPopupAction::MenuButtonPopup` | `QToolButton::MenuButtonPopup` | The toolbar button is split in a main button (triggers default action) and an arrow button (opens the popup menu). |
| `KToolBarPopupAction::InstantPopup` | `QToolButton::InstantPopup` | Clicking anywhere on the toolbar button opens the popup menu. |

This enum was introduced in Qt 6.0.

*See also* [QToolButton::ToolButtonPopupMode](https://doc.qt.io/qt-6/qtoolbutton.html#ToolButtonPopupMode-enum)

## Property Documentation {#property-documentation}

### popupMode : PopupMode {#popupMode-prop}

**Access functions:**

- `KToolBarPopupAction::PopupMode` **[popupMode](ktoolbarpopupaction.md#popupMode)**() const
- `void` **[setPopupMode](ktoolbarpopupaction.md#setPopupMode)**(`KToolBarPopupAction::PopupMode` *popupMode*)

## Member Function Documentation {#member-function-documentation}

### KToolBarPopupAction::KToolBarPopupAction(const QIcon &*icon*, const QString &*text*, QObject \**parent*) {#KToolBarPopupAction}

Create a [KToolBarPopupAction](ktoolbarpopupaction.md), with a text, an icon, a parent and a name.

`icon` The icon to display.

`text` The text that will be displayed.

`parent` This action's parent.

### \[since 6.0\] QMenu \*KToolBarPopupAction::popupMenu() const {#popupMenu}

The popup menu that is shown when clicking (some time) on the toolbar button. You may want to plug items into it on creation, or connect to aboutToShow for a more dynamic menu.

> **Note:** [menu](https://doc.qt.io/qt-6/qaction.html#menu)() is null on this action by default and using [setMenu](https://doc.qt.io/qt-6/qaction.html#setMenu)() will effectively turn this action into a regular action with a submenu.

This function was introduced in Qt 6.0.

### \[since 6.0\] KToolBarPopupAction::PopupMode KToolBarPopupAction::popupMode() const {#popupMode}

The popup mode of the toolbar button.

> **Note:** Getter function for property [popupMode](ktoolbarpopupaction.md#popupMode-prop).

This function was introduced in Qt 6.0.

*See also* [setPopupMode](ktoolbarpopupaction.md#setPopupMode)()

### \[since 6.0\] void KToolBarPopupAction::setPopupMode(KToolBarPopupAction::PopupMode *popupMode*) {#setPopupMode}

Determines the popup mode of the toolbar button.

> **Note:** Setter function for property [popupMode](ktoolbarpopupaction.md#popupMode-prop).

This function was introduced in Qt 6.0.

*See also* [popupMode](ktoolbarpopupaction.md#popupMode)(), [PopupMode](ktoolbarpopupaction.md#PopupMode-enum)
