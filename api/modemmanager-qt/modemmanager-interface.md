---
title: "ModemManager::Interface Class"
description: "Qt wrapper for modemmanager API."
---

# ModemManager::Interface Class

Qt wrapper for modemmanager API. [More...](#details)

- **Header:** `#include <ModemManagerQt/Interface>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)
- **Inherited By:** [ModemManager::Modem](modemmanager-modem.md), [ModemManager::Modem3gpp](modemmanager-modem3gpp.md), [ModemManager::Modem3gppUssd](modemmanager-modem3gppussd.md), [ModemManager::ModemCdma](modemmanager-modemcdma.md), [ModemManager::ModemCellBroadcast](modemmanager-modemcellbroadcast.md), [ModemManager::ModemFirmware](modemmanager-modemfirmware.md), [ModemManager::ModemLocation](modemmanager-modemlocation.md), [ModemManager::ModemMessaging](modemmanager-modemmessaging.md), [ModemManager::ModemOma](modemmanager-modemoma.md), [ModemManager::ModemSignal](modemmanager-modemsignal.md), [ModemManager::ModemSimple](modemmanager-modemsimple.md), [ModemManager::ModemTime](modemmanager-modemtime.md), and [ModemManager::ModemVoice](modemmanager-modemvoice.md)

[List of all members, including inherited members](modemmanager-interface-members.md)

## Public Types

- [Interface::List](#List-typedef)
- [Interface::Ptr](#Ptr-typedef)

## Public Functions

- [Interface(const QString &path, QObject \*parent = nullptr)](#Interface-1)
- [QString uni() const](#uni)

## Protected Functions

- [Interface(ModemManager::InterfacePrivate &dd, QObject \*parent = nullptr)](#Interface)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### Interface::List {#List-typedef}

### Interface::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit protected\] Interface::Interface(ModemManager::InterfacePrivate &*dd*, QObject \**parent* = nullptr) {#Interface}

### \[explicit\] Interface::Interface(const QString &*path*, QObject \**parent* = nullptr) {#Interface-1}

### QString Interface::uni() const {#uni}

> **Note:** Getter function for property uni.
