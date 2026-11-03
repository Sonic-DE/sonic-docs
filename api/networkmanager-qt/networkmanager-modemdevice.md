---
title: "NetworkManager::ModemDevice Class"
description: "Represents a generic modem device, generally defined by the modemCapabilities() it exposes and at the current point in time by the currentCapabilities()."
---

# NetworkManager::ModemDevice Class

Represents a generic modem device, generally defined by the [modemCapabilities](networkmanager-modemdevice.md#modemCapabilities)() it exposes and at the current point in time by the [currentCapabilities](networkmanager-modemdevice.md#currentCapabilities)(). [More...](#details)

- **Header:** `#include <NetworkManagerQt/ModemDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Device](networkmanager-device.md)
- **Inherited By:** [NetworkManager::BluetoothDevice](networkmanager-bluetoothdevice.md)

[List of all members, including inherited members](networkmanager-modemdevice-members.md)

## Public Types

- [enum ModemDevice::Capability](#Capability-enum)
- [ModemDevice::List](#List-typedef)
- [ModemDevice::Ptr](#Ptr-typedef)

## Public Functions

- [ModemDevice(const QString &path, QObject \*parent = nullptr)](#ModemDevice-1)
- [NetworkManager::ModemDevice::Capabilities currentCapabilities() const](#currentCapabilities)
- [NetworkManager::ModemDevice::Capabilities modemCapabilities() const](#modemCapabilities)
- [NetworkManager::Device::Type type() const](#type)

## Signals

- [void currentCapabilitiesChanged(NetworkManager::ModemDevice::Capabilities)](#currentCapabilitiesChanged)

## Protected Functions

- [ModemDevice(NetworkManager::ModemDevicePrivate &dd, QObject \*parent = nullptr)](#ModemDevice)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum ModemDevice::Capability {#Capability-enum}

**flags ModemDevice::Capabilities**

| Constant |   |
| --- | --- |
| `NetworkManager::ModemDevice::NoCapability` | `0x0` |
| `NetworkManager::ModemDevice::Pots` | `0x1` |
| `NetworkManager::ModemDevice::CdmaEvdo` | `0x2` |
| `NetworkManager::ModemDevice::GsmUmts` | `0x4` |
| `NetworkManager::ModemDevice::Lte` | `0x8` |

The `Capabilities` type is a typedef for `QFlags<Capability>. `It stores an OR combination of `Capability` values.

### ModemDevice::List {#List-typedef}

### ModemDevice::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit protected\] ModemDevice::ModemDevice(NetworkManager::ModemDevicePrivate &*dd*, QObject \**parent* = nullptr) {#ModemDevice}

### \[explicit\] ModemDevice::ModemDevice(const QString &*path*, QObject \**parent* = nullptr) {#ModemDevice-1}

### NetworkManager::ModemDevice::Capabilities ModemDevice::currentCapabilities() const {#currentCapabilities}

The generic family of access technologies the modem currently supports without a firmware reload or reinitialization.

### \[signal\] void ModemDevice::currentCapabilitiesChanged(*NetworkManager::ModemDevice::Capabilities*) {#currentCapabilitiesChanged}

This signal is emitted when the capabilities of the device change

### NetworkManager::ModemDevice::Capabilities ModemDevice::modemCapabilities() const {#modemCapabilities}

The generic family of access technologies the modem supports. Not all capabilities are available at the same time however; some modems require a firmware reload or other reinitialization to switch between eg CDMA/EVDO and GSM/UMTS.

### \[override virtual\] NetworkManager::Device::Type ModemDevice::type() const {#type}

Reimplements: [Device::type() const](networkmanager-device.md#type).

Return the type
