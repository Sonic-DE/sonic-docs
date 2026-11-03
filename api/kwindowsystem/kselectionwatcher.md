---
title: "KSelectionWatcher Class"
description: "ICCCM manager selection watching."
---

# KSelectionWatcher Class

ICCCM manager selection watching. [More...](#details)

- **Header:** `#include <KSelectionWatcher>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KWindowSystem)`  
  `target_link_libraries(mytarget PRIVATE KF6::KWindowSystem)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kselectionwatcher-members.md)

## Public Functions

- [KSelectionWatcher(xcb\_atom\_t selection, int screen = -1, QObject \*parent = nullptr)](#KSelectionWatcher)
- [KSelectionWatcher(const char \*selection, int screen = -1, QObject \*parent = nullptr)](#KSelectionWatcher-1)
- [KSelectionWatcher(const char \*selection, xcb\_connection\_t \*c, xcb\_window\_t root, QObject \*parent = nullptr)](#KSelectionWatcher-2)
- [KSelectionWatcher(xcb\_atom\_t selection, xcb\_connection\_t \*c, xcb\_window\_t root, QObject \*parent = nullptr)](#KSelectionWatcher-3)
- [xcb\_window\_t owner()](#owner)

## Signals

- [void lostOwner()](#lostOwner)
- [void newOwner(xcb\_window\_t owner)](#newOwner)

## Detailed Description {#details}

This class implements watching manager selections, as described in the ICCCM section 2.8. It emits signal [newOwner](kselectionwatcher.md#newOwner)() when a new owner claim the selection, and emits [lostOwner](kselectionwatcher.md#lostOwner)() when the selection ownership is given up. To find out current owner of the selection, [owner](kselectionwatcher.md#owner)() can be used.

This class is only useful on the xcb platform. On other platforms the code is only functional if the constructor overloads taking an xcb\_connection\_t are used. In case you inherit from this class ensure that you don't use xcb and/or XLib without verifying the platform.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KSelectionWatcher::KSelectionWatcher(xcb\_atom\_t *selection*, int *screen* = -1, QObject \**parent* = nullptr) {#KSelectionWatcher}

This constructor initializes the object, but doesn't perform any operation on the selection.

`selection` atom representing the manager selection

`screen` X screen, or -1 for default

`parent` parent object, or nullptr if there is none

### \[explicit\] KSelectionWatcher::KSelectionWatcher(const char \**selection*, int *screen* = -1, QObject \**parent* = nullptr) {#KSelectionWatcher-1}

This constructor accepts the selection name and creates the appropriate atom for it automatically.

`selection` name of the manager selection

`screen` X screen, or -1 for default

`parent` parent object, or nullptr if there is none

This is an overloaded function.

### \[explicit\] KSelectionWatcher::KSelectionWatcher(const char \**selection*, xcb\_connection\_t \**c*, xcb\_window\_t *root*, QObject \**parent* = nullptr) {#KSelectionWatcher-2}

This constructor accepts the xcb\_connection\_t and root window and doesn't depend on running on the xcb platform. Otherwise this constructor behaves like the similar one without the xcb\_connection\_t.

`selection` name of the manager selection

`c` the xcb connection this [KSelectionWatcher](kselectionwatcher.md) should use

`root` the root window this [KSelectionWatcher](kselectionwatcher.md) should use

This is an overloaded function.

### \[explicit\] KSelectionWatcher::KSelectionWatcher(xcb\_atom\_t *selection*, xcb\_connection\_t \**c*, xcb\_window\_t *root*, QObject \**parent* = nullptr) {#KSelectionWatcher-3}

This constructor accepts the xcb\_connection\_t and root window and doesn't depend on running on the xcb platform. Otherwise this constructor behaves like the similar one without the xcb\_connection\_t.

`selection` atom representing the manager selection

`c` the xcb connection this [KSelectionWatcher](kselectionwatcher.md) should use

`root` the root window this [KSelectionWatcher](kselectionwatcher.md) should use

This is an overloaded function.

### \[signal\] void KSelectionWatcher::lostOwner() {#lostOwner}

This signal is emitted when the selection is given up, i.e. there's no owner. Note that the selection may be immediately claimed again, so the [newOwner](kselectionwatcher.md#newOwner)() signal may be emitted right after this one. It's safe to delete the instance in a slot connected to this signal.

### \[signal\] void KSelectionWatcher::newOwner(xcb\_window\_t *owner*) {#newOwner}

This signal is emitted when the selection is successfully claimed by a new owner.

`owner` the new owner of the selection

### xcb\_window\_t KSelectionWatcher::owner() {#owner}

Return the current owner of the manager selection, if any. Note that if the event informing about the owner change is still in the input queue, [newOwner](kselectionwatcher.md#newOwner)() might have been emitted yet.
