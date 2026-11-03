---
title: "ModemManager::Notifier Class"
description: "Qt wrapper for modemmanager API."
---

# ModemManager::Notifier Class

Qt wrapper for modemmanager API. [More...](#details)

- **Header:** `#include <ModemManagerQt/Manager>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](modemmanager-notifier-members.md)

## Signals

- [void modemAdded(const QString &udi)](#modemAdded)
- [void modemRemoved(const QString &udi)](#modemRemoved)
- [void serviceAppeared()](#serviceAppeared)
- [void serviceDisappeared()](#serviceDisappeared)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[signal\] void Notifier::modemAdded(const QString &*udi*) {#modemAdded}

This signal is emitted when a new modem interface is available.

`udi` the network interface identifier

### \[signal\] void Notifier::modemRemoved(const QString &*udi*) {#modemRemoved}

This signal is emitted when a network interface is not available anymore.

`udi` the network interface identifier

### \[signal\] void Notifier::serviceAppeared() {#serviceAppeared}

This signal is emitted when the [ModemManager](modemmanager.md) DBus service appears

### \[signal\] void Notifier::serviceDisappeared() {#serviceDisappeared}

This signal is emitted when the [ModemManager](modemmanager.md) DBus service goes away
