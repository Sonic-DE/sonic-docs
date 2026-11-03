---
title: "NetworkManager::OvsPortSetting Class"
description: "Represents o setting."
---

# NetworkManager::OvsPortSetting Class

Represents o setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/OvsPortSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-ovsportsetting-members.md)

## Public Types

- [OvsPortSetting::List](#List-typedef)
- [OvsPortSetting::Ptr](#Ptr-typedef)

## Public Functions

- [OvsPortSetting()](#OvsPortSetting)
- [OvsPortSetting(const NetworkManager::OvsPortSetting::Ptr &other)](#OvsPortSetting-1)
- [quint32 bondDowndelay() const](#bondDowndelay)
- [QString bondMode() const](#bondMode)
- [quint32 bondUpdelay() const](#bondUpdelay)
- [QString lacp() const](#lacp)
- [void setBondDowndelay(quint32 delay)](#setBondDowndelay)
- [void setBondMode(const QString &mode)](#setBondMode)
- [void setBondUpdelay(quint32 delay)](#setBondUpdelay)
- [void setLacp(const QString &lacp)](#setLacp)
- [void setTag(quint32 tag)](#setTag)
- [void setVlanMode(const QString &mode)](#setVlanMode)
- [quint32 tag() const](#tag)
- [QString vlanMode() const](#vlanMode)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### OvsPortSetting::List {#List-typedef}

### OvsPortSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### OvsPortSetting::OvsPortSetting() {#OvsPortSetting}

### \[explicit\] OvsPortSetting::OvsPortSetting(const NetworkManager::OvsPortSetting::Ptr &*other*) {#OvsPortSetting-1}

### quint32 OvsPortSetting::bondDowndelay() const {#bondDowndelay}

*See also* [setBondDowndelay](networkmanager-ovsportsetting.md#setBondDowndelay)()

### QString OvsPortSetting::bondMode() const {#bondMode}

*See also* [setBondMode](networkmanager-ovsportsetting.md#setBondMode)()

### quint32 OvsPortSetting::bondUpdelay() const {#bondUpdelay}

*See also* [setBondUpdelay](networkmanager-ovsportsetting.md#setBondUpdelay)()

### QString OvsPortSetting::lacp() const {#lacp}

*See also* [setLacp](networkmanager-ovsportsetting.md#setLacp)()

### void OvsPortSetting::setBondDowndelay(quint32 *delay*) {#setBondDowndelay}

*See also* [bondDowndelay](networkmanager-ovsportsetting.md#bondDowndelay)()

### void OvsPortSetting::setBondMode(const QString &*mode*) {#setBondMode}

*See also* [bondMode](networkmanager-ovsportsetting.md#bondMode)()

### void OvsPortSetting::setBondUpdelay(quint32 *delay*) {#setBondUpdelay}

*See also* [bondUpdelay](networkmanager-ovsportsetting.md#bondUpdelay)()

### void OvsPortSetting::setLacp(const QString &*lacp*) {#setLacp}

*See also* [lacp](networkmanager-ovsportsetting.md#lacp)()

### void OvsPortSetting::setTag(quint32 *tag*) {#setTag}

*See also* [tag](networkmanager-ovsportsetting.md#tag)()

### void OvsPortSetting::setVlanMode(const QString &*mode*) {#setVlanMode}

*See also* [vlanMode](networkmanager-ovsportsetting.md#vlanMode)()

### quint32 OvsPortSetting::tag() const {#tag}

*See also* [setTag](networkmanager-ovsportsetting.md#setTag)()

### QString OvsPortSetting::vlanMode() const {#vlanMode}

*See also* [setVlanMode](networkmanager-ovsportsetting.md#setVlanMode)()
