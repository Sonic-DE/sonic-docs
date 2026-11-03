---
title: "NetworkManager::ProxySetting Class"
description: "Represents proxy setting."
---

# NetworkManager::ProxySetting Class

Represents proxy setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/ProxySetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-proxysetting-members.md)

## Public Types

- [ProxySetting::List](#List-typedef)
- [enum ProxySetting::Mode](#Mode-enum)
- [ProxySetting::Ptr](#Ptr-typedef)

## Public Functions

- [ProxySetting()](#ProxySetting)
- [ProxySetting(const NetworkManager::ProxySetting::Ptr &other)](#ProxySetting-1)
- [bool browserOnly() const](#browserOnly)
- [NetworkManager::ProxySetting::Mode method() const](#method)
- [QString pacScript() const](#pacScript)
- [QString pacUrl() const](#pacUrl)
- [void setBrowserOnly(bool browserOnly)](#setBrowserOnly)
- [void setMethod(NetworkManager::ProxySetting::Mode method)](#setMethod)
- [void setPacScript(const QString &script)](#setPacScript)
- [void setPacUrl(const QString &url)](#setPacUrl)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### ProxySetting::List {#List-typedef}

### enum ProxySetting::Mode {#Mode-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::ProxySetting::None` | `0` |
| `NetworkManager::ProxySetting::Auto` | `1` |

### ProxySetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### ProxySetting::ProxySetting() {#ProxySetting}

### \[explicit\] ProxySetting::ProxySetting(const NetworkManager::ProxySetting::Ptr &*other*) {#ProxySetting-1}

### bool ProxySetting::browserOnly() const {#browserOnly}

*See also* [setBrowserOnly](networkmanager-proxysetting.md#setBrowserOnly)()

### NetworkManager::ProxySetting::Mode ProxySetting::method() const {#method}

*See also* [setMethod](networkmanager-proxysetting.md#setMethod)()

### QString ProxySetting::pacScript() const {#pacScript}

*See also* [setPacScript](networkmanager-proxysetting.md#setPacScript)()

### QString ProxySetting::pacUrl() const {#pacUrl}

*See also* [setPacUrl](networkmanager-proxysetting.md#setPacUrl)()

### void ProxySetting::setBrowserOnly(bool *browserOnly*) {#setBrowserOnly}

*See also* [browserOnly](networkmanager-proxysetting.md#browserOnly)()

### void ProxySetting::setMethod(NetworkManager::ProxySetting::Mode *method*) {#setMethod}

*See also* [method](networkmanager-proxysetting.md#method)()

### void ProxySetting::setPacScript(const QString &*script*) {#setPacScript}

*See also* [pacScript](networkmanager-proxysetting.md#pacScript)()

### void ProxySetting::setPacUrl(const QString &*url*) {#setPacUrl}

*See also* [pacUrl](networkmanager-proxysetting.md#pacUrl)()
