---
title: "NetworkManager::OvsBridgeSetting Class"
description: "Represents ovs-bridge setting."
---

# NetworkManager::OvsBridgeSetting Class

Represents ovs-bridge setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/OvsBridgeSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-ovsbridgesetting-members.md)

## Public Types

- [OvsBridgeSetting::List](#List-typedef)
- [OvsBridgeSetting::Ptr](#Ptr-typedef)

## Public Functions

- [OvsBridgeSetting()](#OvsBridgeSetting)
- [OvsBridgeSetting(const NetworkManager::OvsBridgeSetting::Ptr &other)](#OvsBridgeSetting-1)
- [QString failMode() const](#failMode)
- [bool mcastSnoopingEnable() const](#mcastSnoopingEnable)
- [bool rstpEnable() const](#rstpEnable)
- [void setFailMode(const QString &mode)](#setFailMode)
- [void setMcastSnoopingEnable(bool mcastSnoopingEnable)](#setMcastSnoopingEnable)
- [void setRstpEnable(bool rstpEnable)](#setRstpEnable)
- [void setStpEnable(bool stpEnable)](#setStpEnable)
- [bool stpEnable() const](#stpEnable)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### OvsBridgeSetting::List {#List-typedef}

### OvsBridgeSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### OvsBridgeSetting::OvsBridgeSetting() {#OvsBridgeSetting}

### \[explicit\] OvsBridgeSetting::OvsBridgeSetting(const NetworkManager::OvsBridgeSetting::Ptr &*other*) {#OvsBridgeSetting-1}

### QString OvsBridgeSetting::failMode() const {#failMode}

*See also* [setFailMode](networkmanager-ovsbridgesetting.md#setFailMode)()

### bool OvsBridgeSetting::mcastSnoopingEnable() const {#mcastSnoopingEnable}

*See also* [setMcastSnoopingEnable](networkmanager-ovsbridgesetting.md#setMcastSnoopingEnable)()

### bool OvsBridgeSetting::rstpEnable() const {#rstpEnable}

*See also* [setRstpEnable](networkmanager-ovsbridgesetting.md#setRstpEnable)()

### void OvsBridgeSetting::setFailMode(const QString &*mode*) {#setFailMode}

*See also* [failMode](networkmanager-ovsbridgesetting.md#failMode)()

### void OvsBridgeSetting::setMcastSnoopingEnable(bool *mcastSnoopingEnable*) {#setMcastSnoopingEnable}

*See also* [mcastSnoopingEnable](networkmanager-ovsbridgesetting.md#mcastSnoopingEnable)()

### void OvsBridgeSetting::setRstpEnable(bool *rstpEnable*) {#setRstpEnable}

*See also* [rstpEnable](networkmanager-ovsbridgesetting.md#rstpEnable)()

### void OvsBridgeSetting::setStpEnable(bool *stpEnable*) {#setStpEnable}

*See also* [stpEnable](networkmanager-ovsbridgesetting.md#stpEnable)()

### bool OvsBridgeSetting::stpEnable() const {#stpEnable}

*See also* [setStpEnable](networkmanager-ovsbridgesetting.md#setStpEnable)()
