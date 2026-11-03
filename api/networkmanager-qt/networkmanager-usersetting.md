---
title: "NetworkManager::UserSetting Class"
description: "Represents user setting."
---

# NetworkManager::UserSetting Class

Represents user setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/UserSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-usersetting-members.md)

## Public Types

- [UserSetting::List](#List-typedef)
- [UserSetting::Ptr](#Ptr-typedef)

## Public Functions

- [UserSetting()](#UserSetting)
- [UserSetting(const NetworkManager::UserSetting::Ptr &other)](#UserSetting-1)
- [void addData(const QString &data, const QString &value)](#addData)
- [NMStringMap data() const](#data)
- [void setData(const NMStringMap &data)](#setData)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### UserSetting::List {#List-typedef}

### UserSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### UserSetting::UserSetting() {#UserSetting}

### \[explicit\] UserSetting::UserSetting(const NetworkManager::UserSetting::Ptr &*other*) {#UserSetting-1}

### void UserSetting::addData(const QString &*data*, const QString &*value*) {#addData}

### NMStringMap UserSetting::data() const {#data}

*See also* [setData](networkmanager-usersetting.md#setData)()

### void UserSetting::setData(const NMStringMap &*data*) {#setData}

*See also* [data](networkmanager-usersetting.md#data)()
