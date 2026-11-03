---
title: "NetworkManager::BluetoothSetting Class"
description: "Represents bluetooth setting."
---

# NetworkManager::BluetoothSetting Class

Represents bluetooth setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/BluetoothSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-bluetoothsetting-members.md)

## Public Types

- [BluetoothSetting::List](#List-typedef)
- [enum BluetoothSetting::ProfileType](#ProfileType-enum)
- [BluetoothSetting::Ptr](#Ptr-typedef)

## Public Functions

- [BluetoothSetting()](#BluetoothSetting)
- [BluetoothSetting(const NetworkManager::BluetoothSetting::Ptr &other)](#BluetoothSetting-1)
- [QByteArray bluetoothAddress() const](#bluetoothAddress)
- [NetworkManager::BluetoothSetting::ProfileType profileType() const](#profileType)
- [void setBluetoothAddress(const QByteArray &address)](#setBluetoothAddress)
- [void setProfileType(NetworkManager::BluetoothSetting::ProfileType type)](#setProfileType)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### BluetoothSetting::List {#List-typedef}

### enum BluetoothSetting::ProfileType {#ProfileType-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::BluetoothSetting::Unknown` | `0` |
| `NetworkManager::BluetoothSetting::Dun` | `1` |
| `NetworkManager::BluetoothSetting::Panu` | `2` |

### BluetoothSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### BluetoothSetting::BluetoothSetting() {#BluetoothSetting}

### \[explicit\] BluetoothSetting::BluetoothSetting(const NetworkManager::BluetoothSetting::Ptr &*other*) {#BluetoothSetting-1}

### QByteArray BluetoothSetting::bluetoothAddress() const {#bluetoothAddress}

*See also* [setBluetoothAddress](networkmanager-bluetoothsetting.md#setBluetoothAddress)()

### NetworkManager::BluetoothSetting::ProfileType BluetoothSetting::profileType() const {#profileType}

*See also* [setProfileType](networkmanager-bluetoothsetting.md#setProfileType)()

### void BluetoothSetting::setBluetoothAddress(const QByteArray &*address*) {#setBluetoothAddress}

*See also* [bluetoothAddress](networkmanager-bluetoothsetting.md#bluetoothAddress)()

### void BluetoothSetting::setProfileType(NetworkManager::BluetoothSetting::ProfileType *type*) {#setProfileType}

*See also* [profileType](networkmanager-bluetoothsetting.md#profileType)()
