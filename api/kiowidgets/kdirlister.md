---
title: "KDirLister Class"
description: "Subclass of KCoreDirLister which uses QWidgets to show error messages and to associate jobs with windows."
---

# KDirLister Class

Subclass of [KCoreDirLister](../kiocore/kcoredirlister.md) which uses QWidgets to show error messages and to associate jobs with windows. [More...](#details)

- **Header:** `#include <KDirLister>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [KCoreDirLister](../kiocore/kcoredirlister.md)

[List of all members, including inherited members](kdirlister-members.md)

## Public Functions

- [KDirLister(QObject \*parent = nullptr)](#KDirLister)
- [~KDirLister()](#dtor.KDirLister)
- [bool autoErrorHandlingEnabled() const](#autoErrorHandlingEnabled)
- [QWidget \*mainWindow()](#mainWindow)
- [void setMainWindow(QWidget \*window)](#setMainWindow)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KDirLister::KDirLister(QObject \**parent* = nullptr) {#KDirLister}

Create a directory lister.

### \[override virtual noexcept\] KDirLister::~KDirLister() {#dtor.KDirLister}

Destroy the directory lister.

### bool KDirLister::autoErrorHandlingEnabled() const {#autoErrorHandlingEnabled}

Check whether auto error handling is enabled. If enabled, it will show an error dialog to the user when an error occurs. It is turned on by default.

Returns `true` if auto error handling is enabled, `false` otherwise

*See also* [setAutoErrorHandlingEnabled](../kiocore/kcoredirlister.md#setAutoErrorHandlingEnabled)()

### QWidget \*KDirLister::mainWindow() {#mainWindow}

Returns the main window associated with this object, or `nullptr` if there is none

*See also* [setMainWindow](kdirlister.md#setMainWindow)()

### void KDirLister::setMainWindow(QWidget \**window*) {#setMainWindow}

Pass the main window this object is associated with this is used for caching authentication data

`window` the window to associate with, `nullptr` to disassociate

*See also* [mainWindow](kdirlister.md#mainWindow)()
