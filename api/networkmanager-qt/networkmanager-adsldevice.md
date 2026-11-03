---
title: "NetworkManager::AdslDevice Class"
description: "An adsl device interface."
---

# NetworkManager::AdslDevice Class

An adsl device interface. [More...](#details)

- **Header:** `#include <NetworkManagerQt/AdslDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Device](networkmanager-device.md)

[List of all members, including inherited members](networkmanager-adsldevice-members.md)

## Public Types

- [AdslDevice::List](#List-typedef)
- [AdslDevice::Ptr](#Ptr-typedef)

## Properties

- [\[read-only\] carrier : bool](#carrier-prop)

## Public Functions

- [AdslDevice(const QString &path, QObject \*parent = nullptr)](#AdslDevice)
- [bool carrier() const](#carrier)

## Signals

- [void carrierChanged(bool plugged)](#carrierChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### AdslDevice::List {#List-typedef}

### AdslDevice::Ptr {#Ptr-typedef}

## Property Documentation {#property-documentation}

### \[read-only\] carrier : bool {#carrier-prop}

**Access functions:**

- `bool` **[carrier](networkmanager-adsldevice.md#carrier)**() const

**Notifier signal:**

- `void` **[carrierChanged](networkmanager-adsldevice.md#carrierChanged)**(`bool` *plugged*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] AdslDevice::AdslDevice(const QString &*path*, QObject \**parent* = nullptr) {#AdslDevice}

### bool AdslDevice::carrier() const {#carrier}

Indicates whether the physical carrier is found

> **Note:** Getter function for property [carrier](networkmanager-adsldevice.md#carrier-prop).

### \[signal\] void AdslDevice::carrierChanged(bool *plugged*) {#carrierChanged}

Emitted when the carrier of this device has changed

> **Note:** Notifier signal for property [carrier](networkmanager-adsldevice.md#carrier-prop).
