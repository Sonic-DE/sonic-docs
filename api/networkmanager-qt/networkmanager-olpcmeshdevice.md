---
title: "NetworkManager::OlpcMeshDevice Class"
description: "A OLPC mesh interface."
---

# NetworkManager::OlpcMeshDevice Class

A OLPC mesh interface. [More...](#details)

- **Header:** `#include <NetworkManagerQt/OlpcMeshDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Device](networkmanager-device.md)

[List of all members, including inherited members](networkmanager-olpcmeshdevice-members.md)

## Public Types

- [OlpcMeshDevice::List](#List-typedef)
- [OlpcMeshDevice::Ptr](#Ptr-typedef)

## Public Functions

- [OlpcMeshDevice(const QString &path, QObject \*parent = nullptr)](#OlpcMeshDevice)
- [~OlpcMeshDevice()](#dtor.OlpcMeshDevice)
- [uint activeChannel() const](#activeChannel)
- [Device::Ptr companionDevice() const](#companionDevice)
- [QString hardwareAddress() const](#hardwareAddress)
- [NetworkManager::Device::Type type() const](#type)

## Signals

- [void activeChannelChanged(uint)](#activeChannelChanged)
- [void companionChanged(const Device::Ptr &device)](#companionChanged)
- [void hardwareAddressChanged(const QString &)](#hardwareAddressChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### OlpcMeshDevice::List {#List-typedef}

### OlpcMeshDevice::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] OlpcMeshDevice::OlpcMeshDevice(const QString &*path*, QObject \**parent* = nullptr) {#OlpcMeshDevice}

Creates a new [OlpcMeshDevice](networkmanager-olpcmeshdevice.md) object.

`path` the DBus path of the device

### \[override virtual noexcept\] OlpcMeshDevice::~OlpcMeshDevice() {#dtor.OlpcMeshDevice}

Destroys a [OlpcMeshDevice](networkmanager-olpcmeshdevice.md) object.

### uint OlpcMeshDevice::activeChannel() const {#activeChannel}

Currently active channel.

### \[signal\] void OlpcMeshDevice::activeChannelChanged(*uint*) {#activeChannelChanged}

The active channel changed.

### \[signal\] void OlpcMeshDevice::companionChanged(const Device::Ptr &*device*) {#companionChanged}

The companion changed.

### Device::Ptr OlpcMeshDevice::companionDevice() const {#companionDevice}

The current companion device.

### QString OlpcMeshDevice::hardwareAddress() const {#hardwareAddress}

The hardware address currently used by the network interface

### \[signal\] void OlpcMeshDevice::hardwareAddressChanged(*const QString &*) {#hardwareAddressChanged}

The device changed its hardware address

### \[override virtual\] NetworkManager::Device::Type OlpcMeshDevice::type() const {#type}

Reimplements: [Device::type() const](networkmanager-device.md#type).

Return the type
