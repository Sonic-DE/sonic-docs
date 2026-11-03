---
title: "NetworkManager::BridgeDevice Class"
description: "A bridge device interface."
---

# NetworkManager::BridgeDevice Class

A bridge device interface. [More...](#details)

- **Header:** `#include <NetworkManagerQt/BridgeDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Device](networkmanager-device.md)

[List of all members, including inherited members](networkmanager-bridgedevice-members.md)

## Public Types

- [BridgeDevice::List](#List-typedef)
- [BridgeDevice::Ptr](#Ptr-typedef)

## Properties

- [\[read-only\] carrier : bool](#carrier-prop)
- [\[read-only\] hwAddress : QString](#hwAddress-prop)
- [\[read-only\] slaves : QStringList](#slaves-prop)

## Public Functions

- [BridgeDevice(const QString &path, QObject \*parent = nullptr)](#BridgeDevice)
- [bool carrier() const](#carrier)
- [QString hwAddress() const](#hwAddress)
- [QStringList slaves() const](#slaves)

## Signals

- [void carrierChanged(bool plugged)](#carrierChanged)
- [void hwAddressChanged(const QString &address)](#hwAddressChanged)
- [void slavesChanged(const QStringList &slaves)](#slavesChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### BridgeDevice::List {#List-typedef}

### BridgeDevice::Ptr {#Ptr-typedef}

## Property Documentation {#property-documentation}

### \[read-only\] carrier : bool {#carrier-prop}

**Access functions:**

- `bool` **[carrier](networkmanager-bridgedevice.md#carrier)**() const

**Notifier signal:**

- `void` **[carrierChanged](networkmanager-bridgedevice.md#carrierChanged)**(`bool` *plugged*)

### \[read-only\] hwAddress : QString {#hwAddress-prop}

**Access functions:**

- `QString` **[hwAddress](networkmanager-bridgedevice.md#hwAddress)**() const

**Notifier signal:**

- `void` **[hwAddressChanged](networkmanager-bridgedevice.md#hwAddressChanged)**(const `QString` &*address*)

### \[read-only\] slaves : QStringList {#slaves-prop}

**Access functions:**

- `QStringList` **[slaves](networkmanager-bridgedevice.md#slaves)**() const

**Notifier signal:**

- `void` **[slavesChanged](networkmanager-bridgedevice.md#slavesChanged)**(const `QStringList` &*slaves*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] BridgeDevice::BridgeDevice(const QString &*path*, QObject \**parent* = nullptr) {#BridgeDevice}

### bool BridgeDevice::carrier() const {#carrier}

Indicates whether the physical carrier is found

> **Note:** Getter function for property [carrier](networkmanager-bridgedevice.md#carrier-prop).

### \[signal\] void BridgeDevice::carrierChanged(bool *plugged*) {#carrierChanged}

Emitted when the carrier of this device has changed

> **Note:** Notifier signal for property [carrier](networkmanager-bridgedevice.md#carrier-prop).

### QString BridgeDevice::hwAddress() const {#hwAddress}

Hardware address of the device

> **Note:** Getter function for property [hwAddress](networkmanager-bridgedevice.md#hwAddress-prop).

### \[signal\] void BridgeDevice::hwAddressChanged(const QString &*address*) {#hwAddressChanged}

Emitted when the hardware address of this device has changed

> **Note:** Notifier signal for property [hwAddress](networkmanager-bridgedevice.md#hwAddress-prop).

### QStringList BridgeDevice::slaves() const {#slaves}

Array of object paths representing devices which are currently slaved to this device

> **Note:** Getter function for property [slaves](networkmanager-bridgedevice.md#slaves-prop).

### \[signal\] void BridgeDevice::slavesChanged(const QStringList &*slaves*) {#slavesChanged}

Emitted when the slaves of this device have changed

> **Note:** Notifier signal for property [slaves](networkmanager-bridgedevice.md#slaves-prop).
