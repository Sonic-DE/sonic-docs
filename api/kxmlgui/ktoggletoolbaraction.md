---
title: "KToggleToolBarAction Class"
description: "Collection of convenience classes and widgets to manage your own main QtWidgets window."
---

# KToggleToolBarAction Class

Collection of convenience classes and widgets to manage your own main QtWidgets window. [More...](#details)

- **Header:** `#include <KToggleToolBarAction>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS XmlGui)`  
  `target_link_libraries(mytarget PRIVATE KF6::XmlGui)`

[List of all members, including inherited members](ktoggletoolbaraction-members.md)

## Public Functions

- [KToggleToolBarAction(KToolBar \*toolBar, const QString &text, QObject \*parent)](#KToggleToolBarAction)
- [~KToggleToolBarAction()](#dtor.KToggleToolBarAction)
- [bool eventFilter(QObject \*watched, QEvent \*event)](#eventFilter)
- [KToolBar \*toolBar()](#toolBar)

## Detailed Description {#details}

An action that takes care of everything associated with showing or hiding a toolbar by a menu action. It will show or hide the toolbar with the given name when activated, and check or uncheck itself if the toolbar is manually shown or hidden.

If you need to perform some additional action when the toolbar is shown or hidden, connect to the toggled(bool) signal. It will be emitted after the toolbar's visibility has changed, whenever it changes.

## Member Function Documentation {#member-function-documentation}

### KToggleToolBarAction::KToggleToolBarAction(KToolBar \**toolBar*, const QString &*text*, QObject \**parent*) {#KToggleToolBarAction}

Creates a [KToggleToolBarAction](ktoggletoolbaraction.md) that manages the `toolBar` with `text` in its label, as a child of `parent`.

### \[override virtual noexcept\] KToggleToolBarAction::~KToggleToolBarAction() {#dtor.KToggleToolBarAction}

Destroys the toggle toolbar action.

### \[override virtual\] bool KToggleToolBarAction::eventFilter(QObject \**watched*, QEvent \**event*) {#eventFilter}

Filters then returns the specified `event` for a given `watched` object.

Reimplemented from [QObject](https://doc.qt.io/qt-6/qobject.html).

### KToolBar \*KToggleToolBarAction::toolBar() {#toolBar}

Returns a pointer to the tool bar it manages.
