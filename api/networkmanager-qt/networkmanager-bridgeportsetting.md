---
title: "NetworkManager::BridgePortSetting Class"
description: "Represents bridge port setting."
---

# NetworkManager::BridgePortSetting Class

Represents bridge port setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/BridgePortSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-bridgeportsetting-members.md)

## Public Types

- [BridgePortSetting::List](#List-typedef)
- [BridgePortSetting::Ptr](#Ptr-typedef)

## Public Functions

- [BridgePortSetting()](#BridgePortSetting)
- [BridgePortSetting(const NetworkManager::BridgePortSetting::Ptr &other)](#BridgePortSetting-1)
- [bool hairpinMode() const](#hairpinMode)
- [quint32 pathCost() const](#pathCost)
- [quint32 priority() const](#priority)
- [void setHairpinMode(bool enable)](#setHairpinMode)
- [void setPathCost(quint32 cost)](#setPathCost)
- [void setPriority(quint32 priority)](#setPriority)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### BridgePortSetting::List {#List-typedef}

### BridgePortSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### BridgePortSetting::BridgePortSetting() {#BridgePortSetting}

### \[explicit\] BridgePortSetting::BridgePortSetting(const NetworkManager::BridgePortSetting::Ptr &*other*) {#BridgePortSetting-1}

### bool BridgePortSetting::hairpinMode() const {#hairpinMode}

*See also* [setHairpinMode](networkmanager-bridgeportsetting.md#setHairpinMode)()

### quint32 BridgePortSetting::pathCost() const {#pathCost}

*See also* [setPathCost](networkmanager-bridgeportsetting.md#setPathCost)()

### quint32 BridgePortSetting::priority() const {#priority}

*See also* [setPriority](networkmanager-bridgeportsetting.md#setPriority)()

### void BridgePortSetting::setHairpinMode(bool *enable*) {#setHairpinMode}

*See also* [hairpinMode](networkmanager-bridgeportsetting.md#hairpinMode)()

### void BridgePortSetting::setPathCost(quint32 *cost*) {#setPathCost}

*See also* [pathCost](networkmanager-bridgeportsetting.md#pathCost)()

### void BridgePortSetting::setPriority(quint32 *priority*) {#setPriority}

*See also* [priority](networkmanager-bridgeportsetting.md#priority)()
