---
title: "NetworkManager::VethDevice Class"
description: "A veth device interface."
---

# NetworkManager::VethDevice Class

A veth device interface. [More...](#details)

- **Header:** `#include <NetworkManagerQt/VethDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Device](networkmanager-device.md)

[List of all members, including inherited members](networkmanager-vethdevice-members.md)

## Public Types

- [VethDevice::List](#List-typedef)
- [VethDevice::Ptr](#Ptr-typedef)

## Properties

- [\[read-only\] peer : QString](#peer-prop)

## Public Functions

- [VethDevice(const QString &path, QObject \*parent = nullptr)](#VethDevice)
- [QString peer() const](#peer)

## Signals

- [void peerChanged(const QString &peer)](#peerChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### VethDevice::List {#List-typedef}

### VethDevice::Ptr {#Ptr-typedef}

## Property Documentation {#property-documentation}

### \[read-only\] peer : QString {#peer-prop}

**Access functions:**

- `QString` **[peer](networkmanager-vethdevice.md#peer)**() const

**Notifier signal:**

- `void` **[peerChanged](networkmanager-vethdevice.md#peerChanged)**(const `QString` &*peer*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] VethDevice::VethDevice(const QString &*path*, QObject \**parent* = nullptr) {#VethDevice}

### QString VethDevice::peer() const {#peer}

> **Note:** Getter function for property [peer](networkmanager-vethdevice.md#peer-prop).

### \[signal\] void VethDevice::peerChanged(const QString &*peer*) {#peerChanged}

> **Note:** Notifier signal for property [peer](networkmanager-vethdevice.md#peer-prop).
