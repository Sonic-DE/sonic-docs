---
title: "NetworkManager::VlanSetting Class"
description: "Represents vlan setting."
---

# NetworkManager::VlanSetting Class

Represents vlan setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/VlanSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-vlansetting-members.md)  
[Deprecated members](networkmanager-vlansetting-obsolete.md)

## Public Types

- [enum VlanSetting::Flag](#Flag-enum)
- [VlanSetting::List](#List-typedef)
- [VlanSetting::Ptr](#Ptr-typedef)

## Public Functions

- [VlanSetting()](#VlanSetting)
- [VlanSetting(const NetworkManager::VlanSetting::Ptr &other)](#VlanSetting-1)
- [QStringList egressPriorityMap() const](#egressPriorityMap)
- [NetworkManager::VlanSetting::Flags flags() const](#flags)
- [quint32 id() const](#id)
- [QStringList ingressPriorityMap() const](#ingressPriorityMap)
- [QString interfaceName() const](#interfaceName)
- [QString parent() const](#parent)
- [void setEgressPriorityMap(const QStringList &map)](#setEgressPriorityMap)
- [void setFlags(NetworkManager::VlanSetting::Flags flags)](#setFlags)
- [void setId(quint32 id)](#setId)
- [void setIngressPriorityMap(const QStringList &map)](#setIngressPriorityMap)
- [void setParent(const QString &parent)](#setParent)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum VlanSetting::Flag {#Flag-enum}

**flags VlanSetting::Flags**

| Constant |   |
| --- | --- |
| `NetworkManager::VlanSetting::None` | `0` |
| `NetworkManager::VlanSetting::ReorderHeaders` | `0x1` |
| `NetworkManager::VlanSetting::Gvrp` | `0x2` |
| `NetworkManager::VlanSetting::LooseBinding` | `0x4` |

The `Flags` type is a typedef for `QFlags<Flag>. `It stores an OR combination of `Flag` values.

### VlanSetting::List {#List-typedef}

### VlanSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### VlanSetting::VlanSetting() {#VlanSetting}

### \[explicit\] VlanSetting::VlanSetting(const NetworkManager::VlanSetting::Ptr &*other*) {#VlanSetting-1}

### QStringList VlanSetting::egressPriorityMap() const {#egressPriorityMap}

*See also* [setEgressPriorityMap](networkmanager-vlansetting.md#setEgressPriorityMap)()

### NetworkManager::VlanSetting::Flags VlanSetting::flags() const {#flags}

*See also* [setFlags](networkmanager-vlansetting.md#setFlags)()

### quint32 VlanSetting::id() const {#id}

*See also* [setId](networkmanager-vlansetting.md#setId)()

### QStringList VlanSetting::ingressPriorityMap() const {#ingressPriorityMap}

*See also* [setIngressPriorityMap](networkmanager-vlansetting.md#setIngressPriorityMap)()

### QString VlanSetting::interfaceName() const {#interfaceName}

### QString VlanSetting::parent() const {#parent}

*See also* [setParent](networkmanager-vlansetting.md#setParent)()

### void VlanSetting::setEgressPriorityMap(const QStringList &*map*) {#setEgressPriorityMap}

*See also* [egressPriorityMap](networkmanager-vlansetting.md#egressPriorityMap)()

### void VlanSetting::setFlags(NetworkManager::VlanSetting::Flags *flags*) {#setFlags}

*See also* [flags](networkmanager-vlansetting.md#flags)()

### void VlanSetting::setId(quint32 *id*) {#setId}

*See also* [id](networkmanager-vlansetting.md#id)()

### void VlanSetting::setIngressPriorityMap(const QStringList &*map*) {#setIngressPriorityMap}

*See also* [ingressPriorityMap](networkmanager-vlansetting.md#ingressPriorityMap)()

### void VlanSetting::setParent(const QString &*parent*) {#setParent}

*See also* [parent](networkmanager-vlansetting.md#parent)()
