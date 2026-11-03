---
title: "NetworkManager::VpnPlugin Class"
description: "Qt wrapper for NetworkManager API."
---

# NetworkManager::VpnPlugin Class

Qt wrapper for NetworkManager API. [More...](#details)

- **Header:** `#include <NetworkManagerQt/VpnPlugin>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](networkmanager-vpnplugin-members.md)

## Public Types

- [enum VpnPlugin::FailureType](#FailureType-enum)

## Public Functions

- [VpnPlugin(const QString &path, QObject \*parent = nullptr)](#VpnPlugin)

## Public Slots

- [void connect(const NMVariantMapMap &connection)](#connect)
- [void disconnect()](#disconnect)
- [QString needSecrets(const NMVariantMapMap &connection)](#needSecrets)
- [void onStateChanged(uint state)](#onStateChanged)
- [void setConfig(const QVariantMap &config)](#setConfig)
- [void setFailure(const QString &reason)](#setFailure)
- [void setIp4Config(const QVariantMap &config)](#setIp4Config)
- [void setIp6Config(const QVariantMap &config)](#setIp6Config)

## Signals

- [void configChanged(const QVariantMap &configuration)](#configChanged)
- [void failureChanged(uint reason)](#failureChanged)
- [void ip4ConfigChanged(const QVariantMap &ip4config)](#ip4ConfigChanged)
- [void ip6ConfigChanged(const QVariantMap &ip6config)](#ip6ConfigChanged)
- [void loginBannerChanged(const QString &banner)](#loginBannerChanged)
- [void stateChanged(NetworkManager::VpnConnection::State state)](#stateChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum VpnPlugin::FailureType {#FailureType-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::VpnPlugin::LoginFailed` | `0` |
| `NetworkManager::VpnPlugin::ConnectFailed` | `1` |
| `NetworkManager::VpnPlugin::BadIpConfig` | `2` |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] VpnPlugin::VpnPlugin(const QString &*path*, QObject \**parent* = nullptr) {#VpnPlugin}

### \[signal\] void VpnPlugin::configChanged(const QVariantMap &*configuration*) {#configChanged}

### \[protected slot\] void VpnPlugin::connect(const NMVariantMapMap &*connection*) {#connect}

### \[protected slot\] void VpnPlugin::disconnect() {#disconnect}

### \[signal\] void VpnPlugin::failureChanged(uint *reason*) {#failureChanged}

### \[signal\] void VpnPlugin::ip4ConfigChanged(const QVariantMap &*ip4config*) {#ip4ConfigChanged}

### \[signal\] void VpnPlugin::ip6ConfigChanged(const QVariantMap &*ip6config*) {#ip6ConfigChanged}

### \[signal\] void VpnPlugin::loginBannerChanged(const QString &*banner*) {#loginBannerChanged}

### \[protected slot\] QString VpnPlugin::needSecrets(const NMVariantMapMap &*connection*) {#needSecrets}

### \[protected slot\] void VpnPlugin::onStateChanged(uint *state*) {#onStateChanged}

### \[protected slot\] void VpnPlugin::setConfig(const QVariantMap &*config*) {#setConfig}

### \[protected slot\] void VpnPlugin::setFailure(const QString &*reason*) {#setFailure}

### \[protected slot\] void VpnPlugin::setIp4Config(const QVariantMap &*config*) {#setIp4Config}

### \[protected slot\] void VpnPlugin::setIp6Config(const QVariantMap &*config*) {#setIp6Config}

### \[signal\] void VpnPlugin::stateChanged(NetworkManager::VpnConnection::State *state*) {#stateChanged}
