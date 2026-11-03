---
title: "NetworkManager::TeamSetting Class"
description: "Represents team setting."
---

# NetworkManager::TeamSetting Class

Represents team setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/TeamSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-teamsetting-members.md)  
[Deprecated members](networkmanager-teamsetting-obsolete.md)

## Public Types

- [TeamSetting::List](#List-typedef)
- [TeamSetting::Ptr](#Ptr-typedef)

## Public Functions

- [TeamSetting()](#TeamSetting)
- [TeamSetting(const NetworkManager::TeamSetting::Ptr &other)](#TeamSetting-1)
- [QString config() const](#config)
- [QString interfaceName() const](#interfaceName)
- [void setConfig(const QString &config)](#setConfig)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### TeamSetting::List {#List-typedef}

### TeamSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### TeamSetting::TeamSetting() {#TeamSetting}

### \[explicit\] TeamSetting::TeamSetting(const NetworkManager::TeamSetting::Ptr &*other*) {#TeamSetting-1}

### QString TeamSetting::config() const {#config}

*See also* [setConfig](networkmanager-teamsetting.md#setConfig)()

### QString TeamSetting::interfaceName() const {#interfaceName}

### void TeamSetting::setConfig(const QString &*config*) {#setConfig}

*See also* [config](networkmanager-teamsetting.md#config)()
