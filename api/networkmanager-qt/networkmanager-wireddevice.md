---
title: "NetworkManager::WiredDevice Class"
description: "A wired device interface."
---

# NetworkManager::WiredDevice Class

A wired device interface. [More...](#details)

- **Header:** `#include <NetworkManagerQt/WiredDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Device](networkmanager-device.md)

[List of all members, including inherited members](networkmanager-wireddevice-members.md)

## Public Types

- [WiredDevice::List](#List-typedef)
- [WiredDevice::Ptr](#Ptr-typedef)

## Properties

- [\[read-only\] bitRate : int](#bitRate-prop)
- [\[read-only\] carrier : bool](#carrier-prop)
- [\[read-only\] hardwareAddress : QString](#hardwareAddress-prop)
- [\[read-only\] permanentHardwareAddress : QString](#permanentHardwareAddress-prop)
- [\[read-only\] s390SubChannels : QStringList](#s390SubChannels-prop)

## Public Functions

- [WiredDevice(const QString &path, QObject \*parent = nullptr)](#WiredDevice)
- [int bitRate() const](#bitRate)
- [bool carrier() const](#carrier)
- [QString hardwareAddress() const](#hardwareAddress)
- [QString permanentHardwareAddress() const](#permanentHardwareAddress)
- [QStringList s390SubChannels() const](#s390SubChannels)
- [NetworkManager::Device::Type type() const](#type)

## Signals

- [void bitRateChanged(int bitRate)](#bitRateChanged)
- [void carrierChanged(bool plugged)](#carrierChanged)
- [void hardwareAddressChanged(const QString &hwAddress)](#hardwareAddressChanged)
- [void permanentHardwareAddressChanged(const QString &permHwAddress)](#permanentHardwareAddressChanged)
- [void s390SubChannelsChanged(const QStringList &channels)](#s390SubChannelsChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### WiredDevice::List {#List-typedef}

### WiredDevice::Ptr {#Ptr-typedef}

## Property Documentation {#property-documentation}

### \[read-only\] bitRate : int {#bitRate-prop}

**Access functions:**

- `int` **[bitRate](networkmanager-wireddevice.md#bitRate)**() const

**Notifier signal:**

- `void` **[bitRateChanged](networkmanager-wireddevice.md#bitRateChanged)**(`int` *bitRate*)

### \[read-only\] carrier : bool {#carrier-prop}

**Access functions:**

- `bool` **[carrier](networkmanager-wireddevice.md#carrier)**() const

**Notifier signal:**

- `void` **[carrierChanged](networkmanager-wireddevice.md#carrierChanged)**(`bool` *plugged*)

### \[read-only\] hardwareAddress : QString {#hardwareAddress-prop}

**Access functions:**

- `QString` **[hardwareAddress](networkmanager-wireddevice.md#hardwareAddress)**() const

### \[read-only\] permanentHardwareAddress : QString {#permanentHardwareAddress-prop}

**Access functions:**

- `QString` **[permanentHardwareAddress](networkmanager-wireddevice.md#permanentHardwareAddress)**() const

### \[read-only\] s390SubChannels : QStringList {#s390SubChannels-prop}

**Access functions:**

- `QStringList` **[s390SubChannels](networkmanager-wireddevice.md#s390SubChannels)**() const

**Notifier signal:**

- `void` **[s390SubChannelsChanged](networkmanager-wireddevice.md#s390SubChannelsChanged)**(const `QStringList` &*channels*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] WiredDevice::WiredDevice(const QString &*path*, QObject \**parent* = nullptr) {#WiredDevice}

### int WiredDevice::bitRate() const {#bitRate}

Design speed of the device, in megabits/second (Mb/s)

> **Note:** Getter function for property [bitRate](networkmanager-wireddevice.md#bitRate-prop).

### \[signal\] void WiredDevice::bitRateChanged(int *bitRate*) {#bitRateChanged}

Emitted when the design speed of the device has changed

> **Note:** Notifier signal for property [bitRate](networkmanager-wireddevice.md#bitRate-prop).

### bool WiredDevice::carrier() const {#carrier}

Indicates whether the physical carrier is found (e.g. whether a cable is plugged in or not)

> **Note:** Getter function for property [carrier](networkmanager-wireddevice.md#carrier-prop).

### \[signal\] void WiredDevice::carrierChanged(bool *plugged*) {#carrierChanged}

Emitted when the carrier of this device has changed

> **Note:** Notifier signal for property [carrier](networkmanager-wireddevice.md#carrier-prop).

### QString WiredDevice::hardwareAddress() const {#hardwareAddress}

Active hardware address of the device

> **Note:** Getter function for property [hardwareAddress](networkmanager-wireddevice.md#hardwareAddress-prop).

### \[signal\] void WiredDevice::hardwareAddressChanged(const QString &*hwAddress*) {#hardwareAddressChanged}

Emitted when the hardware address of this device has changed

### QString WiredDevice::permanentHardwareAddress() const {#permanentHardwareAddress}

Permanent hardware address of the device

> **Note:** Getter function for property [permanentHardwareAddress](networkmanager-wireddevice.md#permanentHardwareAddress-prop).

### \[signal\] void WiredDevice::permanentHardwareAddressChanged(const QString &*permHwAddress*) {#permanentHardwareAddressChanged}

Emitted when the permanent hardware address of this device has changed

### QStringList WiredDevice::s390SubChannels() const {#s390SubChannels}

Array of S/390 subchannels for S/390 or z/Architecture devices

> **Note:** Getter function for property [s390SubChannels](networkmanager-wireddevice.md#s390SubChannels-prop).

### \[signal\] void WiredDevice::s390SubChannelsChanged(const QStringList &*channels*) {#s390SubChannelsChanged}

Emitted when the array of [s390SubChannels](networkmanager-wireddevice.md#s390SubChannels) has changed

> **Note:** Notifier signal for property [s390SubChannels](networkmanager-wireddevice.md#s390SubChannels-prop).

### \[override virtual\] NetworkManager::Device::Type WiredDevice::type() const {#type}

Reimplements: [Device::type() const](networkmanager-device.md#type).

Return the type
