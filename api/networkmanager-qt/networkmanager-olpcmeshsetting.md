---
title: "NetworkManager::OlpcMeshSetting Class"
description: "Represents olpc mesh setting."
---

# NetworkManager::OlpcMeshSetting Class

Represents olpc mesh setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/OlpcMeshSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-olpcmeshsetting-members.md)

## Public Types

- [OlpcMeshSetting::List](#List-typedef)
- [OlpcMeshSetting::Ptr](#Ptr-typedef)

## Public Functions

- [OlpcMeshSetting()](#OlpcMeshSetting)
- [OlpcMeshSetting(const NetworkManager::OlpcMeshSetting::Ptr &other)](#OlpcMeshSetting-1)
- [quint32 channel() const](#channel)
- [QByteArray dhcpAnycastAddress() const](#dhcpAnycastAddress)
- [void setChannel(quint32 channel)](#setChannel)
- [void setDhcpAnycastAddress(const QByteArray &address)](#setDhcpAnycastAddress)
- [void setSsid(const QByteArray &ssid)](#setSsid)
- [QByteArray ssid() const](#ssid)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### OlpcMeshSetting::List {#List-typedef}

### OlpcMeshSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### OlpcMeshSetting::OlpcMeshSetting() {#OlpcMeshSetting}

### \[explicit\] OlpcMeshSetting::OlpcMeshSetting(const NetworkManager::OlpcMeshSetting::Ptr &*other*) {#OlpcMeshSetting-1}

### quint32 OlpcMeshSetting::channel() const {#channel}

*See also* [setChannel](networkmanager-olpcmeshsetting.md#setChannel)()

### QByteArray OlpcMeshSetting::dhcpAnycastAddress() const {#dhcpAnycastAddress}

*See also* [setDhcpAnycastAddress](networkmanager-olpcmeshsetting.md#setDhcpAnycastAddress)()

### void OlpcMeshSetting::setChannel(quint32 *channel*) {#setChannel}

*See also* [channel](networkmanager-olpcmeshsetting.md#channel)()

### void OlpcMeshSetting::setDhcpAnycastAddress(const QByteArray &*address*) {#setDhcpAnycastAddress}

*See also* [dhcpAnycastAddress](networkmanager-olpcmeshsetting.md#dhcpAnycastAddress)()

### void OlpcMeshSetting::setSsid(const QByteArray &*ssid*) {#setSsid}

*See also* [ssid](networkmanager-olpcmeshsetting.md#ssid)()

### QByteArray OlpcMeshSetting::ssid() const {#ssid}

*See also* [setSsid](networkmanager-olpcmeshsetting.md#setSsid)()
