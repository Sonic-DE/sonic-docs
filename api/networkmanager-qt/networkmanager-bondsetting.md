---
title: "NetworkManager::BondSetting Class"
description: "Represents bond setting."
---

# NetworkManager::BondSetting Class

Represents bond setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/BondSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-bondsetting-members.md)  
[Deprecated members](networkmanager-bondsetting-obsolete.md)

## Public Types

- [BondSetting::List](#List-typedef)
- [BondSetting::Ptr](#Ptr-typedef)

## Public Functions

- [BondSetting()](#BondSetting)
- [BondSetting(const NetworkManager::BondSetting::Ptr &other)](#BondSetting-1)
- [void addOption(const QString &option, const QString &value)](#addOption)
- [QString interfaceName() const](#interfaceName)
- [NMStringMap options() const](#options)
- [void setOptions(const NMStringMap &options)](#setOptions)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### BondSetting::List {#List-typedef}

### BondSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### BondSetting::BondSetting() {#BondSetting}

### \[explicit\] BondSetting::BondSetting(const NetworkManager::BondSetting::Ptr &*other*) {#BondSetting-1}

### void BondSetting::addOption(const QString &*option*, const QString &*value*) {#addOption}

### QString BondSetting::interfaceName() const {#interfaceName}

### NMStringMap BondSetting::options() const {#options}

*See also* [setOptions](networkmanager-bondsetting.md#setOptions)()

### void BondSetting::setOptions(const NMStringMap &*options*) {#setOptions}

*See also* [options](networkmanager-bondsetting.md#options)()
