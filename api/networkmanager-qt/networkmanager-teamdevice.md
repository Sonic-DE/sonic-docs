---
title: "NetworkManager::TeamDevice Class"
description: "A team device interface."
---

# NetworkManager::TeamDevice Class

A team device interface. [More...](#details)

- **Header:** `#include <NetworkManagerQt/TeamDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Device](networkmanager-device.md)

[List of all members, including inherited members](networkmanager-teamdevice-members.md)

## Public Types

- [TeamDevice::List](#List-typedef)
- [TeamDevice::Ptr](#Ptr-typedef)

## Properties

- [\[read-only\] carrier : bool](#carrier-prop)
- [\[read-only\] config : QString](#config-prop)
- [\[read-only\] hwAddress : QString](#hwAddress-prop)
- [\[read-only\] slaves : QStringList](#slaves-prop)

## Public Functions

- [TeamDevice(const QString &path, QObject \*parent = nullptr)](#TeamDevice)
- [bool carrier() const](#carrier)
- [QString config() const](#config)
- [QString hwAddress() const](#hwAddress)
- [QStringList slaves() const](#slaves)
- [NetworkManager::Device::Type type() const](#type)

## Signals

- [void carrierChanged(bool plugged)](#carrierChanged)
- [void configChanged(const QString &config)](#configChanged)
- [void hwAddressChanged(const QString &address)](#hwAddressChanged)
- [void slavesChanged(const QStringList &slaves)](#slavesChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### TeamDevice::List {#List-typedef}

### TeamDevice::Ptr {#Ptr-typedef}

## Property Documentation {#property-documentation}

### \[read-only\] carrier : bool {#carrier-prop}

**Access functions:**

- `bool` **[carrier](networkmanager-teamdevice.md#carrier)**() const

**Notifier signal:**

- `void` **[carrierChanged](networkmanager-teamdevice.md#carrierChanged)**(`bool` *plugged*)

### \[read-only\] config : QString {#config-prop}

**Access functions:**

- `QString` **[config](networkmanager-teamdevice.md#config)**() const

**Notifier signal:**

- `void` **[configChanged](networkmanager-teamdevice.md#configChanged)**(const `QString` &*config*)

### \[read-only\] hwAddress : QString {#hwAddress-prop}

**Access functions:**

- `QString` **[hwAddress](networkmanager-teamdevice.md#hwAddress)**() const

**Notifier signal:**

- `void` **[hwAddressChanged](networkmanager-teamdevice.md#hwAddressChanged)**(const `QString` &*address*)

### \[read-only\] slaves : QStringList {#slaves-prop}

**Access functions:**

- `QStringList` **[slaves](networkmanager-teamdevice.md#slaves)**() const

**Notifier signal:**

- `void` **[slavesChanged](networkmanager-teamdevice.md#slavesChanged)**(const `QStringList` &*slaves*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] TeamDevice::TeamDevice(const QString &*path*, QObject \**parent* = nullptr) {#TeamDevice}

### bool TeamDevice::carrier() const {#carrier}

Indicates whether the physical carrier is found

> **Note:** Getter function for property [carrier](networkmanager-teamdevice.md#carrier-prop).

### \[signal\] void TeamDevice::carrierChanged(bool *plugged*) {#carrierChanged}

Emitted when the carrier of this device has changed

> **Note:** Notifier signal for property [carrier](networkmanager-teamdevice.md#carrier-prop).

### QString TeamDevice::config() const {#config}

The JSON configuration currently applied on the device.

> **Note:** Getter function for property [config](networkmanager-teamdevice.md#config-prop).

### \[signal\] void TeamDevice::configChanged(const QString &*config*) {#configChanged}

Emitted when the JSON confugration which is currently applied has changed

> **Note:** Notifier signal for property [config](networkmanager-teamdevice.md#config-prop).

### QString TeamDevice::hwAddress() const {#hwAddress}

Hardware address of the device

> **Note:** Getter function for property [hwAddress](networkmanager-teamdevice.md#hwAddress-prop).

### \[signal\] void TeamDevice::hwAddressChanged(const QString &*address*) {#hwAddressChanged}

Emitted when the hardware address of this device has changed

> **Note:** Notifier signal for property [hwAddress](networkmanager-teamdevice.md#hwAddress-prop).

### QStringList TeamDevice::slaves() const {#slaves}

Devices which are currently slaved to this device

> **Note:** Getter function for property [slaves](networkmanager-teamdevice.md#slaves-prop).

### \[signal\] void TeamDevice::slavesChanged(const QStringList &*slaves*) {#slavesChanged}

Emitted when the list of devices slaved to this device has changed

> **Note:** Notifier signal for property [slaves](networkmanager-teamdevice.md#slaves-prop).

### \[override virtual\] NetworkManager::Device::Type TeamDevice::type() const {#type}

Reimplements: [Device::type() const](networkmanager-device.md#type).
