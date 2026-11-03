---
title: "NetworkManager::WirelessSecuritySetting Class"
description: "Represents wireless security setting."
---

# NetworkManager::WirelessSecuritySetting Class

Represents wireless security setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/WirelessSecuritySetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-wirelesssecuritysetting-members.md)

## Public Types

- [enum WirelessSecuritySetting::AuthAlg](#AuthAlg-enum)
- [enum WirelessSecuritySetting::KeyMgmt](#KeyMgmt-enum)
- [WirelessSecuritySetting::List](#List-typedef)
- [enum WirelessSecuritySetting::Pmf](#Pmf-enum)
- [WirelessSecuritySetting::Ptr](#Ptr-typedef)
- [enum WirelessSecuritySetting::WepKeyType](#WepKeyType-enum)
- [enum WirelessSecuritySetting::WpaEncryptionCapabilities](#WpaEncryptionCapabilities-enum)
- [enum WirelessSecuritySetting::WpaProtocolVersion](#WpaProtocolVersion-enum)

## Public Functions

- [WirelessSecuritySetting()](#WirelessSecuritySetting)
- [WirelessSecuritySetting(const NetworkManager::WirelessSecuritySetting::Ptr &other)](#WirelessSecuritySetting-1)
- [NetworkManager::WirelessSecuritySetting::AuthAlg authAlg() const](#authAlg)
- [QList\<NetworkManager::WirelessSecuritySetting::WpaEncryptionCapabilities\> group() const](#group)
- [NetworkManager::WirelessSecuritySetting::KeyMgmt keyMgmt() const](#keyMgmt)
- [QString leapPassword() const](#leapPassword)
- [NetworkManager::Setting::SecretFlags leapPasswordFlags() const](#leapPasswordFlags)
- [QString leapUsername() const](#leapUsername)
- [QList\<NetworkManager::WirelessSecuritySetting::WpaEncryptionCapabilities\> pairwise() const](#pairwise)
- [NetworkManager::WirelessSecuritySetting::Pmf pmf() const](#pmf)
- [QList\<NetworkManager::WirelessSecuritySetting::WpaProtocolVersion\> proto() const](#proto)
- [QString psk() const](#psk)
- [NetworkManager::Setting::SecretFlags pskFlags() const](#pskFlags)
- [void setAuthAlg(NetworkManager::WirelessSecuritySetting::AuthAlg alg)](#setAuthAlg)
- [void setGroup(const QList\<NetworkManager::WirelessSecuritySetting::WpaEncryptionCapabilities\> &list)](#setGroup)
- [void setKeyMgmt(NetworkManager::WirelessSecuritySetting::KeyMgmt mgmt)](#setKeyMgmt)
- [void setLeapPassword(const QString &password)](#setLeapPassword)
- [void setLeapPasswordFlags(NetworkManager::Setting::SecretFlags type)](#setLeapPasswordFlags)
- [void setLeapUsername(const QString &username)](#setLeapUsername)
- [void setPairwise(const QList\<NetworkManager::WirelessSecuritySetting::WpaEncryptionCapabilities\> &list)](#setPairwise)
- [void setPmf(NetworkManager::WirelessSecuritySetting::Pmf pmf)](#setPmf)
- [void setProto(const QList\<NetworkManager::WirelessSecuritySetting::WpaProtocolVersion\> &list)](#setProto)
- [void setPsk(const QString &key)](#setPsk)
- [void setPskFlags(NetworkManager::Setting::SecretFlags type)](#setPskFlags)
- [void setWepKey0(const QString key)](#setWepKey0)
- [void setWepKey1(const QString key)](#setWepKey1)
- [void setWepKey2(const QString key)](#setWepKey2)
- [void setWepKey3(const QString key)](#setWepKey3)
- [void setWepKeyFlags(NetworkManager::Setting::SecretFlags type)](#setWepKeyFlags)
- [void setWepKeyType(NetworkManager::WirelessSecuritySetting::WepKeyType type)](#setWepKeyType)
- [void setWepTxKeyindex(quint32 index)](#setWepTxKeyindex)
- [QString wepKey0() const](#wepKey0)
- [QString wepKey1() const](#wepKey1)
- [QString wepKey2() const](#wepKey2)
- [QString wepKey3() const](#wepKey3)
- [NetworkManager::Setting::SecretFlags wepKeyFlags() const](#wepKeyFlags)
- [NetworkManager::WirelessSecuritySetting::WepKeyType wepKeyType() const](#wepKeyType)
- [quint32 wepTxKeyindex() const](#wepTxKeyindex)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum WirelessSecuritySetting::AuthAlg {#AuthAlg-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::WirelessSecuritySetting::None` | `0` |
| `NetworkManager::WirelessSecuritySetting::Open` | `1` |
| `NetworkManager::WirelessSecuritySetting::Shared` | `2` |
| `NetworkManager::WirelessSecuritySetting::Leap` | `3` |

### enum WirelessSecuritySetting::KeyMgmt {#KeyMgmt-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::WirelessSecuritySetting::Unknown` | `-1` |
| `NetworkManager::WirelessSecuritySetting::Wep` | `0` |
| `NetworkManager::WirelessSecuritySetting::Ieee8021x` | `1` |
| `NetworkManager::WirelessSecuritySetting::WpaNone` | `2` |
| `NetworkManager::WirelessSecuritySetting::WpaPsk` | `3` |
| `NetworkManager::WirelessSecuritySetting::WpaEap` | `4` |
| `NetworkManager::WirelessSecuritySetting::SAE` | `5` |
| `NetworkManager::WirelessSecuritySetting::WpaEapSuiteB192` | `6` |
| `NetworkManager::WirelessSecuritySetting::OWE` | `7` |

### WirelessSecuritySetting::List {#List-typedef}

### enum WirelessSecuritySetting::Pmf {#Pmf-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::WirelessSecuritySetting::DefaultPmf` | `0` |
| `NetworkManager::WirelessSecuritySetting::DisablePmf` | `1` |
| `NetworkManager::WirelessSecuritySetting::OptionalPmf` | `2` |
| `NetworkManager::WirelessSecuritySetting::RequiredPmf` | `3` |

### WirelessSecuritySetting::Ptr {#Ptr-typedef}

### enum WirelessSecuritySetting::WepKeyType {#WepKeyType-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::WirelessSecuritySetting::NotSpecified` | `0` |
| `NetworkManager::WirelessSecuritySetting::Hex` | `1` |
| `NetworkManager::WirelessSecuritySetting::Passphrase` | `2` |

### enum WirelessSecuritySetting::WpaEncryptionCapabilities {#WpaEncryptionCapabilities-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::WirelessSecuritySetting::Wep40` | `0` |
| `NetworkManager::WirelessSecuritySetting::Wep104` | `1` |
| `NetworkManager::WirelessSecuritySetting::Tkip` | `2` |
| `NetworkManager::WirelessSecuritySetting::Ccmp` | `3` |

### enum WirelessSecuritySetting::WpaProtocolVersion {#WpaProtocolVersion-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::WirelessSecuritySetting::Wpa` | `0` |
| `NetworkManager::WirelessSecuritySetting::Rsn` | `1` |

## Member Function Documentation {#member-function-documentation}

### WirelessSecuritySetting::WirelessSecuritySetting() {#WirelessSecuritySetting}

### \[explicit\] WirelessSecuritySetting::WirelessSecuritySetting(const NetworkManager::WirelessSecuritySetting::Ptr &*other*) {#WirelessSecuritySetting-1}

### NetworkManager::WirelessSecuritySetting::AuthAlg WirelessSecuritySetting::authAlg() const {#authAlg}

*See also* [setAuthAlg](networkmanager-wirelesssecuritysetting.md#setAuthAlg)()

### QList\<NetworkManager::WirelessSecuritySetting::WpaEncryptionCapabilities\> WirelessSecuritySetting::group() const {#group}

*See also* [setGroup](networkmanager-wirelesssecuritysetting.md#setGroup)()

### NetworkManager::WirelessSecuritySetting::KeyMgmt WirelessSecuritySetting::keyMgmt() const {#keyMgmt}

*See also* [setKeyMgmt](networkmanager-wirelesssecuritysetting.md#setKeyMgmt)()

### QString WirelessSecuritySetting::leapPassword() const {#leapPassword}

*See also* [setLeapPassword](networkmanager-wirelesssecuritysetting.md#setLeapPassword)()

### NetworkManager::Setting::SecretFlags WirelessSecuritySetting::leapPasswordFlags() const {#leapPasswordFlags}

*See also* [setLeapPasswordFlags](networkmanager-wirelesssecuritysetting.md#setLeapPasswordFlags)()

### QString WirelessSecuritySetting::leapUsername() const {#leapUsername}

*See also* [setLeapUsername](networkmanager-wirelesssecuritysetting.md#setLeapUsername)()

### QList\<NetworkManager::WirelessSecuritySetting::WpaEncryptionCapabilities\> WirelessSecuritySetting::pairwise() const {#pairwise}

*See also* [setPairwise](networkmanager-wirelesssecuritysetting.md#setPairwise)()

### NetworkManager::WirelessSecuritySetting::Pmf WirelessSecuritySetting::pmf() const {#pmf}

*See also* [setPmf](networkmanager-wirelesssecuritysetting.md#setPmf)()

### QList\<NetworkManager::WirelessSecuritySetting::WpaProtocolVersion\> WirelessSecuritySetting::proto() const {#proto}

*See also* [setProto](networkmanager-wirelesssecuritysetting.md#setProto)()

### QString WirelessSecuritySetting::psk() const {#psk}

*See also* [setPsk](networkmanager-wirelesssecuritysetting.md#setPsk)()

### NetworkManager::Setting::SecretFlags WirelessSecuritySetting::pskFlags() const {#pskFlags}

*See also* [setPskFlags](networkmanager-wirelesssecuritysetting.md#setPskFlags)()

### void WirelessSecuritySetting::setAuthAlg(NetworkManager::WirelessSecuritySetting::AuthAlg *alg*) {#setAuthAlg}

*See also* [authAlg](networkmanager-wirelesssecuritysetting.md#authAlg)()

### void WirelessSecuritySetting::setGroup(const QList\<NetworkManager::WirelessSecuritySetting::WpaEncryptionCapabilities\> &*list*) {#setGroup}

*See also* [group](networkmanager-wirelesssecuritysetting.md#group)()

### void WirelessSecuritySetting::setKeyMgmt(NetworkManager::WirelessSecuritySetting::KeyMgmt *mgmt*) {#setKeyMgmt}

*See also* [keyMgmt](networkmanager-wirelesssecuritysetting.md#keyMgmt)()

### void WirelessSecuritySetting::setLeapPassword(const QString &*password*) {#setLeapPassword}

*See also* [leapPassword](networkmanager-wirelesssecuritysetting.md#leapPassword)()

### void WirelessSecuritySetting::setLeapPasswordFlags(NetworkManager::Setting::SecretFlags *type*) {#setLeapPasswordFlags}

*See also* [leapPasswordFlags](networkmanager-wirelesssecuritysetting.md#leapPasswordFlags)()

### void WirelessSecuritySetting::setLeapUsername(const QString &*username*) {#setLeapUsername}

*See also* [leapUsername](networkmanager-wirelesssecuritysetting.md#leapUsername)()

### void WirelessSecuritySetting::setPairwise(const QList\<NetworkManager::WirelessSecuritySetting::WpaEncryptionCapabilities\> &*list*) {#setPairwise}

*See also* [pairwise](networkmanager-wirelesssecuritysetting.md#pairwise)()

### void WirelessSecuritySetting::setPmf(NetworkManager::WirelessSecuritySetting::Pmf *pmf*) {#setPmf}

*See also* [pmf](networkmanager-wirelesssecuritysetting.md#pmf)()

### void WirelessSecuritySetting::setProto(const QList\<NetworkManager::WirelessSecuritySetting::WpaProtocolVersion\> &*list*) {#setProto}

*See also* [proto](networkmanager-wirelesssecuritysetting.md#proto)()

### void WirelessSecuritySetting::setPsk(const QString &*key*) {#setPsk}

*See also* [psk](networkmanager-wirelesssecuritysetting.md#psk)()

### void WirelessSecuritySetting::setPskFlags(NetworkManager::Setting::SecretFlags *type*) {#setPskFlags}

*See also* [pskFlags](networkmanager-wirelesssecuritysetting.md#pskFlags)()

### void WirelessSecuritySetting::setWepKey0(const QString *key*) {#setWepKey0}

*See also* [wepKey0](networkmanager-wirelesssecuritysetting.md#wepKey0)()

### void WirelessSecuritySetting::setWepKey1(const QString *key*) {#setWepKey1}

*See also* [wepKey1](networkmanager-wirelesssecuritysetting.md#wepKey1)()

### void WirelessSecuritySetting::setWepKey2(const QString *key*) {#setWepKey2}

*See also* [wepKey2](networkmanager-wirelesssecuritysetting.md#wepKey2)()

### void WirelessSecuritySetting::setWepKey3(const QString *key*) {#setWepKey3}

*See also* [wepKey3](networkmanager-wirelesssecuritysetting.md#wepKey3)()

### void WirelessSecuritySetting::setWepKeyFlags(NetworkManager::Setting::SecretFlags *type*) {#setWepKeyFlags}

*See also* [wepKeyFlags](networkmanager-wirelesssecuritysetting.md#wepKeyFlags)()

### void WirelessSecuritySetting::setWepKeyType(NetworkManager::WirelessSecuritySetting::WepKeyType *type*) {#setWepKeyType}

*See also* [wepKeyType](networkmanager-wirelesssecuritysetting.md#wepKeyType)()

### void WirelessSecuritySetting::setWepTxKeyindex(quint32 *index*) {#setWepTxKeyindex}

*See also* [wepTxKeyindex](networkmanager-wirelesssecuritysetting.md#wepTxKeyindex)()

### QString WirelessSecuritySetting::wepKey0() const {#wepKey0}

*See also* [setWepKey0](networkmanager-wirelesssecuritysetting.md#setWepKey0)()

### QString WirelessSecuritySetting::wepKey1() const {#wepKey1}

*See also* [setWepKey1](networkmanager-wirelesssecuritysetting.md#setWepKey1)()

### QString WirelessSecuritySetting::wepKey2() const {#wepKey2}

*See also* [setWepKey2](networkmanager-wirelesssecuritysetting.md#setWepKey2)()

### QString WirelessSecuritySetting::wepKey3() const {#wepKey3}

*See also* [setWepKey3](networkmanager-wirelesssecuritysetting.md#setWepKey3)()

### NetworkManager::Setting::SecretFlags WirelessSecuritySetting::wepKeyFlags() const {#wepKeyFlags}

*See also* [setWepKeyFlags](networkmanager-wirelesssecuritysetting.md#setWepKeyFlags)()

### NetworkManager::WirelessSecuritySetting::WepKeyType WirelessSecuritySetting::wepKeyType() const {#wepKeyType}

*See also* [setWepKeyType](networkmanager-wirelesssecuritysetting.md#setWepKeyType)()

### quint32 WirelessSecuritySetting::wepTxKeyindex() const {#wepTxKeyindex}

*See also* [setWepTxKeyindex](networkmanager-wirelesssecuritysetting.md#setWepTxKeyindex)()
