---
title: "NetworkManager::TunSetting Class"
description: "Represents generic setting."
---

# NetworkManager::TunSetting Class

Represents generic setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/TunSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-tunsetting-members.md)

## Public Types

- [TunSetting::List](#List-typedef)
- [enum TunSetting::Mode](#Mode-enum)
- [TunSetting::Ptr](#Ptr-typedef)

## Public Functions

- [TunSetting()](#TunSetting)
- [TunSetting(const NetworkManager::TunSetting::Ptr &other)](#TunSetting-1)
- [QString group() const](#group)
- [NetworkManager::TunSetting::Mode mode() const](#mode)
- [bool multiQueue() const](#multiQueue)
- [QString owner() const](#owner)
- [bool pi() const](#pi)
- [void setGroup(const QString &group)](#setGroup)
- [void setMode(NetworkManager::TunSetting::Mode mode)](#setMode)
- [void setMultiQueue(bool multiQueue)](#setMultiQueue)
- [void setOwner(const QString &owner)](#setOwner)
- [void setPi(bool pi)](#setPi)
- [void setVnetHdr(bool vnetHdr)](#setVnetHdr)
- [bool vnetHdr() const](#vnetHdr)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### TunSetting::List {#List-typedef}

### enum TunSetting::Mode {#Mode-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::TunSetting::Tun` | `0` |
| `NetworkManager::TunSetting::Tap` | `1` |

### TunSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### TunSetting::TunSetting() {#TunSetting}

### \[explicit\] TunSetting::TunSetting(const NetworkManager::TunSetting::Ptr &*other*) {#TunSetting-1}

### QString TunSetting::group() const {#group}

*See also* [setGroup](networkmanager-tunsetting.md#setGroup)()

### NetworkManager::TunSetting::Mode TunSetting::mode() const {#mode}

*See also* [setMode](networkmanager-tunsetting.md#setMode)()

### bool TunSetting::multiQueue() const {#multiQueue}

*See also* [setMultiQueue](networkmanager-tunsetting.md#setMultiQueue)()

### QString TunSetting::owner() const {#owner}

*See also* [setOwner](networkmanager-tunsetting.md#setOwner)()

### bool TunSetting::pi() const {#pi}

*See also* [setPi](networkmanager-tunsetting.md#setPi)()

### void TunSetting::setGroup(const QString &*group*) {#setGroup}

*See also* [group](networkmanager-tunsetting.md#group)()

### void TunSetting::setMode(NetworkManager::TunSetting::Mode *mode*) {#setMode}

*See also* [mode](networkmanager-tunsetting.md#mode)()

### void TunSetting::setMultiQueue(bool *multiQueue*) {#setMultiQueue}

*See also* [multiQueue](networkmanager-tunsetting.md#multiQueue)()

### void TunSetting::setOwner(const QString &*owner*) {#setOwner}

*See also* [owner](networkmanager-tunsetting.md#owner)()

### void TunSetting::setPi(bool *pi*) {#setPi}

*See also* [pi](networkmanager-tunsetting.md#pi)()

### void TunSetting::setVnetHdr(bool *vnetHdr*) {#setVnetHdr}

*See also* [vnetHdr](networkmanager-tunsetting.md#vnetHdr)()

### bool TunSetting::vnetHdr() const {#vnetHdr}

*See also* [setVnetHdr](networkmanager-tunsetting.md#setVnetHdr)()
