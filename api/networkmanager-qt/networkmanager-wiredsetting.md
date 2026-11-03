---
title: "NetworkManager::WiredSetting Class"
description: "Represents wired setting."
---

# NetworkManager::WiredSetting Class

Represents wired setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/WiredSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-wiredsetting-members.md)

## Public Types

- [enum WiredSetting::DuplexType](#DuplexType-enum)
- [WiredSetting::List](#List-typedef)
- [enum WiredSetting::PortType](#PortType-enum)
- [WiredSetting::Ptr](#Ptr-typedef)
- [enum WiredSetting::S390Nettype](#S390Nettype-enum)
- [enum WiredSetting::WakeOnLanFlag](#WakeOnLanFlag-enum)

## Public Functions

- [WiredSetting()](#WiredSetting)
- [WiredSetting(const NetworkManager::WiredSetting::Ptr &other)](#WiredSetting-1)
- [QString assignedMacAddress() const](#assignedMacAddress)
- [bool autoNegotiate() const](#autoNegotiate)
- [QByteArray clonedMacAddress() const](#clonedMacAddress)
- [NetworkManager::WiredSetting::DuplexType duplexType() const](#duplexType)
- [QString generateMacAddressMask() const](#generateMacAddressMask)
- [QByteArray macAddress() const](#macAddress)
- [QStringList macAddressBlacklist() const](#macAddressBlacklist)
- [quint32 mtu() const](#mtu)
- [NetworkManager::WiredSetting::PortType port() const](#port)
- [NetworkManager::WiredSetting::S390Nettype s390NetType() const](#s390NetType)
- [QMap\<QString, QString\> s390Options() const](#s390Options)
- [QStringList s390Subchannels() const](#s390Subchannels)
- [void setAssignedMacAddress(const QString &assignedMacAddress)](#setAssignedMacAddress)
- [void setAutoNegotiate(bool autoNegotiate)](#setAutoNegotiate)
- [void setClonedMacAddress(const QByteArray &address)](#setClonedMacAddress)
- [void setDuplexType(NetworkManager::WiredSetting::DuplexType type)](#setDuplexType)
- [void setGenerateMacAddressMask(const QString &mask)](#setGenerateMacAddressMask)
- [void setMacAddress(const QByteArray &address)](#setMacAddress)
- [void setMacAddressBlacklist(const QStringList &list)](#setMacAddressBlacklist)
- [void setMtu(quint32 mtu)](#setMtu)
- [void setPort(NetworkManager::WiredSetting::PortType port)](#setPort)
- [void setS390NetType(NetworkManager::WiredSetting::S390Nettype type)](#setS390NetType)
- [void setS390Options(const QMap\<QString, QString\> &options)](#setS390Options)
- [void setS390Subchannels(const QStringList &channels)](#setS390Subchannels)
- [void setSpeed(quint32 speed)](#setSpeed)
- [void setWakeOnLan(NetworkManager::WiredSetting::WakeOnLanFlags wol)](#setWakeOnLan)
- [void setWakeOnLanPassword(const QString &password)](#setWakeOnLanPassword)
- [quint32 speed() const](#speed)
- [NetworkManager::WiredSetting::WakeOnLanFlags wakeOnLan() const](#wakeOnLan)
- [QString wakeOnLanPassword() const](#wakeOnLanPassword)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum WiredSetting::DuplexType {#DuplexType-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::WiredSetting::UnknownDuplexType` | `0` |
| `NetworkManager::WiredSetting::Half` | `1` |
| `NetworkManager::WiredSetting::Full` | `2` |

### WiredSetting::List {#List-typedef}

### enum WiredSetting::PortType {#PortType-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::WiredSetting::UnknownPort` | `0` |
| `NetworkManager::WiredSetting::Tp` | `1` |
| `NetworkManager::WiredSetting::Aui` | `2` |
| `NetworkManager::WiredSetting::Bnc` | `3` |
| `NetworkManager::WiredSetting::Mii` | `4` |

### WiredSetting::Ptr {#Ptr-typedef}

### enum WiredSetting::S390Nettype {#S390Nettype-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::WiredSetting::Undefined` | `0` |
| `NetworkManager::WiredSetting::Qeth` | `1` |
| `NetworkManager::WiredSetting::Lcs` | `2` |
| `NetworkManager::WiredSetting::Ctc` | `3` |

### enum WiredSetting::WakeOnLanFlag {#WakeOnLanFlag-enum}

**flags WiredSetting::WakeOnLanFlags**

| Constant |   |
| --- | --- |
| `NetworkManager::WiredSetting::WakeOnLanPhy` | `1 << 1` |
| `NetworkManager::WiredSetting::WakeOnLanUnicast` | `1 << 2` |
| `NetworkManager::WiredSetting::WakeOnLanMulticast` | `1 << 3` |
| `NetworkManager::WiredSetting::WakeOnLanBroadcast` | `1 << 4` |
| `NetworkManager::WiredSetting::WakeOnLanArp` | `1 << 5` |
| `NetworkManager::WiredSetting::WakeOnLanMagic` | `1 << 6` |

Special values

| Constant |   |
| --- | --- |
| `NetworkManager::WiredSetting::WakeOnLanDefault` | `1 << 0` |
| `NetworkManager::WiredSetting::WakeOnLanIgnore` | `1 << 15` |

The `WakeOnLanFlags` type is a typedef for `QFlags<WakeOnLanFlag>. `It stores an OR combination of `WakeOnLanFlag` values.

## Member Function Documentation {#member-function-documentation}

### WiredSetting::WiredSetting() {#WiredSetting}

### \[explicit\] WiredSetting::WiredSetting(const NetworkManager::WiredSetting::Ptr &*other*) {#WiredSetting-1}

### QString WiredSetting::assignedMacAddress() const {#assignedMacAddress}

*See also* [setAssignedMacAddress](networkmanager-wiredsetting.md#setAssignedMacAddress)()

### bool WiredSetting::autoNegotiate() const {#autoNegotiate}

*See also* [setAutoNegotiate](networkmanager-wiredsetting.md#setAutoNegotiate)()

### QByteArray WiredSetting::clonedMacAddress() const {#clonedMacAddress}

*See also* [setClonedMacAddress](networkmanager-wiredsetting.md#setClonedMacAddress)()

### NetworkManager::WiredSetting::DuplexType WiredSetting::duplexType() const {#duplexType}

*See also* [setDuplexType](networkmanager-wiredsetting.md#setDuplexType)()

### QString WiredSetting::generateMacAddressMask() const {#generateMacAddressMask}

*See also* [setGenerateMacAddressMask](networkmanager-wiredsetting.md#setGenerateMacAddressMask)()

### QByteArray WiredSetting::macAddress() const {#macAddress}

*See also* [setMacAddress](networkmanager-wiredsetting.md#setMacAddress)()

### QStringList WiredSetting::macAddressBlacklist() const {#macAddressBlacklist}

*See also* [setMacAddressBlacklist](networkmanager-wiredsetting.md#setMacAddressBlacklist)()

### quint32 WiredSetting::mtu() const {#mtu}

*See also* [setMtu](networkmanager-wiredsetting.md#setMtu)()

### NetworkManager::WiredSetting::PortType WiredSetting::port() const {#port}

*See also* [setPort](networkmanager-wiredsetting.md#setPort)()

### NetworkManager::WiredSetting::S390Nettype WiredSetting::s390NetType() const {#s390NetType}

*See also* [setS390NetType](networkmanager-wiredsetting.md#setS390NetType)()

### QMap\<QString, QString\> WiredSetting::s390Options() const {#s390Options}

*See also* [setS390Options](networkmanager-wiredsetting.md#setS390Options)()

### QStringList WiredSetting::s390Subchannels() const {#s390Subchannels}

*See also* [setS390Subchannels](networkmanager-wiredsetting.md#setS390Subchannels)()

### void WiredSetting::setAssignedMacAddress(const QString &*assignedMacAddress*) {#setAssignedMacAddress}

*See also* [assignedMacAddress](networkmanager-wiredsetting.md#assignedMacAddress)()

### void WiredSetting::setAutoNegotiate(bool *autoNegotiate*) {#setAutoNegotiate}

*See also* [autoNegotiate](networkmanager-wiredsetting.md#autoNegotiate)()

### void WiredSetting::setClonedMacAddress(const QByteArray &*address*) {#setClonedMacAddress}

*See also* [clonedMacAddress](networkmanager-wiredsetting.md#clonedMacAddress)()

### void WiredSetting::setDuplexType(NetworkManager::WiredSetting::DuplexType *type*) {#setDuplexType}

*See also* [duplexType](networkmanager-wiredsetting.md#duplexType)()

### void WiredSetting::setGenerateMacAddressMask(const QString &*mask*) {#setGenerateMacAddressMask}

*See also* [generateMacAddressMask](networkmanager-wiredsetting.md#generateMacAddressMask)()

### void WiredSetting::setMacAddress(const QByteArray &*address*) {#setMacAddress}

*See also* [macAddress](networkmanager-wiredsetting.md#macAddress)()

### void WiredSetting::setMacAddressBlacklist(const QStringList &*list*) {#setMacAddressBlacklist}

*See also* [macAddressBlacklist](networkmanager-wiredsetting.md#macAddressBlacklist)()

### void WiredSetting::setMtu(quint32 *mtu*) {#setMtu}

*See also* [mtu](networkmanager-wiredsetting.md#mtu)()

### void WiredSetting::setPort(NetworkManager::WiredSetting::PortType *port*) {#setPort}

*See also* [port](networkmanager-wiredsetting.md#port)()

### void WiredSetting::setS390NetType(NetworkManager::WiredSetting::S390Nettype *type*) {#setS390NetType}

*See also* [s390NetType](networkmanager-wiredsetting.md#s390NetType)()

### void WiredSetting::setS390Options(const QMap\<QString, QString\> &*options*) {#setS390Options}

*See also* [s390Options](networkmanager-wiredsetting.md#s390Options)()

### void WiredSetting::setS390Subchannels(const QStringList &*channels*) {#setS390Subchannels}

*See also* [s390Subchannels](networkmanager-wiredsetting.md#s390Subchannels)()

### void WiredSetting::setSpeed(quint32 *speed*) {#setSpeed}

*See also* [speed](networkmanager-wiredsetting.md#speed)()

### void WiredSetting::setWakeOnLan(NetworkManager::WiredSetting::WakeOnLanFlags *wol*) {#setWakeOnLan}

*See also* [wakeOnLan](networkmanager-wiredsetting.md#wakeOnLan)()

### void WiredSetting::setWakeOnLanPassword(const QString &*password*) {#setWakeOnLanPassword}

*See also* [wakeOnLanPassword](networkmanager-wiredsetting.md#wakeOnLanPassword)()

### quint32 WiredSetting::speed() const {#speed}

*See also* [setSpeed](networkmanager-wiredsetting.md#setSpeed)()

### NetworkManager::WiredSetting::WakeOnLanFlags WiredSetting::wakeOnLan() const {#wakeOnLan}

*See also* [setWakeOnLan](networkmanager-wiredsetting.md#setWakeOnLan)()

### QString WiredSetting::wakeOnLanPassword() const {#wakeOnLanPassword}

*See also* [setWakeOnLanPassword](networkmanager-wiredsetting.md#setWakeOnLanPassword)()
