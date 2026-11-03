---
title: "NetworkManager::IpTunnelSetting Class"
description: "Represents IpTunnel setting."
---

# NetworkManager::IpTunnelSetting Class

Represents IpTunnel setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/IpTunnelSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-iptunnelsetting-members.md)

## Public Types

- [enum IpTunnelSetting::Flag](#Flag-enum)
- [IpTunnelSetting::List](#List-typedef)
- [enum IpTunnelSetting::Mode](#Mode-enum)
- [IpTunnelSetting::Ptr](#Ptr-typedef)

## Public Functions

- [IpTunnelSetting()](#IpTunnelSetting)
- [IpTunnelSetting(const NetworkManager::IpTunnelSetting::Ptr &other)](#IpTunnelSetting-1)
- [quint32 encapsulationLimit() const](#encapsulationLimit)
- [NetworkManager::IpTunnelSetting::Flags flags() const](#flags)
- [quint32 flowLabel() const](#flowLabel)
- [QString inputKey() const](#inputKey)
- [QString local() const](#local)
- [NetworkManager::IpTunnelSetting::Mode mode() const](#mode)
- [quint32 mtu() const](#mtu)
- [QString outputKey() const](#outputKey)
- [QString parent() const](#parent)
- [bool pathMtuDiscovery() const](#pathMtuDiscovery)
- [QString remote() const](#remote)
- [void setEncapsulationLimit(quint32 limit)](#setEncapsulationLimit)
- [void setFlags(NetworkManager::IpTunnelSetting::Flags flags)](#setFlags)
- [void setFlowLabel(quint32 label)](#setFlowLabel)
- [void setInputKey(const QString &key)](#setInputKey)
- [void setLocal(const QString &local)](#setLocal)
- [void setMode(NetworkManager::IpTunnelSetting::Mode mode)](#setMode)
- [void setMtu(quint32 mtu)](#setMtu)
- [void setOutputKey(const QString &key)](#setOutputKey)
- [void setParent(const QString &parent)](#setParent)
- [void setPathMtuDiscovery(bool discovery)](#setPathMtuDiscovery)
- [void setRemote(const QString &remote)](#setRemote)
- [void setTos(quint32 tos)](#setTos)
- [void setTtl(quint32 ttl)](#setTtl)
- [quint32 tos() const](#tos)
- [quint32 ttl() const](#ttl)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum IpTunnelSetting::Flag {#Flag-enum}

**flags IpTunnelSetting::Flags**

| Constant |   |
| --- | --- |
| `NetworkManager::IpTunnelSetting::None` | `0x0` |
| `NetworkManager::IpTunnelSetting::Ip6IgnEncapLimit` | `0x1` |
| `NetworkManager::IpTunnelSetting::Ip6UseOrigTclass` | `0x2` |
| `NetworkManager::IpTunnelSetting::Ip6UseOrigFlowlabel` | `0x4` |
| `NetworkManager::IpTunnelSetting::Ip6Mip6Dev` | `0x8` |
| `NetworkManager::IpTunnelSetting::Ip6RcvDscpCopy` | `0x10` |
| `NetworkManager::IpTunnelSetting::Ip6UseOrigFwmark` | `0x20` |

The `Flags` type is a typedef for `QFlags<Flag>. `It stores an OR combination of `Flag` values.

### IpTunnelSetting::List {#List-typedef}

### enum IpTunnelSetting::Mode {#Mode-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::IpTunnelSetting::Unknown` | `NM_IP_TUNNEL_MODE_UNKNOWN` |
| `NetworkManager::IpTunnelSetting::Ipip` | `NM_IP_TUNNEL_MODE_IPIP` |
| `NetworkManager::IpTunnelSetting::Gre` | `NM_IP_TUNNEL_MODE_GRE` |
| `NetworkManager::IpTunnelSetting::Sit` | `NM_IP_TUNNEL_MODE_SIT` |
| `NetworkManager::IpTunnelSetting::Isatap` | `NM_IP_TUNNEL_MODE_ISATAP` |
| `NetworkManager::IpTunnelSetting::Vti` | `NM_IP_TUNNEL_MODE_VTI` |
| `NetworkManager::IpTunnelSetting::Ip6ip6` | `NM_IP_TUNNEL_MODE_IP6IP6` |
| `NetworkManager::IpTunnelSetting::Ipip6` | `NM_IP_TUNNEL_MODE_IPIP6` |
| `NetworkManager::IpTunnelSetting::Ip6gre` | `NM_IP_TUNNEL_MODE_IP6GRE` |
| `NetworkManager::IpTunnelSetting::Vti6` | `NM_IP_TUNNEL_MODE_VTI6` |

### IpTunnelSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### IpTunnelSetting::IpTunnelSetting() {#IpTunnelSetting}

### \[explicit\] IpTunnelSetting::IpTunnelSetting(const NetworkManager::IpTunnelSetting::Ptr &*other*) {#IpTunnelSetting-1}

### quint32 IpTunnelSetting::encapsulationLimit() const {#encapsulationLimit}

*See also* [setEncapsulationLimit](networkmanager-iptunnelsetting.md#setEncapsulationLimit)()

### NetworkManager::IpTunnelSetting::Flags IpTunnelSetting::flags() const {#flags}

*See also* [setFlags](networkmanager-iptunnelsetting.md#setFlags)()

### quint32 IpTunnelSetting::flowLabel() const {#flowLabel}

*See also* [setFlowLabel](networkmanager-iptunnelsetting.md#setFlowLabel)()

### QString IpTunnelSetting::inputKey() const {#inputKey}

*See also* [setInputKey](networkmanager-iptunnelsetting.md#setInputKey)()

### QString IpTunnelSetting::local() const {#local}

*See also* [setLocal](networkmanager-iptunnelsetting.md#setLocal)()

### NetworkManager::IpTunnelSetting::Mode IpTunnelSetting::mode() const {#mode}

*See also* [setMode](networkmanager-iptunnelsetting.md#setMode)()

### quint32 IpTunnelSetting::mtu() const {#mtu}

*See also* [setMtu](networkmanager-iptunnelsetting.md#setMtu)()

### QString IpTunnelSetting::outputKey() const {#outputKey}

*See also* [setOutputKey](networkmanager-iptunnelsetting.md#setOutputKey)()

### QString IpTunnelSetting::parent() const {#parent}

*See also* [setParent](networkmanager-iptunnelsetting.md#setParent)()

### bool IpTunnelSetting::pathMtuDiscovery() const {#pathMtuDiscovery}

*See also* [setPathMtuDiscovery](networkmanager-iptunnelsetting.md#setPathMtuDiscovery)()

### QString IpTunnelSetting::remote() const {#remote}

*See also* [setRemote](networkmanager-iptunnelsetting.md#setRemote)()

### void IpTunnelSetting::setEncapsulationLimit(quint32 *limit*) {#setEncapsulationLimit}

*See also* [encapsulationLimit](networkmanager-iptunnelsetting.md#encapsulationLimit)()

### void IpTunnelSetting::setFlags(NetworkManager::IpTunnelSetting::Flags *flags*) {#setFlags}

*See also* [flags](networkmanager-iptunnelsetting.md#flags)()

### void IpTunnelSetting::setFlowLabel(quint32 *label*) {#setFlowLabel}

*See also* [flowLabel](networkmanager-iptunnelsetting.md#flowLabel)()

### void IpTunnelSetting::setInputKey(const QString &*key*) {#setInputKey}

*See also* [inputKey](networkmanager-iptunnelsetting.md#inputKey)()

### void IpTunnelSetting::setLocal(const QString &*local*) {#setLocal}

*See also* [local](networkmanager-iptunnelsetting.md#local)()

### void IpTunnelSetting::setMode(NetworkManager::IpTunnelSetting::Mode *mode*) {#setMode}

*See also* [mode](networkmanager-iptunnelsetting.md#mode)()

### void IpTunnelSetting::setMtu(quint32 *mtu*) {#setMtu}

*See also* [mtu](networkmanager-iptunnelsetting.md#mtu)()

### void IpTunnelSetting::setOutputKey(const QString &*key*) {#setOutputKey}

*See also* [outputKey](networkmanager-iptunnelsetting.md#outputKey)()

### void IpTunnelSetting::setParent(const QString &*parent*) {#setParent}

*See also* [parent](networkmanager-iptunnelsetting.md#parent)()

### void IpTunnelSetting::setPathMtuDiscovery(bool *discovery*) {#setPathMtuDiscovery}

*See also* [pathMtuDiscovery](networkmanager-iptunnelsetting.md#pathMtuDiscovery)()

### void IpTunnelSetting::setRemote(const QString &*remote*) {#setRemote}

*See also* [remote](networkmanager-iptunnelsetting.md#remote)()

### void IpTunnelSetting::setTos(quint32 *tos*) {#setTos}

*See also* [tos](networkmanager-iptunnelsetting.md#tos)()

### void IpTunnelSetting::setTtl(quint32 *ttl*) {#setTtl}

*See also* [ttl](networkmanager-iptunnelsetting.md#ttl)()

### quint32 IpTunnelSetting::tos() const {#tos}

*See also* [setTos](networkmanager-iptunnelsetting.md#setTos)()

### quint32 IpTunnelSetting::ttl() const {#ttl}

*See also* [setTtl](networkmanager-iptunnelsetting.md#setTtl)()
