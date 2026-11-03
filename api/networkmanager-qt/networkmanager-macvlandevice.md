---
title: "NetworkManager::MacVlanDevice Class"
description: "A macvlan device interface."
---

# NetworkManager::MacVlanDevice Class

A macvlan device interface. [More...](#details)

- **Header:** `#include <NetworkManagerQt/MacVlanDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Device](networkmanager-device.md)

[List of all members, including inherited members](networkmanager-macvlandevice-members.md)

## Public Types

- [MacVlanDevice::List](#List-typedef)
- [MacVlanDevice::Ptr](#Ptr-typedef)

## Properties

- [\[read-only\] mode : QString](#mode-prop)
- [\[read-only\] noPromisc : bool](#noPromisc-prop)
- [\[read-only\] parent : QString](#parent-prop)

## Public Functions

- [MacVlanDevice(const QString &path, QObject \*parent = nullptr)](#MacVlanDevice)
- [QString mode() const](#mode)
- [bool noPromisc() const](#noPromisc)
- [QString parent() const](#parent)

## Signals

- [void modeChanged(const QString &mode)](#modeChanged)
- [void noPromiscChanged(bool noPromisc)](#noPromiscChanged)
- [void parentChanged(const QString &parent)](#parentChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### MacVlanDevice::List {#List-typedef}

### MacVlanDevice::Ptr {#Ptr-typedef}

## Property Documentation {#property-documentation}

### \[read-only\] mode : QString {#mode-prop}

**Access functions:**

- `QString` **[mode](networkmanager-macvlandevice.md#mode)**() const

**Notifier signal:**

- `void` **[modeChanged](networkmanager-macvlandevice.md#modeChanged)**(const `QString` &*mode*)

### \[read-only\] noPromisc : bool {#noPromisc-prop}

**Access functions:**

- `bool` **[noPromisc](networkmanager-macvlandevice.md#noPromisc)**() const

**Notifier signal:**

- `void` **[noPromiscChanged](networkmanager-macvlandevice.md#noPromiscChanged)**(`bool` *noPromisc*)

### \[read-only\] parent : QString {#parent-prop}

**Access functions:**

- `QString` **[parent](networkmanager-macvlandevice.md#parent)**() const

**Notifier signal:**

- `void` **[parentChanged](networkmanager-macvlandevice.md#parentChanged)**(const `QString` &*parent*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] MacVlanDevice::MacVlanDevice(const QString &*path*, QObject \**parent* = nullptr) {#MacVlanDevice}

### QString MacVlanDevice::mode() const {#mode}

> **Note:** Getter function for property [mode](networkmanager-macvlandevice.md#mode-prop).

### \[signal\] void MacVlanDevice::modeChanged(const QString &*mode*) {#modeChanged}

> **Note:** Notifier signal for property [mode](networkmanager-macvlandevice.md#mode-prop).

### bool MacVlanDevice::noPromisc() const {#noPromisc}

> **Note:** Getter function for property [noPromisc](networkmanager-macvlandevice.md#noPromisc-prop).

### \[signal\] void MacVlanDevice::noPromiscChanged(bool *noPromisc*) {#noPromiscChanged}

> **Note:** Notifier signal for property [noPromisc](networkmanager-macvlandevice.md#noPromisc-prop).

### QString MacVlanDevice::parent() const {#parent}

> **Note:** Getter function for property [parent](networkmanager-macvlandevice.md#parent-prop).

### \[signal\] void MacVlanDevice::parentChanged(const QString &*parent*) {#parentChanged}

> **Note:** Notifier signal for property [parent](networkmanager-macvlandevice.md#parent-prop).
