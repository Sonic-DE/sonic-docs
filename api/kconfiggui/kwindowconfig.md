---
title: "KWindowConfig Namespace"
description: "Save and load window sizes into a config."
---

# KWindowConfig Namespace

Save and load window sizes into a config. [More...](#details)

- **Header:** `#include <KWindowConfig>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigGui)`

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### \[since 6.0\] bool KWindowConfig::hasSavedWindowPosition(KConfigGroup &*config*) {#hasSavedWindowPosition}

Returns whether a given [KConfig](../kconfigcore/kconfig.md) group has any saved window position data.

> **Note:** : always returns false on Wayland where saving and restoring window position data is not supported.

`config` The config group to read from.

This function was introduced in Qt 6.0.

### \[since 6.0\] bool KWindowConfig::hasSavedWindowSize(KConfigGroup &*config*) {#hasSavedWindowSize}

Returns whether a given [KConfig](../kconfigcore/kconfig.md) group has any saved window size data.

`config` The config group to read from.

This function was introduced in Qt 6.0.

### void KWindowConfig::restoreWindowPosition(QWindow \**window*, const KConfigGroup &*config*) {#restoreWindowPosition}

Restores the window's screen position from the configuration and calls [restoreWindowScreenPosition](kwindowconfig.md#restoreWindowScreenPosition). This function has no effect on Wayland, where the compositor is responsible for window positioning.

`window` The window whose position to restore.

`config` The config group to read from.

### void KWindowConfig::restoreWindowScreenPosition(QWindow \**window*, const QScreen \**screen*, const KConfigGroup &*config*) {#restoreWindowScreenPosition}

Restores the window's position on provided screen from the configuration. This function has no effect on Wayland, where the compositor is responsible for window positioning.

`window` The window whose position to restore.

`screen` Screen on which window should be placed.

`config` The config group to read from.

### void KWindowConfig::restoreWindowSize(QWindow \**window*, const KConfigGroup &*config*) {#restoreWindowSize}

Restores the dialog's size from the configuration according to the screen size.

If you're calling this from a constructor (for a mainwindow or dialog, for instance) you should first call winId() so that a [QWindow](https://doc.qt.io/qt-6/qwindow.html) is created, then you can call windowHandle() to pass to this method.

Example code:

```cpp
create(); // ensure there's a window created
const QSize availableSize = windowHandle()->screen()->availableSize();
windowHandle()->resize(availableSize.width() * 0.7, availableSize.height() * 0.5); // default size
KWindowConfig::restoreWindowSize(windowHandle(), KSharedConfig::openConfig()->group("MyDialog"));
resize(windowHandle()->size()); // workaround for QTBUG-40584
```

`window` The window to restore size.

`config` The config group to read from.

### void KWindowConfig::saveWindowPosition(const QWindow \**window*, KConfigGroup &*config*, KConfigGroup::WriteConfigFlags *options* = KConfigGroup::Normal) {#saveWindowPosition}

Saves the window's position either to the global or application config file. This function has no effect on Wayland, where the compositor is responsible for window positioning.

`window` The window whose position to save.

`config` The config group to read from.

`options` passed to [KConfigGroup::writeEntry](../kconfigcore/kconfiggroup.md#writeEntry)()

### void KWindowConfig::saveWindowSize(const QWindow \**window*, KConfigGroup &*config*, KConfigGroup::WriteConfigFlags *options* = KConfigGroup::Normal) {#saveWindowSize}

Saves the window's size dependent on the screen dimension either to the global or application config file.

`window` The window to save size.

`config` The config group to read from.

`options` passed to [KConfigGroup::writeEntry](../kconfigcore/kconfiggroup.md#writeEntry)()
