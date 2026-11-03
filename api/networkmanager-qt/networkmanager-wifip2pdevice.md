---
title: "NetworkManager::WifiP2PDevice Class"
description: "WiFi P2P device. This class was introduced in Qt 6.20."
---

# NetworkManager::WifiP2PDevice Class

[WiFi](networkmanager.md#LogDomain-enum) P2P device. This class was introduced in Qt 6.20. [More...](#details)

- **Header:** `#include <NetworkManagerQt/WifiP2PDevice>`
- **Since:** Qt 6.20
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Device](networkmanager-device.md)

[List of all members, including inherited members](networkmanager-wifip2pdevice-members.md)

## Public Types

- [\[alias\] WifiP2PDevice::Ptr](#Ptr-typedef)

## Properties

- [\[read-only\] hardwareAddress : QString](#hardwareAddress-prop)
- [\[read-only\] peers : QStringList](#peers-prop)

## Public Functions

- [WifiP2PDevice(const QString &path, QObject \*parent = nullptr)](#WifiP2PDevice)
- [WifiP2PPeer::Ptr findPeer(const QString &uni)](#findPeer)
- [NetworkManager::Device::Type type() const](#type)

## Public Slots

- [QDBusPendingReply\<\> startFind(const QVariantMap &options = {})](#startFind)
- [QDBusPendingReply\<\> stopFind()](#stopFind)

## Signals

- [void peerAppeared(const QString &peer)](#peerAppeared)
- [void peerDisappeared(const QString &peer)](#peerDisappeared)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### \[alias\] WifiP2PDevice::Ptr {#Ptr-typedef}

## Property Documentation {#property-documentation}

### \[read-only\] hardwareAddress : QString {#hardwareAddress-prop}

**Access functions:**

- `QString` **hardwareAddress**() const

**Notifier signal:**

- `void` **hardwareAddressChanged**(const `QString` &*hardwareAddress*)

### \[read-only\] peers : QStringList {#peers-prop}

**Access functions:**

- `QStringList` **peers**() const

**Notifier signal:**

- `void` **peersChanged**(const `QStringList` &*peers*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] WifiP2PDevice::WifiP2PDevice(const QString &*path*, QObject \**parent* = nullptr) {#WifiP2PDevice}

### \[invokable\] WifiP2PPeer::Ptr WifiP2PDevice::findPeer(const QString &*uni*) {#findPeer}

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[signal\] void WifiP2PDevice::peerAppeared(const QString &*peer*) {#peerAppeared}

### \[signal\] void WifiP2PDevice::peerDisappeared(const QString &*peer*) {#peerDisappeared}

### \[slot\] QDBusPendingReply\<\> WifiP2PDevice::startFind(const QVariantMap &*options* = {}) {#startFind}

### \[slot\] QDBusPendingReply\<\> WifiP2PDevice::stopFind() {#stopFind}

### \[override virtual\] NetworkManager::Device::Type WifiP2PDevice::type() const {#type}

Reimplements: [Device::type() const](networkmanager-device.md#type).
