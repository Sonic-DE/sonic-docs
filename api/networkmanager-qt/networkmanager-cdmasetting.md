---
title: "NetworkManager::CdmaSetting Class"
description: "Represents cdma setting."
---

# NetworkManager::CdmaSetting Class

Represents cdma setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/CdmaSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-cdmasetting-members.md)

## Public Types

- [CdmaSetting::List](#List-typedef)
- [CdmaSetting::Ptr](#Ptr-typedef)

## Public Functions

- [CdmaSetting()](#CdmaSetting)
- [CdmaSetting(const NetworkManager::CdmaSetting::Ptr &other)](#CdmaSetting-1)
- [QString number() const](#number)
- [QString password() const](#password)
- [NetworkManager::Setting::SecretFlags passwordFlags() const](#passwordFlags)
- [void setNumber(const QString &number)](#setNumber)
- [void setPassword(const QString &password)](#setPassword)
- [void setPasswordFlags(NetworkManager::Setting::SecretFlags flags)](#setPasswordFlags)
- [void setUsername(const QString &username)](#setUsername)
- [QString username() const](#username)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### CdmaSetting::List {#List-typedef}

### CdmaSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### CdmaSetting::CdmaSetting() {#CdmaSetting}

### \[explicit\] CdmaSetting::CdmaSetting(const NetworkManager::CdmaSetting::Ptr &*other*) {#CdmaSetting-1}

### QString CdmaSetting::number() const {#number}

*See also* [setNumber](networkmanager-cdmasetting.md#setNumber)()

### QString CdmaSetting::password() const {#password}

*See also* [setPassword](networkmanager-cdmasetting.md#setPassword)()

### NetworkManager::Setting::SecretFlags CdmaSetting::passwordFlags() const {#passwordFlags}

*See also* [setPasswordFlags](networkmanager-cdmasetting.md#setPasswordFlags)()

### void CdmaSetting::setNumber(const QString &*number*) {#setNumber}

*See also* [number](networkmanager-cdmasetting.md#number)()

### void CdmaSetting::setPassword(const QString &*password*) {#setPassword}

*See also* [password](networkmanager-cdmasetting.md#password)()

### void CdmaSetting::setPasswordFlags(NetworkManager::Setting::SecretFlags *flags*) {#setPasswordFlags}

*See also* [passwordFlags](networkmanager-cdmasetting.md#passwordFlags)()

### void CdmaSetting::setUsername(const QString &*username*) {#setUsername}

*See also* [username](networkmanager-cdmasetting.md#username)()

### QString CdmaSetting::username() const {#username}

*See also* [setUsername](networkmanager-cdmasetting.md#setUsername)()
