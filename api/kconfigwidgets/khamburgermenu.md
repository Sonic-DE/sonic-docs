---
title: "KHamburgerMenu Class"
description: "A menu that substitutes a menu bar when necessary."
---

# KHamburgerMenu Class

A menu that substitutes a menu bar when necessary. [More...](#details)

- **Header:** `#include <KHamburgerMenu>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ConfigWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigWidgets)`
- **Inherits:** [QWidgetAction](https://doc.qt.io/qt-6/qwidgetaction.html)

[List of all members, including inherited members](khamburgermenu-members.md)

## Public Functions

- [KHamburgerMenu(QObject \*parent)](#KHamburgerMenu)
- [void addToMenu(QMenu \*menu)](#addToMenu)
- [void hideActionsOf(QWidget \*widget)](#hideActionsOf)
- [void insertIntoMenuBefore(QMenu \*menu, QAction \*before)](#insertIntoMenuBefore)
- [QMenuBar \*menuBar() const](#menuBar)
- [bool menuBarAdvertised() const](#menuBarAdvertised)
- [void setMenuBar(QMenuBar \*menuBar)](#setMenuBar)
- [void setMenuBarAdvertised(bool advertise)](#setMenuBarAdvertised)
- [void setShowMenuBarAction(QAction \*showMenuBarAction)](#setShowMenuBarAction)
- [void showActionsOf(QWidget \*widget)](#showActionsOf)

## Signals

- [void aboutToShowMenu()](#aboutToShowMenu)

## Protected Functions

- [QWidget \*createWidget(QWidget \*parent)](#createWidget)

## Detailed Description {#details}

Allowing users to toggle the visibility of the menu bar and/or toolbars, while pretty/"simple by default", can lead to various grave usability issues. This class makes it easy to prevent all of them.

Simply add a [KHamburgerMenu](khamburgermenu.md) to your UI (typically to a [QToolBar](https://doc.qt.io/qt-6/qtoolbar.html)) and make it aware of a [QMenuBar](https://doc.qt.io/qt-6/qmenubar.html) like this:

```cpp
auto hamburgerMenu = KStandardAction::hamburgerMenu(nullptr, nullptr, actionCollection());
toolBar()->addAction(hamburgerMenu);
hamburgerMenu->hideActionsOf(toolBar());
// after the QMenuBar has been initialised
hamburgerMenu->setMenuBar(menuBar()); // line not needed if there is no QMenuBar
```

The added menu button will only be visible when the [QMenuBar](https://doc.qt.io/qt-6/qmenubar.html) is hidden. With this minimal initialisation it will contain the contents of the menu bar. If a user (also) hides the container the [KHamburgerMenu](khamburgermenu.md) was added to they might find themselves without a way to get a menu back. To prevent this, it is recommended to add the hamburgerMenu to prominent context menus like the one of your central widget preferably at the first position. Simply write:

```cpp
hamburgerMenu->addActionToMenu(contextMenu);
```

The added menu will only be visible if the [QMenuBar](https://doc.qt.io/qt-6/qmenubar.html) is hidden and the hamburgerMenu-\>[createdWidgets](https://doc.qt.io/qt-6/qwidgetaction.html#createdWidgets)() are all invisible to the user.

### Populating the KHamburgerMenu {#populating-the-khamburgermenu}

This is easy:

```cpp
auto menu = new QMenu(this);
menu->addAction(action);
// Add actions, separators, etc. like usual.
hamburgerMenu->setMenu(menu);
```

You probably do not want this to happen on startup. Therefore [KHamburgerMenu](khamburgermenu.md) provides the signal [aboutToShowMenu](khamburgermenu.md#aboutToShowMenu) that you can connect to a function containing the previous statements.

```cpp
connect(hamburgerMenu, &KHamburgerMenu::aboutToShowMenu,
        this, &MainWindow::updateHamburgerMenu);
// You might want to disconnect the signal after initial creation if the contents never change.
```

### Deciding what to put on the hamburger menu {#deciding-what-to-put-on-the-hamburger-menu}

1. Be sure to add all of the most important actions. Actions which are already visible on QToolBars, etc. will not show up in the hamburgerMenu. To manage which containers [KHamburgerMenu](khamburgermenu.md) should watch for redundancy use [hideActionsOf](khamburgermenu.md#hideActionsOf)([QWidget](https://doc.qt.io/qt-6/qwidget.html) \*) and [showActionsOf](khamburgermenu.md#showActionsOf)([QWidget](https://doc.qt.io/qt-6/qwidget.html) \*). When a [KHamburgerMenu](khamburgermenu.md) is added to a widget, [hideActionsOf](khamburgermenu.md#hideActionsOf)(that widget) will automatically be called.

2. Do not worry about adding all actions the application has to offer. The [KHamburgerMenu](khamburgermenu.md) will automatically have a section advertising excluded actions which can be found in the [QMenuBar](https://doc.qt.io/qt-6/qmenubar.html). There will also be the showMenuBarAction if you set it with [setShowMenuBarAction](khamburgermenu.md#setShowMenuBarAction)().

3. Do not worry about the help menu. [KHamburgerMenu](khamburgermenu.md) will automatically contain a help menu as the second to last item (if you set a [QMenuBar](https://doc.qt.io/qt-6/qmenubar.html) which is expected to have the help menu as the last action).

### Open menu by shortcut {#open-menu-by-shortcut}

For visually impaired users it is important to have a consistent way to open a general-purpose menu. Triggering the keyboard shortcut bound to [KHamburgerMenu](khamburgermenu.md) will always open a menu.

- If [setMenuBar](khamburgermenu.md#setMenuBar)() was called and that menu bar is visible, the shortcut will open the first menu of that menu bar.
- Otherwise, if there is a visible [KHamburgerMenu](khamburgermenu.md) button in the user interface, that menu will open.
- Otherwise, [KHamburgerMenu](khamburgermenu.md)'s menu will open at the mouse cursor position.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KHamburgerMenu::KHamburgerMenu(QObject \**parent*) {#KHamburgerMenu}

### \[signal\] void KHamburgerMenu::aboutToShowMenu() {#aboutToShowMenu}

This signal is emitted when a hamburger menu button is about to be pressed down. It is also emitted when a [QMenu](https://doc.qt.io/qt-6/qmenu.html) that contains a visible [KHamburgerMenu](khamburgermenu.md) emits [QMenu::aboutToShow](https://doc.qt.io/qt-6/qmenu.html#aboutToShow).

### void KHamburgerMenu::addToMenu(QMenu \**menu*) {#addToMenu}

Adds this [KHamburgerMenu](khamburgermenu.md) to `menu`. It will only be visible in the menu if both the menu bar and all of this [QWidgetAction](https://doc.qt.io/qt-6/qwidgetaction.html)'s [createdWidgets](https://doc.qt.io/qt-6/qwidgetaction.html#createdWidgets)() are invisible. If it is visible in the menu, then opening the menu emits the [aboutToShowMenu](khamburgermenu.md#aboutToShowMenu) signal.

`menu` The menu this [KHamburgerMenu](khamburgermenu.md) is supposed to appear in.

### \[override virtual protected\] QWidget \*KHamburgerMenu::createWidget(QWidget \**parent*) {#createWidget}

Reimplements: [QWidgetAction::createWidget(QWidget \*parent)](https://doc.qt.io/qt-6/qwidgetaction.html#createWidget).

`QWidgetAction::createWidget`

### void KHamburgerMenu::hideActionsOf(QWidget \**widget*) {#hideActionsOf}

Adds `widget` to a list of widgets that should be monitored for their [actions()](https://doc.qt.io/qt-6/qmenu.html#actions). If the widget is a [QMenu](https://doc.qt.io/qt-6/qmenu.html), its actions will be treated as known to the user. If the widget isn't a [QMenu](https://doc.qt.io/qt-6/qmenu.html), its actions will only be treated as known to the user when the widget is actually visible. `widget` A widget that contains actions which should not show up in the [KHamburgerMenu](khamburgermenu.md) redundantly.

### void KHamburgerMenu::insertIntoMenuBefore(QMenu \**menu*, QAction \**before*) {#insertIntoMenuBefore}

Inserts this [KHamburgerMenu](khamburgermenu.md) to `menu`'s list of actions, before the action `before`. It will only be visible in the menu if both the menu bar and all of this [QWidgetAction](https://doc.qt.io/qt-6/qwidgetaction.html)'s [createdWidgets](https://doc.qt.io/qt-6/qwidgetaction.html#createdWidgets)() are invisible. If it is visible in the menu, then opening the menu emits the [aboutToShowMenu](khamburgermenu.md#aboutToShowMenu) signal.

`before` The action before which [KHamburgerMenu](khamburgermenu.md) should be inserted.

`menu` The menu this [KHamburgerMenu](khamburgermenu.md) is supposed to appear in.

`QWidget::insertAction()`, [QMenu::insertMenu](https://doc.qt.io/qt-6/qmenu.html#insertMenu)()

### QMenuBar \*KHamburgerMenu::menuBar() const {#menuBar}

*See also* [setMenuBar](khamburgermenu.md#setMenuBar)()

### bool KHamburgerMenu::menuBarAdvertised() const {#menuBarAdvertised}

`setMenuBarAdvertised()`

*See also* [setMenuBarAdvertised](khamburgermenu.md#setMenuBarAdvertised)()

### void KHamburgerMenu::setMenuBar(QMenuBar \**menuBar*) {#setMenuBar}

Associates this [KHamburgerMenu](khamburgermenu.md) with `menuBar`. The [KHamburgerMenu](khamburgermenu.md) will from now on only be visible when `menuBar` is hidden. (Menu bars with [QMenuBar::isNativeMenuBar](https://doc.qt.io/qt-6/qmenubar.html#nativeMenuBar-prop)() == true are considered hidden.)

Furthermore the [KHamburgerMenu](khamburgermenu.md) will have the help menu from the `menuBar` added at the end. There will also be a special sub-menu advertising actions which are only available in the menu bar unless advertiseMenuBar(false) was called.

`menuBar` The [QMenuBar](https://doc.qt.io/qt-6/qmenubar.html) the [KHamburgerMenu](khamburgermenu.md) should be associated with. This can be set to nullptr.

*See also* [menuBar](khamburgermenu.md#menuBar)()

### void KHamburgerMenu::setMenuBarAdvertised(bool *advertise*) {#setMenuBarAdvertised}

By default the [KHamburgerMenu](khamburgermenu.md) contains a special sub-menu that advertises actions of the menu bar which would otherwise not be visible or discoverable for the user. This method removes or re-adds that sub-menu.

`advertise` sets whether the special sub-menu that advertises menu bar only actions should exist.

*See also* [menuBarAdvertised](khamburgermenu.md#menuBarAdvertised)()

### void KHamburgerMenu::setShowMenuBarAction(QAction \**showMenuBarAction*) {#setShowMenuBarAction}

Adds the `showMenuBarAction` as the first item of the sub-menu which advertises actions from the menu bar. `setMenuBarAdvertised()`

### void KHamburgerMenu::showActionsOf(QWidget \**widget*) {#showActionsOf}

Reverses a [hideActionsOf](khamburgermenu.md#hideActionsOf)(widget) method call.

`hideActionsOf()`
