---
title: "NetworkManager::GsmSetting Class"
description: "Represents gsm setting."
---

# NetworkManager::GsmSetting Class

Represents gsm setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/GsmSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-gsmsetting-members.md)  
[Deprecated members](networkmanager-gsmsetting-obsolete.md)

## Public Types

- [GsmSetting::List](#List-typedef)
- [enum GsmSetting::NetworkType](#NetworkType-enum)
- [GsmSetting::Ptr](#Ptr-typedef)

## Public Functions

- [GsmSetting()](#GsmSetting)
- [GsmSetting(const NetworkManager::GsmSetting::Ptr &other)](#GsmSetting-1)
- [quint32 allowedBand() const](#allowedBand)
- [QString apn() const](#apn)
- [QString deviceId() const](#deviceId)
- [bool homeOnly() const](#homeOnly)
- [QString networkId() const](#networkId)
- [NetworkManager::GsmSetting::NetworkType networkType() const](#networkType)
- [QString number() const](#number)
- [QString password() const](#password)
- [NetworkManager::Setting::SecretFlags passwordFlags() const](#passwordFlags)
- [QString pin() const](#pin)
- [NetworkManager::Setting::SecretFlags pinFlags() const](#pinFlags)
- [void setApn(const QString &apn)](#setApn)
- [void setDeviceId(const QString &id)](#setDeviceId)
- [void setHomeOnly(bool homeOnly)](#setHomeOnly)
- [void setNetworkId(const QString &id)](#setNetworkId)
- [void setNumber(const QString &number)](#setNumber)
- [void setPassword(const QString &password)](#setPassword)
- [void setPasswordFlags(NetworkManager::Setting::SecretFlags flags)](#setPasswordFlags)
- [void setPin(const QString &pin)](#setPin)
- [void setPinFlags(NetworkManager::Setting::SecretFlags flags)](#setPinFlags)
- [void setSimId(const QString &id)](#setSimId)
- [void setSimOperatorId(const QString &id)](#setSimOperatorId)
- [void setUsername(const QString &username)](#setUsername)
- [QString simId() const](#simId)
- [QString simOperatorId() const](#simOperatorId)
- [QString username() const](#username)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### GsmSetting::List {#List-typedef}

### enum GsmSetting::NetworkType {#NetworkType-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::GsmSetting::Any` | `-1` |
| `NetworkManager::GsmSetting::Only3G` | `0` |
| `NetworkManager::GsmSetting::GprsEdgeOnly` | `1` |
| `NetworkManager::GsmSetting::Prefer3G` | `2` |
| `NetworkManager::GsmSetting::Prefer2G` | `3` |
| `NetworkManager::GsmSetting::Prefer4GLte` | `4` |
| `NetworkManager::GsmSetting::Only4GLte` | `5` |

### GsmSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### GsmSetting::GsmSetting() {#GsmSetting}

### \[explicit\] GsmSetting::GsmSetting(const NetworkManager::GsmSetting::Ptr &*other*) {#GsmSetting-1}

### quint32 GsmSetting::allowedBand() const {#allowedBand}

### QString GsmSetting::apn() const {#apn}

*See also* [setApn](networkmanager-gsmsetting.md#setApn)()

### QString GsmSetting::deviceId() const {#deviceId}

*See also* [setDeviceId](networkmanager-gsmsetting.md#setDeviceId)()

### bool GsmSetting::homeOnly() const {#homeOnly}

*See also* [setHomeOnly](networkmanager-gsmsetting.md#setHomeOnly)()

### QString GsmSetting::networkId() const {#networkId}

*See also* [setNetworkId](networkmanager-gsmsetting.md#setNetworkId)()

### NetworkManager::GsmSetting::NetworkType GsmSetting::networkType() const {#networkType}

### QString GsmSetting::number() const {#number}

*See also* [setNumber](networkmanager-gsmsetting.md#setNumber)()

### QString GsmSetting::password() const {#password}

*See also* [setPassword](networkmanager-gsmsetting.md#setPassword)()

### NetworkManager::Setting::SecretFlags GsmSetting::passwordFlags() const {#passwordFlags}

*See also* [setPasswordFlags](networkmanager-gsmsetting.md#setPasswordFlags)()

### QString GsmSetting::pin() const {#pin}

*See also* [setPin](networkmanager-gsmsetting.md#setPin)()

### NetworkManager::Setting::SecretFlags GsmSetting::pinFlags() const {#pinFlags}

*See also* [setPinFlags](networkmanager-gsmsetting.md#setPinFlags)()

### void GsmSetting::setApn(const QString &*apn*) {#setApn}

*See also* [apn](networkmanager-gsmsetting.md#apn)()

### void GsmSetting::setDeviceId(const QString &*id*) {#setDeviceId}

*See also* [deviceId](networkmanager-gsmsetting.md#deviceId)()

### void GsmSetting::setHomeOnly(bool *homeOnly*) {#setHomeOnly}

*See also* [homeOnly](networkmanager-gsmsetting.md#homeOnly)()

### void GsmSetting::setNetworkId(const QString &*id*) {#setNetworkId}

*See also* [networkId](networkmanager-gsmsetting.md#networkId)()

### void GsmSetting::setNumber(const QString &*number*) {#setNumber}

*See also* [number](networkmanager-gsmsetting.md#number)()

### void GsmSetting::setPassword(const QString &*password*) {#setPassword}

*See also* [password](networkmanager-gsmsetting.md#password)()

### void GsmSetting::setPasswordFlags(NetworkManager::Setting::SecretFlags *flags*) {#setPasswordFlags}

*See also* [passwordFlags](networkmanager-gsmsetting.md#passwordFlags)()

### void GsmSetting::setPin(const QString &*pin*) {#setPin}

*See also* [pin](networkmanager-gsmsetting.md#pin)()

### void GsmSetting::setPinFlags(NetworkManager::Setting::SecretFlags *flags*) {#setPinFlags}

*See also* [pinFlags](networkmanager-gsmsetting.md#pinFlags)()

### void GsmSetting::setSimId(const QString &*id*) {#setSimId}

*See also* [simId](networkmanager-gsmsetting.md#simId)()

### void GsmSetting::setSimOperatorId(const QString &*id*) {#setSimOperatorId}

*See also* [simOperatorId](networkmanager-gsmsetting.md#simOperatorId)()

### void GsmSetting::setUsername(const QString &*username*) {#setUsername}

*See also* [username](networkmanager-gsmsetting.md#username)()

### QString GsmSetting::simId() const {#simId}

*See also* [setSimId](networkmanager-gsmsetting.md#setSimId)()

### QString GsmSetting::simOperatorId() const {#simOperatorId}

*See also* [setSimOperatorId](networkmanager-gsmsetting.md#setSimOperatorId)()

### QString GsmSetting::username() const {#username}

*See also* [setUsername](networkmanager-gsmsetting.md#setUsername)()
