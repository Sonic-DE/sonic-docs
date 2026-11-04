---
title: "QMenuProxy Class"
description: "Plasma Extras QML Module."
---

# QMenuProxy Class

Plasma Extras QML Module. [More...](#details)

- **Header:** `#include <QMenuProxy>`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](qmenuproxy-members.md)

## Public Types

- [enum QMenuProxy::PopupPlacement](#PopupPlacement-enum)

## Public Functions

- [void addMenuItem(const QString &text)](#addMenuItem)
- [void addMenuItem(QMenuItem \*item, QMenuItem \*before = nullptr)](#addMenuItem-1)
- [void addSection(const QString &text)](#addSection)
- [void clearMenuItems()](#clearMenuItems)
- [void close()](#close)
- [void open(int x = 0, int y = 0)](#open)
- [void openRelative()](#openRelative)
- [void removeMenuItem(QMenuItem \*item)](#removeMenuItem)

## Detailed Description {#details}

@class Menu

An Item provides a menu for use in context specific situations. You can specify the position for the menu to open by setting its visualParent. MenuItems should be used to draw entries in the menu. The [open](qmenuproxy.md#open)() function opens up the menu at the given visualParent.

Example usage: @code import org.kde.plasma.extras 2.0 as [PlasmaExtras](plasmaextras-module.md)

\[...\] [PlasmaExtras](plasmaextras-module.md).Menu { id: menu ... [PlasmaExtras](plasmaextras-module.md).[MenuItem](https://doc.qt.io/qt-6/qml-qtquick-controls-menuitem.html) { text: "Delete" onClicked: { myListItem.remove(); } } } [PlasmaExtras](plasmaextras-module.md).Button { id: btn onClicked: { menu.visualParent = btn menu.[open](qmenuproxy.md#open)() } } \[...\] @endcode

## Member Type Documentation {#member-type-documentation}

### enum QMenuProxy::PopupPlacement {#PopupPlacement-enum}

The popup position enumeration relatively to his attached widget

## Member Function Documentation {#member-function-documentation}

### \[invokable\] void QMenuProxy::addMenuItem(const QString &*text*) {#addMenuItem}

This adds a menu item from a String

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void QMenuProxy::addMenuItem(QMenuItem \**item*, QMenuItem \**before* = nullptr) {#addMenuItem-1}

This adds [MenuItem](https://doc.qt.io/qt-6/qml-qtquick-controls-menuitem.html) 'item' to the menu before [MenuItem](https://doc.qt.io/qt-6/qml-qtquick-controls-menuitem.html) 'before'. If [MenuItem](https://doc.qt.io/qt-6/qml-qtquick-controls-menuitem.html) 'before' is 0 or does not exist in the menu, 'item' is appended to the menu instead. If [MenuItem](https://doc.qt.io/qt-6/qml-qtquick-controls-menuitem.html) 'item' already exists in the menu, it is removed and inserted at the new position.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void QMenuProxy::addSection(const QString &*text*) {#addSection}

This adds a section header with a string used as name for the section

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void QMenuProxy::clearMenuItems() {#clearMenuItems}

This removes all menuItems inside the menu

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void QMenuProxy::close() {#close}

This closes the menu

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void QMenuProxy::open(int *x* = 0, int *y* = 0) {#open}

This opens the menu at position x,y on the given visualParent. By default x and y are set to 0

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void QMenuProxy::openRelative() {#openRelative}

This opens the menu at the specified placement relative to the visualParent.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void QMenuProxy::removeMenuItem(QMenuItem \**item*) {#removeMenuItem}

This removes [MenuItem](https://doc.qt.io/qt-6/qml-qtquick-controls-menuitem.html) 'item'

@since 5.27

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.
