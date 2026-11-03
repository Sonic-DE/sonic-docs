---
title: "NetworkManager::InfinibandSetting Class"
description: "Represents infiniband setting."
---

# NetworkManager::InfinibandSetting Class

Represents infiniband setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/InfinibandSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-infinibandsetting-members.md)

## Public Types

- [InfinibandSetting::List](#List-typedef)
- [InfinibandSetting::Ptr](#Ptr-typedef)
- [enum InfinibandSetting::TransportMode](#TransportMode-enum)

## Public Functions

- [InfinibandSetting()](#InfinibandSetting)
- [InfinibandSetting(const NetworkManager::InfinibandSetting::Ptr &other)](#InfinibandSetting-1)
- [QByteArray macAddress() const](#macAddress)
- [quint32 mtu() const](#mtu)
- [qint32 pKey() const](#pKey)
- [QString parent() const](#parent)
- [void setMacAddress(const QByteArray &address)](#setMacAddress)
- [void setMtu(quint32 mtu)](#setMtu)
- [void setPKey(qint32 key)](#setPKey)
- [void setParent(const QString &parent)](#setParent)
- [void setTransportMode(NetworkManager::InfinibandSetting::TransportMode mode)](#setTransportMode)
- [NetworkManager::InfinibandSetting::TransportMode transportMode() const](#transportMode)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### InfinibandSetting::List {#List-typedef}

### InfinibandSetting::Ptr {#Ptr-typedef}

### enum InfinibandSetting::TransportMode {#TransportMode-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::InfinibandSetting::Unknown` | `0` |
| `NetworkManager::InfinibandSetting::Datagram` | `1` |
| `NetworkManager::InfinibandSetting::Connected` | `2` |

## Member Function Documentation {#member-function-documentation}

### InfinibandSetting::InfinibandSetting() {#InfinibandSetting}

### \[explicit\] InfinibandSetting::InfinibandSetting(const NetworkManager::InfinibandSetting::Ptr &*other*) {#InfinibandSetting-1}

### QByteArray InfinibandSetting::macAddress() const {#macAddress}

*See also* [setMacAddress](networkmanager-infinibandsetting.md#setMacAddress)()

### quint32 InfinibandSetting::mtu() const {#mtu}

*See also* [setMtu](networkmanager-infinibandsetting.md#setMtu)()

### qint32 InfinibandSetting::pKey() const {#pKey}

*See also* [setPKey](networkmanager-infinibandsetting.md#setPKey)()

### QString InfinibandSetting::parent() const {#parent}

*See also* [setParent](networkmanager-infinibandsetting.md#setParent)()

### void InfinibandSetting::setMacAddress(const QByteArray &*address*) {#setMacAddress}

*See also* [macAddress](networkmanager-infinibandsetting.md#macAddress)()

### void InfinibandSetting::setMtu(quint32 *mtu*) {#setMtu}

*See also* [mtu](networkmanager-infinibandsetting.md#mtu)()

### void InfinibandSetting::setPKey(qint32 *key*) {#setPKey}

*See also* [pKey](networkmanager-infinibandsetting.md#pKey)()

### void InfinibandSetting::setParent(const QString &*parent*) {#setParent}

*See also* [parent](networkmanager-infinibandsetting.md#parent)()

### void InfinibandSetting::setTransportMode(NetworkManager::InfinibandSetting::TransportMode *mode*) {#setTransportMode}

*See also* [transportMode](networkmanager-infinibandsetting.md#transportMode)()

### NetworkManager::InfinibandSetting::TransportMode InfinibandSetting::transportMode() const {#transportMode}

*See also* [setTransportMode](networkmanager-infinibandsetting.md#setTransportMode)()
