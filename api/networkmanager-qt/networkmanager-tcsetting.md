---
title: "NetworkManager::TcSetting Class"
description: "Represents Tc setting."
---

# NetworkManager::TcSetting Class

Represents Tc setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/TcSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-tcsetting-members.md)

## Public Types

- [TcSetting::List](#List-typedef)
- [TcSetting::Ptr](#Ptr-typedef)

## Public Functions

- [TcSetting()](#TcSetting)
- [TcSetting(const NetworkManager::TcSetting::Ptr &other)](#TcSetting-1)
- [NMVariantMapList qdiscs() const](#qdiscs)
- [void setQdiscs(const NMVariantMapList &qdiscs)](#setQdiscs)
- [void setTfilters(const NMVariantMapList &tfilters)](#setTfilters)
- [NMVariantMapList tfilters() const](#tfilters)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### TcSetting::List {#List-typedef}

### TcSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### TcSetting::TcSetting() {#TcSetting}

### \[explicit\] TcSetting::TcSetting(const NetworkManager::TcSetting::Ptr &*other*) {#TcSetting-1}

### NMVariantMapList TcSetting::qdiscs() const {#qdiscs}

*See also* [setQdiscs](networkmanager-tcsetting.md#setQdiscs)()

### void TcSetting::setQdiscs(const NMVariantMapList &*qdiscs*) {#setQdiscs}

*See also* [qdiscs](networkmanager-tcsetting.md#qdiscs)()

### void TcSetting::setTfilters(const NMVariantMapList &*tfilters*) {#setTfilters}

*See also* [tfilters](networkmanager-tcsetting.md#tfilters)()

### NMVariantMapList TcSetting::tfilters() const {#tfilters}

*See also* [setTfilters](networkmanager-tcsetting.md#setTfilters)()
