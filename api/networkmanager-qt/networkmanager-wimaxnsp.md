---
title: "NetworkManager::WimaxNsp Class"
description: "Wimax network service provider (access point)."
---

# NetworkManager::WimaxNsp Class

Wimax network service provider (access point). [More...](#details)

- **Header:** `#include <NetworkManagerQt/WimaxNsp>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](networkmanager-wimaxnsp-members.md)

## Public Types

- [WimaxNsp::List](#List-typedef)
- [enum WimaxNsp::NetworkType](#NetworkType-enum)
- [WimaxNsp::Ptr](#Ptr-typedef)

## Public Functions

- [WimaxNsp(const QString &path, QObject \*parent = nullptr)](#WimaxNsp)
- [QString name() const](#name)
- [NetworkManager::WimaxNsp::NetworkType networkType() const](#networkType)
- [uint signalQuality() const](#signalQuality)
- [QString uni() const](#uni)

## Signals

- [void nameChanged(const QString &name)](#nameChanged)
- [void networkTypeChanged(NetworkManager::WimaxNsp::NetworkType type)](#networkTypeChanged)
- [void signalQualityChanged(uint quality)](#signalQualityChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### WimaxNsp::List {#List-typedef}

### enum WimaxNsp::NetworkType {#NetworkType-enum}

network types a NSP can have

| Constant |   |
| --- | --- |
| `NetworkManager::WimaxNsp::Unknown` | `0x1` |
| `NetworkManager::WimaxNsp::Home` | `0x2` |
| `NetworkManager::WimaxNsp::Partner` | `0x3` |
| `NetworkManager::WimaxNsp::RoamingPartner` | `0x4` |

### WimaxNsp::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] WimaxNsp::WimaxNsp(const QString &*path*, QObject \**parent* = nullptr) {#WimaxNsp}

### QString WimaxNsp::name() const {#name}

The name of the NSP

### \[signal\] void WimaxNsp::nameChanged(const QString &*name*) {#nameChanged}

This signal is emitted when the name of this NSP has changed

`name` the new name for this NSP

### NetworkManager::WimaxNsp::NetworkType WimaxNsp::networkType() const {#networkType}

The network type of the NSP

### \[signal\] void WimaxNsp::networkTypeChanged(NetworkManager::WimaxNsp::NetworkType *type*) {#networkTypeChanged}

This signal is emitted when the network type of this NSP has changed.

`type` the new type

### uint WimaxNsp::signalQuality() const {#signalQuality}

The current signal quality of the NSP, in percent

### \[signal\] void WimaxNsp::signalQualityChanged(uint *quality*) {#signalQualityChanged}

This signal is emitted when the signal quality of this NSP has changed.

`quality` the new quality

### QString WimaxNsp::uni() const {#uni}
