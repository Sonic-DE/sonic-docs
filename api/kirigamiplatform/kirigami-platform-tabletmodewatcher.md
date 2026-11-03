---
title: "Kirigami::Platform::TabletModeWatcher Class"
description: "This class reports on the status of certain transformable devices which can be both tablets and laptops at the same time, with a detachable keyboard."
---

# Kirigami::Platform::TabletModeWatcher Class

This class reports on the status of certain transformable devices which can be both tablets and laptops at the same time, with a detachable keyboard. [More...](#details)

- **Header:** `#include <Kirigami/Platform/TabletModeWatcher>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KirigamiPlatform)`  
  `target_link_libraries(mytarget PRIVATE KF6::KirigamiPlatform)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kirigami-platform-tabletmodewatcher-members.md)

## Properties

- [\[read-only\] tabletMode : bool](#tabletMode-prop)
- [\[read-only\] tabletModeAvailable : bool](#tabletModeAvailable-prop)

## Public Functions

- [void addWatcher(QObject \*watcher)](#addWatcher)
- [void removeWatcher(QObject \*watcher)](#removeWatcher)

## Detailed Description {#details}

It reports whether the device supports a tablet mode and if the device is currently in such mode or not, emitting a signal when the user switches.

## Property Documentation {#property-documentation}

### \[read-only\] tabletMode : bool {#tabletMode-prop}

`true` if the machine is now in tablet mode, such as the laptop keyboard flipped away or detached.

Note that this doesn't mean exactly a tablet form factor, but that the preferred input mode for the device is the touch screen and that pointer and keyboard are either secondary or not available.

For debug purposes, if either the environment variable QT\_QUICK\_CONTROLS\_MOBILE or KDE\_KIRIGAMI\_TABLET\_MODE are set to true, tabletMode will be true

**Access functions:**

- `bool` **isTabletMode**() const

**Notifier signal:**

- `void` **tabletModeChanged**(`bool` *tabletMode*)

### \[read-only\] tabletModeAvailable : bool {#tabletModeAvailable-prop}

`true` if the device supports a tablet mode and has a switch to report when the device has been transformed.

For debug purposes, if either the environment variable QT\_QUICK\_CONTROLS\_MOBILE or KDE\_KIRIGAMI\_TABLET\_MODE are set to true, tabletModeAvailable will be true

**Access functions:**

- `bool` **isTabletModeAvailable**() const

**Notifier signal:**

- `void` **tabletModeAvailableChanged**(`bool` *tabletModeAvailable*)

## Member Function Documentation {#member-function-documentation}

### void TabletModeWatcher::addWatcher(QObject \**watcher*) {#addWatcher}

Register an arbitrary [QObject](https://doc.qt.io/qt-6/qobject.html) to send events from this. At the moment only one event will be sent: [TabletModeChangedEvent](kirigami-platform-tabletmodechangedevent.md)

### void TabletModeWatcher::removeWatcher(QObject \**watcher*) {#removeWatcher}

Unsubscribe watcher from receiving events from [TabletModeWatcher](kirigami-platform-tabletmodewatcher.md).
