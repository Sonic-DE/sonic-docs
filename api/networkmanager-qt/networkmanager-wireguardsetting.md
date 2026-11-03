---
title: "NetworkManager::WireGuardSetting Class"
description: "Represents generic setting."
---

# NetworkManager::WireGuardSetting Class

Represents generic setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/WireGuardSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-wireguardsetting-members.md)

## Public Types

- [WireGuardSetting::List](#List-typedef)
- [WireGuardSetting::Ptr](#Ptr-typedef)

## Public Functions

- [WireGuardSetting()](#WireGuardSetting)
- [WireGuardSetting(const NetworkManager::WireGuardSetting::Ptr &other)](#WireGuardSetting-1)
- [quint32 fwmark() const](#fwmark)
- [quint32 listenPort() const](#listenPort)
- [quint32 mtu() const](#mtu)
- [bool peerRoutes() const](#peerRoutes)
- [NMVariantMapList peers() const](#peers)
- [QString privateKey() const](#privateKey)
- [NetworkManager::Setting::SecretFlags privateKeyFlags() const](#privateKeyFlags)
- [void setFwmark(quint32 fwmark)](#setFwmark)
- [void setListenPort(quint32 port)](#setListenPort)
- [void setMtu(quint32 mtu)](#setMtu)
- [void setPeerRoutes(bool peerRoutes)](#setPeerRoutes)
- [void setPeers(const NMVariantMapList &peers)](#setPeers)
- [void setPrivateKey(const QString &key)](#setPrivateKey)
- [void setPrivateKeyFlags(NetworkManager::Setting::SecretFlags flags)](#setPrivateKeyFlags)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### WireGuardSetting::List {#List-typedef}

### WireGuardSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### WireGuardSetting::WireGuardSetting() {#WireGuardSetting}

### \[explicit\] WireGuardSetting::WireGuardSetting(const NetworkManager::WireGuardSetting::Ptr &*other*) {#WireGuardSetting-1}

### quint32 WireGuardSetting::fwmark() const {#fwmark}

*See also* [setFwmark](networkmanager-wireguardsetting.md#setFwmark)()

### quint32 WireGuardSetting::listenPort() const {#listenPort}

*See also* [setListenPort](networkmanager-wireguardsetting.md#setListenPort)()

### quint32 WireGuardSetting::mtu() const {#mtu}

*See also* [setMtu](networkmanager-wireguardsetting.md#setMtu)()

### bool WireGuardSetting::peerRoutes() const {#peerRoutes}

*See also* [setPeerRoutes](networkmanager-wireguardsetting.md#setPeerRoutes)()

### NMVariantMapList WireGuardSetting::peers() const {#peers}

*See also* [setPeers](networkmanager-wireguardsetting.md#setPeers)()

### QString WireGuardSetting::privateKey() const {#privateKey}

*See also* [setPrivateKey](networkmanager-wireguardsetting.md#setPrivateKey)()

### NetworkManager::Setting::SecretFlags WireGuardSetting::privateKeyFlags() const {#privateKeyFlags}

*See also* [setPrivateKeyFlags](networkmanager-wireguardsetting.md#setPrivateKeyFlags)()

### void WireGuardSetting::setFwmark(quint32 *fwmark*) {#setFwmark}

*See also* [fwmark](networkmanager-wireguardsetting.md#fwmark)()

### void WireGuardSetting::setListenPort(quint32 *port*) {#setListenPort}

*See also* [listenPort](networkmanager-wireguardsetting.md#listenPort)()

### void WireGuardSetting::setMtu(quint32 *mtu*) {#setMtu}

*See also* [mtu](networkmanager-wireguardsetting.md#mtu)()

### void WireGuardSetting::setPeerRoutes(bool *peerRoutes*) {#setPeerRoutes}

*See also* [peerRoutes](networkmanager-wireguardsetting.md#peerRoutes)()

### void WireGuardSetting::setPeers(const NMVariantMapList &*peers*) {#setPeers}

*See also* [peers](networkmanager-wireguardsetting.md#peers)()

### void WireGuardSetting::setPrivateKey(const QString &*key*) {#setPrivateKey}

*See also* [privateKey](networkmanager-wireguardsetting.md#privateKey)()

### void WireGuardSetting::setPrivateKeyFlags(NetworkManager::Setting::SecretFlags *flags*) {#setPrivateKeyFlags}

*See also* [privateKeyFlags](networkmanager-wireguardsetting.md#privateKeyFlags)()
