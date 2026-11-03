---
title: "NetworkManager::VlanDevice Class"
description: "A vlan device interface."
---

# NetworkManager::VlanDevice Class

A vlan device interface. [More...](#details)

- **Header:** `#include <NetworkManagerQt/VlanDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Device](networkmanager-device.md)

[List of all members, including inherited members](networkmanager-vlandevice-members.md)

## Public Types

- [VlanDevice::List](#List-typedef)
- [VlanDevice::Ptr](#Ptr-typedef)

## Properties

- [\[read-only\] carrier : bool](#carrier-prop)
- [\[read-only\] hwAddress : QString](#hwAddress-prop)
- [\[read-only\] parent : NetworkManager::Device::Ptr](#parent-prop)
- [\[read-only\] vlanId : uint](#vlanId-prop)

## Public Functions

- [VlanDevice(const QString &path, QObject \*parent = nullptr)](#VlanDevice)
- [bool carrier() const](#carrier)
- [QString hwAddress() const](#hwAddress)
- [NetworkManager::Device::Ptr parent() const](#parent)
- [uint vlanId() const](#vlanId)

## Signals

- [void carrierChanged(bool plugged)](#carrierChanged)
- [void hwAddressChanged(const QString &address)](#hwAddressChanged)
- [void parentChanged(const QString &path)](#parentChanged)
- [void vlanIdChanged(uint id)](#vlanIdChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### VlanDevice::List {#List-typedef}

### VlanDevice::Ptr {#Ptr-typedef}

## Property Documentation {#property-documentation}

### \[read-only\] carrier : bool {#carrier-prop}

**Access functions:**

- `bool` **[carrier](networkmanager-vlandevice.md#carrier)**() const

**Notifier signal:**

- `void` **[carrierChanged](networkmanager-vlandevice.md#carrierChanged)**(`bool` *plugged*)

### \[read-only\] hwAddress : QString {#hwAddress-prop}

**Access functions:**

- `QString` **[hwAddress](networkmanager-vlandevice.md#hwAddress)**() const

**Notifier signal:**

- `void` **[hwAddressChanged](networkmanager-vlandevice.md#hwAddressChanged)**(const `QString` &*address*)

### \[read-only\] parent : NetworkManager::Device::Ptr {#parent-prop}

**Access functions:**

- `NetworkManager::Device::Ptr` **[parent](networkmanager-vlandevice.md#parent)**() const

**Notifier signal:**

- `void` **[parentChanged](networkmanager-vlandevice.md#parentChanged)**(const `QString` &*path*)

### \[read-only\] vlanId : uint {#vlanId-prop}

**Access functions:**

- `uint` **[vlanId](networkmanager-vlandevice.md#vlanId)**() const

**Notifier signal:**

- `void` **[vlanIdChanged](networkmanager-vlandevice.md#vlanIdChanged)**(`uint` *id*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] VlanDevice::VlanDevice(const QString &*path*, QObject \**parent* = nullptr) {#VlanDevice}

### bool VlanDevice::carrier() const {#carrier}

Indicates whether the physical carrier is found

> **Note:** Getter function for property [carrier](networkmanager-vlandevice.md#carrier-prop).

### \[signal\] void VlanDevice::carrierChanged(bool *plugged*) {#carrierChanged}

Emitted when the carrier of this device has changed

> **Note:** Notifier signal for property [carrier](networkmanager-vlandevice.md#carrier-prop).

### QString VlanDevice::hwAddress() const {#hwAddress}

Hardware address of the device

> **Note:** Getter function for property [hwAddress](networkmanager-vlandevice.md#hwAddress-prop).

### \[signal\] void VlanDevice::hwAddressChanged(const QString &*address*) {#hwAddressChanged}

Emitted when the hardware address of this device has changed

> **Note:** Notifier signal for property [hwAddress](networkmanager-vlandevice.md#hwAddress-prop).

### NetworkManager::Device::Ptr VlanDevice::parent() const {#parent}

The parent device of this VLAN device

> **Note:** Getter function for property [parent](networkmanager-vlandevice.md#parent-prop).

### \[signal\] void VlanDevice::parentChanged(const QString &*path*) {#parentChanged}

Emitted when the parent device of this device has changed

> **Note:** Notifier signal for property [parent](networkmanager-vlandevice.md#parent-prop).

### uint VlanDevice::vlanId() const {#vlanId}

The VLAN ID of this VLAN interface

> **Note:** Getter function for property [vlanId](networkmanager-vlandevice.md#vlanId-prop).

### \[signal\] void VlanDevice::vlanIdChanged(uint *id*) {#vlanIdChanged}

Emitted when the VLAN ID of this device has changed

> **Note:** Notifier signal for property [vlanId](networkmanager-vlandevice.md#vlanId-prop).
