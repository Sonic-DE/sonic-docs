---
title: "KAcceleratorManager Class"
description: "KDE Accelerator manager."
---

# KAcceleratorManager Class

KDE Accelerator manager. [More...](#details)

- **Header:** `#include <KAcceleratorManager>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`

[List of all members, including inherited members](kacceleratormanager-members.md)

## Static Public Members

- [void addStandardActionNames(const QStringList &names)](#addStandardActionNames)
- [void manage(QWidget \*widget, bool programmers\_mode = false)](#manage)
- [void setNoAccel(QWidget \*widget)](#setNoAccel)

## Detailed Description {#details}

This class can be used to find a valid and working set of accelerators for any widget.

## Member Function Documentation {#member-function-documentation}

### \[static\] void KAcceleratorManager::addStandardActionNames(const QStringList &*names*) {#addStandardActionNames}

Append names to a list of standard action names.

These strings will be given higher priority when assigning keyboard accelerators.

### \[static\] void KAcceleratorManager::manage(QWidget \**widget*, bool *programmers\_mode* = false) {#manage}

Manages the accelerators of a widget.

Call this function on the top widget of the hierarchy you want to manage. It will fix the accelerators of the child widgets so there are never duplicate accelerators. It also tries to put accelerators on as many widgets as possible.

The algorithm used tries to take the existing accelerators into account, as well as the class of each widget. Hopefully, the result is close to what you would assign manually.

[QMenu](https://doc.qt.io/qt-6/qmenu.html)'s are managed dynamically, so when you add or remove entries, the accelerators are reassigned. If you add or remove widgets to your toplevel widget, you will have to call manage again to fix the accelerators.

`widget` The toplevel widget you want to manage.

`programmers_mode` if true, [KAcceleratorManager](kacceleratormanager.md) adds (&) for removed accels and & before added accels

### \[static\] void KAcceleratorManager::setNoAccel(QWidget \**widget*) {#setNoAccel}

Use this method for a widget (and its children) you want no accels to be set on.
