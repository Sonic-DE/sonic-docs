---
title: "NetworkManager::OvsInterfaceSetting Class"
description: "Represents ovs-interface setting."
---

# NetworkManager::OvsInterfaceSetting Class

Represents ovs-interface setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/OvsInterfaceSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-ovsinterfacesetting-members.md)

## Public Types

- [OvsInterfaceSetting::List](#List-typedef)
- [OvsInterfaceSetting::Ptr](#Ptr-typedef)

## Public Functions

- [OvsInterfaceSetting()](#OvsInterfaceSetting)
- [OvsInterfaceSetting(const NetworkManager::OvsInterfaceSetting::Ptr &other)](#OvsInterfaceSetting-1)
- [QString interfaceType() const](#interfaceType)
- [void setInterfaceType(const QString &type)](#setInterfaceType)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### OvsInterfaceSetting::List {#List-typedef}

### OvsInterfaceSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### OvsInterfaceSetting::OvsInterfaceSetting() {#OvsInterfaceSetting}

### \[explicit\] OvsInterfaceSetting::OvsInterfaceSetting(const NetworkManager::OvsInterfaceSetting::Ptr &*other*) {#OvsInterfaceSetting-1}

### QString OvsInterfaceSetting::interfaceType() const {#interfaceType}

*See also* [setInterfaceType](networkmanager-ovsinterfacesetting.md#setInterfaceType)()

### void OvsInterfaceSetting::setInterfaceType(const QString &*type*) {#setInterfaceType}

*See also* [interfaceType](networkmanager-ovsinterfacesetting.md#interfaceType)()
