---
title: "NetworkManager::VpnSetting Class"
description: "Represents vpn setting."
---

# NetworkManager::VpnSetting Class

Represents vpn setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/VpnSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-vpnsetting-members.md)

## Public Types

- [VpnSetting::List](#List-typedef)
- [VpnSetting::Ptr](#Ptr-typedef)

## Public Functions

- [VpnSetting()](#VpnSetting)
- [VpnSetting(const NetworkManager::VpnSetting::Ptr &other)](#VpnSetting-1)
- [NMStringMap data() const](#data)
- [bool persistent() const](#persistent)
- [NMStringMap secrets() const](#secrets)
- [QString serviceType() const](#serviceType)
- [void setData(const NMStringMap &data)](#setData)
- [void setPersistent(bool persistent)](#setPersistent)
- [void setSecrets(const NMStringMap &secrets)](#setSecrets)
- [void setServiceType(const QString &type)](#setServiceType)
- [void setTimeout(uint timeout)](#setTimeout)
- [void setUsername(const QString &username)](#setUsername)
- [uint timeout() const](#timeout)
- [QString username() const](#username)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### VpnSetting::List {#List-typedef}

### VpnSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### VpnSetting::VpnSetting() {#VpnSetting}

### \[explicit\] VpnSetting::VpnSetting(const NetworkManager::VpnSetting::Ptr &*other*) {#VpnSetting-1}

### NMStringMap VpnSetting::data() const {#data}

*See also* [setData](networkmanager-vpnsetting.md#setData)()

### bool VpnSetting::persistent() const {#persistent}

*See also* [setPersistent](networkmanager-vpnsetting.md#setPersistent)()

### NMStringMap VpnSetting::secrets() const {#secrets}

*See also* [setSecrets](networkmanager-vpnsetting.md#setSecrets)()

### QString VpnSetting::serviceType() const {#serviceType}

*See also* [setServiceType](networkmanager-vpnsetting.md#setServiceType)()

### void VpnSetting::setData(const NMStringMap &*data*) {#setData}

*See also* [data](networkmanager-vpnsetting.md#data)()

### void VpnSetting::setPersistent(bool *persistent*) {#setPersistent}

*See also* [persistent](networkmanager-vpnsetting.md#persistent)()

### void VpnSetting::setSecrets(const NMStringMap &*secrets*) {#setSecrets}

*See also* [secrets](networkmanager-vpnsetting.md#secrets)()

### void VpnSetting::setServiceType(const QString &*type*) {#setServiceType}

*See also* [serviceType](networkmanager-vpnsetting.md#serviceType)()

### void VpnSetting::setTimeout(uint *timeout*) {#setTimeout}

*See also* [timeout](networkmanager-vpnsetting.md#timeout)()

### void VpnSetting::setUsername(const QString &*username*) {#setUsername}

*See also* [username](networkmanager-vpnsetting.md#username)()

### uint VpnSetting::timeout() const {#timeout}

*See also* [setTimeout](networkmanager-vpnsetting.md#setTimeout)()

### QString VpnSetting::username() const {#username}

*See also* [setUsername](networkmanager-vpnsetting.md#setUsername)()
