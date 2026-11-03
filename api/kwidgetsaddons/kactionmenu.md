---
title: "KActionMenu Class"
description: "A KActionMenu is an action that provides a sub-menu of other actions."
---

# KActionMenu Class

A [KActionMenu](kactionmenu.md) is an action that provides a sub-menu of other actions. [More...](#details)

- **Header:** `#include <KActionMenu>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidgetAction](https://doc.qt.io/qt-6/qwidgetaction.html)

[List of all members, including inherited members](kactionmenu-members.md)

## Properties

- [popupMode : QToolButton::ToolButtonPopupMode](#popupMode-prop)

## Public Functions

- [KActionMenu(QObject \*parent)](#KActionMenu)
- [KActionMenu(const QString &text, QObject \*parent)](#KActionMenu-1)
- [KActionMenu(const QIcon &icon, const QString &text, QObject \*parent)](#KActionMenu-2)
- [void addAction(QAction \*action)](#addAction)
- [QAction \*addSeparator()](#addSeparator)
- [void insertAction(QAction \*before, QAction \*action)](#insertAction)
- [QAction \*insertSeparator(QAction \*before)](#insertSeparator)
- [QToolButton::ToolButtonPopupMode popupMode() const](#popupMode)
- [void removeAction(QAction \*action)](#removeAction)
- [void setPopupMode(QToolButton::ToolButtonPopupMode popupMode)](#setPopupMode)

## Detailed Description {#details}

Plugged in a popupmenu, it will create a submenu.

Plugged in a toolbar, it will create a button with a popup menu.

This is the action used by the XMLGUI since it holds other actions.

If you want a submenu for selecting one tool among many (without icons), see [KSelectAction](kselectaction.md).

## Property Documentation {#property-documentation}

### popupMode : QToolButton::ToolButtonPopupMode {#popupMode-prop}

**Access functions:**

- `QToolButton::ToolButtonPopupMode` **[popupMode](kactionmenu.md#popupMode)**() const
- `void` **[setPopupMode](kactionmenu.md#setPopupMode)**(`QToolButton::ToolButtonPopupMode` *popupMode*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KActionMenu::KActionMenu(QObject \**parent*) {#KActionMenu}

### KActionMenu::KActionMenu(const QString &*text*, QObject \**parent*) {#KActionMenu-1}

### KActionMenu::KActionMenu(const QIcon &*icon*, const QString &*text*, QObject \**parent*) {#KActionMenu-2}

### void KActionMenu::addAction(QAction \**action*) {#addAction}

Adds `action` to this [KActionMenu](kactionmenu.md). The [KActionMenu](kactionmenu.md) does not take ownership of `action`.

### QAction \*KActionMenu::addSeparator() {#addSeparator}

### void KActionMenu::insertAction(QAction \**before*, QAction \**action*) {#insertAction}

### QAction \*KActionMenu::insertSeparator(QAction \**before*) {#insertSeparator}

### QToolButton::ToolButtonPopupMode KActionMenu::popupMode() const {#popupMode}

The currently used popup mode when plugged in a KToolBar.

> **Note:** Getter function for property [popupMode](kactionmenu.md#popupMode-prop).

*See also* [setPopupMode](kactionmenu.md#setPopupMode)()

### void KActionMenu::removeAction(QAction \**action*) {#removeAction}

### void KActionMenu::setPopupMode(QToolButton::ToolButtonPopupMode *popupMode*) {#setPopupMode}

Determines the popup mode when plugged in a KToolBar.

Options are:

- [QToolButton::InstantPopup](https://doc.qt.io/qt-6/qtoolbutton.html#ToolButtonPopupMode-enum) Clicking anywhere on the toolbar button opens the popup menu.
- [QToolButton::DelayedPopup](https://doc.qt.io/qt-6/qtoolbutton.html#ToolButtonPopupMode-enum) (Default) Clicking anywhere on the toolbar button triggers the default action. Clicking and holding the toolbar button opens the popup menu instead.
- [QToolButton::MenuButtonPopup](https://doc.qt.io/qt-6/qtoolbutton.html#ToolButtonPopupMode-enum) The toolbar button is split in a main button (triggers default action) and an arrow button (opens the popup menu).

> **Note:** Setter function for property [popupMode](kactionmenu.md#popupMode-prop).

*See also* [popupMode](kactionmenu.md#popupMode)(), [QToolButton](https://doc.qt.io/qt-6/qtoolbutton.html)
