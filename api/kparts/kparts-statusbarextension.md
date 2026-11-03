---
title: "KParts::StatusBarExtension Class"
description: "An extension for KParts that allows more sophisticated statusbar handling."
---

# KParts::StatusBarExtension Class

An extension for [KParts](kparts-module.md) that allows more sophisticated statusbar handling. [More...](#details)

- **Header:** `#include <KParts/StatusBarExtension>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Parts)`  
  `target_link_libraries(mytarget PRIVATE KF6::Parts)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kparts-statusbarextension-members.md)

## Public Functions

- [StatusBarExtension(KParts::Part \*parent)](#StatusBarExtension)
- [StatusBarExtension(KParts::ReadOnlyPart \*parent)](#StatusBarExtension-1)
- [void addStatusBarItem(QWidget \*widget, int stretch, bool permanent)](#addStatusBarItem)
- [void removeStatusBarItem(QWidget \*widget)](#removeStatusBarItem)
- [void setStatusBar(QStatusBar \*status)](#setStatusBar)
- [QStatusBar \*statusBar() const](#statusBar)

## Static Public Members

- [KParts::StatusBarExtension \*childObject(QObject \*obj)](#childObject)

## Detailed Description {#details}

Every part can use this class to customize the statusbar as long as it is active. Add items via [addStatusBarItem](kparts-statusbarextension.md#addStatusBarItem) and remove an item with [removeStatusBarItem](kparts-statusbarextension.md#removeStatusBarItem).

IMPORTANT: do NOT add any items immediately after constructing the extension. Give the application time to set the statusbar in the extension if necessary.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] StatusBarExtension::StatusBarExtension(KParts::Part \**parent*) {#StatusBarExtension}

### \[explicit\] StatusBarExtension::StatusBarExtension(KParts::ReadOnlyPart \**parent*) {#StatusBarExtension-1}

### void StatusBarExtension::addStatusBarItem(QWidget \**widget*, int *stretch*, bool *permanent*) {#addStatusBarItem}

This adds a widget to the statusbar for this part. If you use this method instead of using [statusBar](kparts-statusbarextension.md#statusBar)() directly, this extension will take care of removing the items when the parts GUI is deactivated and will re-add them when it is reactivated. The parameters are the same as [QStatusBar::addWidget](https://doc.qt.io/qt-6/qstatusbar.html#addWidget)().

Note that you can't use KStatusBar methods (inserting text items by id) but you can create a KStatusBarLabel with a dummy id instead, and use it directly in order to get the same look and feel.

`widget` the widget to add

`stretch` the stretch factor. 0 for a minimum size.

`permanent` passed to [QStatusBar::addWidget](https://doc.qt.io/qt-6/qstatusbar.html#addWidget) as the "permanent" bool.

Note that the item isn't really permanent though, it goes away when the part is unactivated. This simply controls whether temporary messages hide the `widget`, and whether it's added to the left or to the right side.

> **Note:** that the widget does not technically become a child of the [StatusBarExtension](kparts-statusbarextension.md) in a [QObject](https://doc.qt.io/qt-6/qobject.html) sense. However, it will be deleted when the [StatusBarExtension](kparts-statusbarextension.md) is deleted.

IMPORTANT: do NOT add any items immediately after constructing the extension. Give the application time to set the statusbar in the extension if necessary.

### \[static\] KParts::StatusBarExtension \*StatusBarExtension::childObject(QObject \**obj*) {#childObject}

Queries `obj` for a child object which inherits from this [StatusBarExtension](kparts-statusbarextension.md) class. Convenience method.

### void StatusBarExtension::removeStatusBarItem(QWidget \**widget*) {#removeStatusBarItem}

Remove a widget from the statusbar for this part.

### void StatusBarExtension::setStatusBar(QStatusBar \**status*) {#setStatusBar}

This allows the hosting application to set a particular [QStatusBar](https://doc.qt.io/qt-6/qstatusbar.html) for this part. If it doesn't do this, the statusbar used will be the one of the [KMainWindow](../kxmlgui/kmainwindow.md) in which the part is embedded. Konqueror uses this to assign a view-statusbar to the part. The part should never call this method!

*See also* [statusBar](kparts-statusbarextension.md#statusBar)()

### QStatusBar \*StatusBarExtension::statusBar() const {#statusBar}

Returns the statusbar of the [KMainWindow](../kxmlgui/kmainwindow.md) in which this part is currently embedded. This can return `nullptr`

*See also* [setStatusBar](kparts-statusbarextension.md#setStatusBar)()
