---
title: "NetworkManager::AdslSetting Class"
description: "Represents adsl setting."
---

# NetworkManager::AdslSetting Class

Represents adsl setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/AdslSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-adslsetting-members.md)

## Public Types

- [enum AdslSetting::Encapsulation](#Encapsulation-enum)
- [AdslSetting::List](#List-typedef)
- [enum AdslSetting::Protocol](#Protocol-enum)
- [AdslSetting::Ptr](#Ptr-typedef)

## Public Functions

- [AdslSetting()](#AdslSetting)
- [AdslSetting(const NetworkManager::AdslSetting::Ptr &other)](#AdslSetting-1)
- [NetworkManager::AdslSetting::Encapsulation encapsulation() const](#encapsulation)
- [QString password() const](#password)
- [NetworkManager::Setting::SecretFlags passwordFlags() const](#passwordFlags)
- [NetworkManager::AdslSetting::Protocol protocol() const](#protocol)
- [void setEncapsulation(NetworkManager::AdslSetting::Encapsulation encapsulation)](#setEncapsulation)
- [void setPassword(const QString &password)](#setPassword)
- [void setPasswordFlags(NetworkManager::Setting::SecretFlags flags)](#setPasswordFlags)
- [void setProtocol(NetworkManager::AdslSetting::Protocol protocol)](#setProtocol)
- [void setUsername(const QString &username)](#setUsername)
- [void setVci(quint32 vci)](#setVci)
- [void setVpi(quint32 vpi)](#setVpi)
- [QString username() const](#username)
- [quint32 vci() const](#vci)
- [quint32 vpi() const](#vpi)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum AdslSetting::Encapsulation {#Encapsulation-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::AdslSetting::UnknownEncapsulation` | `0` |
| `NetworkManager::AdslSetting::Vcmux` | `1` |
| `NetworkManager::AdslSetting::Llc` | `2` |

### AdslSetting::List {#List-typedef}

### enum AdslSetting::Protocol {#Protocol-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::AdslSetting::UnknownProtocol` | `0` |
| `NetworkManager::AdslSetting::Pppoa` | `1` |
| `NetworkManager::AdslSetting::Pppoe` | `2` |
| `NetworkManager::AdslSetting::Ipoatm` | `3` |

### AdslSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### AdslSetting::AdslSetting() {#AdslSetting}

### \[explicit\] AdslSetting::AdslSetting(const NetworkManager::AdslSetting::Ptr &*other*) {#AdslSetting-1}

### NetworkManager::AdslSetting::Encapsulation AdslSetting::encapsulation() const {#encapsulation}

*See also* [setEncapsulation](networkmanager-adslsetting.md#setEncapsulation)()

### QString AdslSetting::password() const {#password}

*See also* [setPassword](networkmanager-adslsetting.md#setPassword)()

### NetworkManager::Setting::SecretFlags AdslSetting::passwordFlags() const {#passwordFlags}

*See also* [setPasswordFlags](networkmanager-adslsetting.md#setPasswordFlags)()

### NetworkManager::AdslSetting::Protocol AdslSetting::protocol() const {#protocol}

*See also* [setProtocol](networkmanager-adslsetting.md#setProtocol)()

### void AdslSetting::setEncapsulation(NetworkManager::AdslSetting::Encapsulation *encapsulation*) {#setEncapsulation}

*See also* [encapsulation](networkmanager-adslsetting.md#encapsulation)()

### void AdslSetting::setPassword(const QString &*password*) {#setPassword}

*See also* [password](networkmanager-adslsetting.md#password)()

### void AdslSetting::setPasswordFlags(NetworkManager::Setting::SecretFlags *flags*) {#setPasswordFlags}

*See also* [passwordFlags](networkmanager-adslsetting.md#passwordFlags)()

### void AdslSetting::setProtocol(NetworkManager::AdslSetting::Protocol *protocol*) {#setProtocol}

*See also* [protocol](networkmanager-adslsetting.md#protocol)()

### void AdslSetting::setUsername(const QString &*username*) {#setUsername}

*See also* [username](networkmanager-adslsetting.md#username)()

### void AdslSetting::setVci(quint32 *vci*) {#setVci}

*See also* [vci](networkmanager-adslsetting.md#vci)()

### void AdslSetting::setVpi(quint32 *vpi*) {#setVpi}

*See also* [vpi](networkmanager-adslsetting.md#vpi)()

### QString AdslSetting::username() const {#username}

*See also* [setUsername](networkmanager-adslsetting.md#setUsername)()

### quint32 AdslSetting::vci() const {#vci}

*See also* [setVci](networkmanager-adslsetting.md#setVci)()

### quint32 AdslSetting::vpi() const {#vpi}

*See also* [setVpi](networkmanager-adslsetting.md#setVpi)()

## Member Variable Documentation {#member-variable-documentation}

### NetworkManager::AdslSettingPrivate \* AdslSetting::d\_ptr {#d_ptr-var}
