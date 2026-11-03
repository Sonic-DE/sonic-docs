---
title: "NetworkManager::BluetoothDevice Class"
description: "A bluetooth device interface."
---

# NetworkManager::BluetoothDevice Class

A bluetooth device interface. [More...](#details)

- **Header:** `#include <NetworkManagerQt/BluetoothDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::ModemDevice](networkmanager-modemdevice.md)

[List of all members, including inherited members](networkmanager-bluetoothdevice-members.md)

## Public Types

- [enum BluetoothDevice::Capability](#Capability-enum)
- [BluetoothDevice::List](#List-typedef)
- [BluetoothDevice::Ptr](#Ptr-typedef)

## Properties

- [\[read-only\] bluetoothCapabilities : uint](#bluetoothCapabilities-prop)
- [\[read-only\] hardwareAddress : QString](#hardwareAddress-prop)
- [\[read-only\] name : QString](#name-prop)

## Public Functions

- [BluetoothDevice(const QString &path, QObject \*parent = nullptr)](#BluetoothDevice)
- [~BluetoothDevice()](#dtor.BluetoothDevice)
- [NetworkManager::BluetoothDevice::Capabilities bluetoothCapabilities() const](#bluetoothCapabilities)
- [QString hardwareAddress() const](#hardwareAddress)
- [QString name() const](#name)
- [NetworkManager::Device::Type type() const](#type)

## Signals

- [void nameChanged(const QString &name)](#nameChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum BluetoothDevice::Capability {#Capability-enum}

**flags BluetoothDevice::Capabilities**

Capabilities of the Bluetooth device

| Constant | Value | Description |
| --- | --- | --- |
| `NetworkManager::BluetoothDevice::NoCapability` | `0x0` | No special capability |
| `NetworkManager::BluetoothDevice::Dun` | `0x1` | Dial Up Networking profile |
| `NetworkManager::BluetoothDevice::Pan` | `0x2` | Personal Area Network profile |

The `Capabilities` type is a typedef for `QFlags<Capability>. `It stores an OR combination of `Capability` values.

### BluetoothDevice::List {#List-typedef}

### BluetoothDevice::Ptr {#Ptr-typedef}

## Property Documentation {#property-documentation}

### \[read-only\] bluetoothCapabilities : uint {#bluetoothCapabilities-prop}

**Access functions:**

- `NetworkManager::BluetoothDevice::Capabilities` **[bluetoothCapabilities](networkmanager-bluetoothdevice.md#bluetoothCapabilities)**() const

### \[read-only\] hardwareAddress : QString {#hardwareAddress-prop}

**Access functions:**

- `QString` **[hardwareAddress](networkmanager-bluetoothdevice.md#hardwareAddress)**() const

### \[read-only\] name : QString {#name-prop}

**Access functions:**

- `QString` **[name](networkmanager-bluetoothdevice.md#name)**() const

## Member Function Documentation {#member-function-documentation}

### \[explicit\] BluetoothDevice::BluetoothDevice(const QString &*path*, QObject \**parent* = nullptr) {#BluetoothDevice}

Creates a new [BluetoothDevice](networkmanager-bluetoothdevice.md) object.

### \[override virtual noexcept\] BluetoothDevice::~BluetoothDevice() {#dtor.BluetoothDevice}

Destroys a [BluetoothDevice](networkmanager-bluetoothdevice.md) object.

### NetworkManager::BluetoothDevice::Capabilities BluetoothDevice::bluetoothCapabilities() const {#bluetoothCapabilities}

Retrieves the capabilities supported by this device.

> **Note:** Getter function for property [bluetoothCapabilities](networkmanager-bluetoothdevice.md#bluetoothCapabilities-prop).

*See also* [NetworkManager::BluetoothDevice::Capability](networkmanager-bluetoothdevice.md#Capability-enum)

### QString BluetoothDevice::hardwareAddress() const {#hardwareAddress}

The hardware address assigned to the bluetooth interface

> **Note:** Getter function for property [hardwareAddress](networkmanager-bluetoothdevice.md#hardwareAddress-prop).

### QString BluetoothDevice::name() const {#name}

Name of the bluetooth interface

> **Note:** Getter function for property [name](networkmanager-bluetoothdevice.md#name-prop).

### \[signal\] void BluetoothDevice::nameChanged(const QString &*name*) {#nameChanged}

Emitted when the BT device `name` changes

### \[override virtual\] NetworkManager::Device::Type BluetoothDevice::type() const {#type}

Reimplements: [ModemDevice::type() const](networkmanager-modemdevice.md#type).

The NetworkInterface type.

Returns the [NetworkManager::Device::Type](networkmanager-device.md#Type-enum). This always returns [NetworkManager::Device::Bluetooth](networkmanager-device.md#Type-enum)
