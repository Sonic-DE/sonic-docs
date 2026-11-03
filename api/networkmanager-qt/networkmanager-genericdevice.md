---
title: "NetworkManager::GenericDevice Class"
description: "A generic device interface."
---

# NetworkManager::GenericDevice Class

A generic device interface. [More...](#details)

- **Header:** `#include <NetworkManagerQt/GenericDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Device](networkmanager-device.md)

[List of all members, including inherited members](networkmanager-genericdevice-members.md)

## Public Types

- [GenericDevice::List](#List-typedef)
- [GenericDevice::Ptr](#Ptr-typedef)

## Properties

- [\[read-only\] hardwareAddress : QString](#hardwareAddress-prop)
- [\[read-only\] typeDescription : QString](#typeDescription-prop)

## Public Functions

- [GenericDevice(const QString &path, QObject \*parent = nullptr)](#GenericDevice)
- [QString hardwareAddress() const](#hardwareAddress)
- [NetworkManager::Device::Type type() const](#type)
- [QString typeDescription() const](#typeDescription)

## Signals

- [void hardwareAddressChanged(const QString &hwAddress)](#hardwareAddressChanged)
- [void permanentHardwareAddressChanged(const QString &permHwAddress)](#permanentHardwareAddressChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### GenericDevice::List {#List-typedef}

### GenericDevice::Ptr {#Ptr-typedef}

## Property Documentation {#property-documentation}

### \[read-only\] hardwareAddress : QString {#hardwareAddress-prop}

**Access functions:**

- `QString` **[hardwareAddress](networkmanager-genericdevice.md#hardwareAddress)**() const

### \[read-only\] typeDescription : QString {#typeDescription-prop}

**Access functions:**

- `QString` **[typeDescription](networkmanager-genericdevice.md#typeDescription)**() const

## Member Function Documentation {#member-function-documentation}

### \[explicit\] GenericDevice::GenericDevice(const QString &*path*, QObject \**parent* = nullptr) {#GenericDevice}

### QString GenericDevice::hardwareAddress() const {#hardwareAddress}

Active hardware address of the device

> **Note:** Getter function for property [hardwareAddress](networkmanager-genericdevice.md#hardwareAddress-prop).

### \[signal\] void GenericDevice::hardwareAddressChanged(const QString &*hwAddress*) {#hardwareAddressChanged}

Emitted when the hardware address of this device has changed

### \[signal\] void GenericDevice::permanentHardwareAddressChanged(const QString &*permHwAddress*) {#permanentHardwareAddressChanged}

Emitted when the type description this device has changed

### \[override virtual\] NetworkManager::Device::Type GenericDevice::type() const {#type}

Reimplements: [Device::type() const](networkmanager-device.md#type).

Return the type

### QString GenericDevice::typeDescription() const {#typeDescription}

A (non-localized) description of the interface type, if known.

> **Note:** Getter function for property [typeDescription](networkmanager-genericdevice.md#typeDescription-prop).
