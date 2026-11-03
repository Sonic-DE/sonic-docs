---
title: "NetworkManager::WimaxSetting Class"
description: "Represents wimax setting."
---

# NetworkManager::WimaxSetting Class

Represents wimax setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/WimaxSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-wimaxsetting-members.md)

## Public Functions

- [WimaxSetting()](#WimaxSetting)
- [WimaxSetting(const NetworkManager::WimaxSetting::Ptr &other)](#WimaxSetting-1)
- [QByteArray macAddress() const](#macAddress)
- [QString networkName() const](#networkName)
- [void setMacAddress(const QByteArray &address)](#setMacAddress)
- [void setNetworkName(const QString &name)](#setNetworkName)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### WimaxSetting::WimaxSetting() {#WimaxSetting}

### \[explicit\] WimaxSetting::WimaxSetting(const NetworkManager::WimaxSetting::Ptr &*other*) {#WimaxSetting-1}

### QByteArray WimaxSetting::macAddress() const {#macAddress}

*See also* [setMacAddress](networkmanager-wimaxsetting.md#setMacAddress)()

### QString WimaxSetting::networkName() const {#networkName}

*See also* [setNetworkName](networkmanager-wimaxsetting.md#setNetworkName)()

### void WimaxSetting::setMacAddress(const QByteArray &*address*) {#setMacAddress}

*See also* [macAddress](networkmanager-wimaxsetting.md#macAddress)()

### void WimaxSetting::setNetworkName(const QString &*name*) {#setNetworkName}

*See also* [networkName](networkmanager-wimaxsetting.md#networkName)()
