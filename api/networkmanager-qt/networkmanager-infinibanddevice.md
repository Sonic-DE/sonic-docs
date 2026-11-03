---
title: "NetworkManager::InfinibandDevice Class"
description: "An infiniband device interface."
---

# NetworkManager::InfinibandDevice Class

An infiniband device interface. [More...](#details)

- **Header:** `#include <NetworkManagerQt/InfinibandDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Device](networkmanager-device.md)

[List of all members, including inherited members](networkmanager-infinibanddevice-members.md)

## Public Types

- [InfinibandDevice::List](#List-typedef)
- [InfinibandDevice::Ptr](#Ptr-typedef)

## Properties

- [\[read-only\] carrier : bool](#carrier-prop)
- [\[read-only\] hwAddress : QString](#hwAddress-prop)

## Public Functions

- [InfinibandDevice(const QString &path, QObject \*parent = nullptr)](#InfinibandDevice)
- [bool carrier() const](#carrier)
- [QString hwAddress() const](#hwAddress)

## Signals

- [void carrierChanged(bool plugged)](#carrierChanged)
- [void hwAddressChanged(const QString &address)](#hwAddressChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### InfinibandDevice::List {#List-typedef}

### InfinibandDevice::Ptr {#Ptr-typedef}

## Property Documentation {#property-documentation}

### \[read-only\] carrier : bool {#carrier-prop}

**Access functions:**

- `bool` **[carrier](networkmanager-infinibanddevice.md#carrier)**() const

**Notifier signal:**

- `void` **[carrierChanged](networkmanager-infinibanddevice.md#carrierChanged)**(`bool` *plugged*)

### \[read-only\] hwAddress : QString {#hwAddress-prop}

**Access functions:**

- `QString` **[hwAddress](networkmanager-infinibanddevice.md#hwAddress)**() const

**Notifier signal:**

- `void` **[hwAddressChanged](networkmanager-infinibanddevice.md#hwAddressChanged)**(const `QString` &*address*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] InfinibandDevice::InfinibandDevice(const QString &*path*, QObject \**parent* = nullptr) {#InfinibandDevice}

### bool InfinibandDevice::carrier() const {#carrier}

Indicates whether the physical carrier is found

> **Note:** Getter function for property [carrier](networkmanager-infinibanddevice.md#carrier-prop).

### \[signal\] void InfinibandDevice::carrierChanged(bool *plugged*) {#carrierChanged}

Emitted when the carrier of this device has changed

> **Note:** Notifier signal for property [carrier](networkmanager-infinibanddevice.md#carrier-prop).

### QString InfinibandDevice::hwAddress() const {#hwAddress}

Hardware address of the device

> **Note:** Getter function for property [hwAddress](networkmanager-infinibanddevice.md#hwAddress-prop).

### \[signal\] void InfinibandDevice::hwAddressChanged(const QString &*address*) {#hwAddressChanged}

Emitted when the hardware address of this device has changed

> **Note:** Notifier signal for property [hwAddress](networkmanager-infinibanddevice.md#hwAddress-prop).
