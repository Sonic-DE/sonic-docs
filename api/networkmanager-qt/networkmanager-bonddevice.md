---
title: "NetworkManager::BondDevice Class"
description: "A bond device interface."
---

# NetworkManager::BondDevice Class

A bond device interface. [More...](#details)

- **Header:** `#include <NetworkManagerQt/BondDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Device](networkmanager-device.md)

[List of all members, including inherited members](networkmanager-bonddevice-members.md)

## Public Types

- [BondDevice::List](#List-typedef)
- [BondDevice::Ptr](#Ptr-typedef)

## Properties

- [\[read-only\] carrier : bool](#carrier-prop)
- [\[read-only\] hwAddress : QString](#hwAddress-prop)
- [\[read-only\] slaves : QStringList](#slaves-prop)

## Public Functions

- [BondDevice(const QString &path, QObject \*parent = nullptr)](#BondDevice)
- [bool carrier() const](#carrier)
- [QString hwAddress() const](#hwAddress)
- [QStringList slaves() const](#slaves)

## Signals

- [void carrierChanged(bool plugged)](#carrierChanged)
- [void hwAddressChanged(const QString &address)](#hwAddressChanged)
- [void slavesChanged(const QStringList &slaves)](#slavesChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### BondDevice::List {#List-typedef}

### BondDevice::Ptr {#Ptr-typedef}

## Property Documentation {#property-documentation}

### \[read-only\] carrier : bool {#carrier-prop}

**Access functions:**

- `bool` **[carrier](networkmanager-bonddevice.md#carrier)**() const

**Notifier signal:**

- `void` **[carrierChanged](networkmanager-bonddevice.md#carrierChanged)**(`bool` *plugged*)

### \[read-only\] hwAddress : QString {#hwAddress-prop}

**Access functions:**

- `QString` **[hwAddress](networkmanager-bonddevice.md#hwAddress)**() const

**Notifier signal:**

- `void` **[hwAddressChanged](networkmanager-bonddevice.md#hwAddressChanged)**(const `QString` &*address*)

### \[read-only\] slaves : QStringList {#slaves-prop}

**Access functions:**

- `QStringList` **[slaves](networkmanager-bonddevice.md#slaves)**() const

**Notifier signal:**

- `void` **[slavesChanged](networkmanager-bonddevice.md#slavesChanged)**(const `QStringList` &*slaves*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] BondDevice::BondDevice(const QString &*path*, QObject \**parent* = nullptr) {#BondDevice}

### bool BondDevice::carrier() const {#carrier}

Indicates whether the physical carrier is found

> **Note:** Getter function for property [carrier](networkmanager-bonddevice.md#carrier-prop).

### \[signal\] void BondDevice::carrierChanged(bool *plugged*) {#carrierChanged}

Emitted when the carrier of this device has changed

> **Note:** Notifier signal for property [carrier](networkmanager-bonddevice.md#carrier-prop).

### QString BondDevice::hwAddress() const {#hwAddress}

Hardware address of the device

> **Note:** Getter function for property [hwAddress](networkmanager-bonddevice.md#hwAddress-prop).

### \[signal\] void BondDevice::hwAddressChanged(const QString &*address*) {#hwAddressChanged}

Emitted when the hardware address of this device has changed

> **Note:** Notifier signal for property [hwAddress](networkmanager-bonddevice.md#hwAddress-prop).

### QStringList BondDevice::slaves() const {#slaves}

Array of object paths representing devices which are currently slaved to this device

> **Note:** Getter function for property [slaves](networkmanager-bonddevice.md#slaves-prop).

### \[signal\] void BondDevice::slavesChanged(const QStringList &*slaves*) {#slavesChanged}

Emitted when the slaves of this device have changed

> **Note:** Notifier signal for property [slaves](networkmanager-bonddevice.md#slaves-prop).
