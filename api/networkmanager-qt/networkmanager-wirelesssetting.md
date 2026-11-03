---
title: "NetworkManager::WirelessSetting Class"
description: "Represents wireless setting."
---

# NetworkManager::WirelessSetting Class

Represents wireless setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/WirelessSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-wirelesssetting-members.md)  
[Deprecated members](networkmanager-wirelesssetting-obsolete.md)

## Public Types

- [enum WirelessSetting::FrequencyBand](#FrequencyBand-enum)
- [WirelessSetting::List](#List-typedef)
- [enum WirelessSetting::NetworkMode](#NetworkMode-enum)
- [enum WirelessSetting::PowerSave](#PowerSave-enum)
- [WirelessSetting::Ptr](#Ptr-typedef)

## Public Functions

- [WirelessSetting()](#WirelessSetting)
- [WirelessSetting(const NetworkManager::WirelessSetting::Ptr &setting)](#WirelessSetting-1)
- [QString assignedMacAddress() const](#assignedMacAddress)
- [NetworkManager::WirelessSetting::FrequencyBand band() const](#band)
- [QByteArray bssid() const](#bssid)
- [quint32 channel() const](#channel)
- [QByteArray clonedMacAddress() const](#clonedMacAddress)
- [QString generateMacAddressMask() const](#generateMacAddressMask)
- [bool hidden() const](#hidden)
- [QByteArray macAddress() const](#macAddress)
- [QStringList macAddressBlacklist() const](#macAddressBlacklist)
- [NetworkManager::Setting::MacAddressRandomization macAddressRandomization() const](#macAddressRandomization)
- [NetworkManager::WirelessSetting::NetworkMode mode() const](#mode)
- [quint32 mtu() const](#mtu)
- [NetworkManager::WirelessSetting::PowerSave powerSave() const](#powerSave)
- [quint32 rate() const](#rate)
- [QString security() const](#security)
- [QStringList seenBssids() const](#seenBssids)
- [void setAssignedMacAddress(const QString &assignedMacAddress)](#setAssignedMacAddress)
- [void setBand(NetworkManager::WirelessSetting::FrequencyBand band)](#setBand)
- [void setBssid(const QByteArray &bssid)](#setBssid)
- [void setChannel(quint32 channel)](#setChannel)
- [void setGenerateMacAddressMask(const QString &macAddressMask)](#setGenerateMacAddressMask)
- [void setHidden(bool hidden)](#setHidden)
- [void setMacAddress(const QByteArray &address)](#setMacAddress)
- [void setMacAddressBlacklist(const QStringList &list)](#setMacAddressBlacklist)
- [void setMacAddressRandomization(NetworkManager::Setting::MacAddressRandomization randomization)](#setMacAddressRandomization)
- [void setMode(NetworkManager::WirelessSetting::NetworkMode mode)](#setMode)
- [void setMtu(quint32 mtu)](#setMtu)
- [void setPowerSave(NetworkManager::WirelessSetting::PowerSave powersave)](#setPowerSave)
- [void setRate(quint32 rate)](#setRate)
- [void setSeenBssids(const QStringList &list)](#setSeenBssids)
- [void setSsid(const QByteArray &ssid)](#setSsid)
- [void setTxPower(quint32 power)](#setTxPower)
- [QByteArray ssid() const](#ssid)
- [quint32 txPower() const](#txPower)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum WirelessSetting::FrequencyBand {#FrequencyBand-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::WirelessSetting::Automatic` | `0` |
| `NetworkManager::WirelessSetting::A` | `1` |
| `NetworkManager::WirelessSetting::Bg` | `2` |

### WirelessSetting::List {#List-typedef}

### enum WirelessSetting::NetworkMode {#NetworkMode-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::WirelessSetting::Infrastructure` | `0` |
| `NetworkManager::WirelessSetting::Adhoc` | `1` |
| `NetworkManager::WirelessSetting::Ap` | `2` |

### enum WirelessSetting::PowerSave {#PowerSave-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::WirelessSetting::PowerSaveDefault` | `0` |
| `NetworkManager::WirelessSetting::PowerSaveIgnore` | `1` |
| `NetworkManager::WirelessSetting::PowerSaveDisable` | `2` |
| `NetworkManager::WirelessSetting::PowerSaveEnable` | `3` |

### WirelessSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### WirelessSetting::WirelessSetting() {#WirelessSetting}

### \[explicit\] WirelessSetting::WirelessSetting(const NetworkManager::WirelessSetting::Ptr &*setting*) {#WirelessSetting-1}

### QString WirelessSetting::assignedMacAddress() const {#assignedMacAddress}

*See also* [setAssignedMacAddress](networkmanager-wirelesssetting.md#setAssignedMacAddress)()

### NetworkManager::WirelessSetting::FrequencyBand WirelessSetting::band() const {#band}

*See also* [setBand](networkmanager-wirelesssetting.md#setBand)()

### QByteArray WirelessSetting::bssid() const {#bssid}

*See also* [setBssid](networkmanager-wirelesssetting.md#setBssid)()

### quint32 WirelessSetting::channel() const {#channel}

*See also* [setChannel](networkmanager-wirelesssetting.md#setChannel)()

### QByteArray WirelessSetting::clonedMacAddress() const {#clonedMacAddress}

### QString WirelessSetting::generateMacAddressMask() const {#generateMacAddressMask}

*See also* [setGenerateMacAddressMask](networkmanager-wirelesssetting.md#setGenerateMacAddressMask)()

### bool WirelessSetting::hidden() const {#hidden}

*See also* [setHidden](networkmanager-wirelesssetting.md#setHidden)()

### QByteArray WirelessSetting::macAddress() const {#macAddress}

*See also* [setMacAddress](networkmanager-wirelesssetting.md#setMacAddress)()

### QStringList WirelessSetting::macAddressBlacklist() const {#macAddressBlacklist}

*See also* [setMacAddressBlacklist](networkmanager-wirelesssetting.md#setMacAddressBlacklist)()

### NetworkManager::Setting::MacAddressRandomization WirelessSetting::macAddressRandomization() const {#macAddressRandomization}

*See also* [setMacAddressRandomization](networkmanager-wirelesssetting.md#setMacAddressRandomization)()

### NetworkManager::WirelessSetting::NetworkMode WirelessSetting::mode() const {#mode}

*See also* [setMode](networkmanager-wirelesssetting.md#setMode)()

### quint32 WirelessSetting::mtu() const {#mtu}

*See also* [setMtu](networkmanager-wirelesssetting.md#setMtu)()

### NetworkManager::WirelessSetting::PowerSave WirelessSetting::powerSave() const {#powerSave}

*See also* [setPowerSave](networkmanager-wirelesssetting.md#setPowerSave)()

### quint32 WirelessSetting::rate() const {#rate}

*See also* [setRate](networkmanager-wirelesssetting.md#setRate)()

### QString WirelessSetting::security() const {#security}

### QStringList WirelessSetting::seenBssids() const {#seenBssids}

*See also* [setSeenBssids](networkmanager-wirelesssetting.md#setSeenBssids)()

### void WirelessSetting::setAssignedMacAddress(const QString &*assignedMacAddress*) {#setAssignedMacAddress}

*See also* [assignedMacAddress](networkmanager-wirelesssetting.md#assignedMacAddress)()

### void WirelessSetting::setBand(NetworkManager::WirelessSetting::FrequencyBand *band*) {#setBand}

*See also* [band](networkmanager-wirelesssetting.md#band)()

### void WirelessSetting::setBssid(const QByteArray &*bssid*) {#setBssid}

*See also* [bssid](networkmanager-wirelesssetting.md#bssid)()

### void WirelessSetting::setChannel(quint32 *channel*) {#setChannel}

*See also* [channel](networkmanager-wirelesssetting.md#channel)()

### void WirelessSetting::setGenerateMacAddressMask(const QString &*macAddressMask*) {#setGenerateMacAddressMask}

*See also* [generateMacAddressMask](networkmanager-wirelesssetting.md#generateMacAddressMask)()

### void WirelessSetting::setHidden(bool *hidden*) {#setHidden}

*See also* [hidden](networkmanager-wirelesssetting.md#hidden)()

### void WirelessSetting::setMacAddress(const QByteArray &*address*) {#setMacAddress}

*See also* [macAddress](networkmanager-wirelesssetting.md#macAddress)()

### void WirelessSetting::setMacAddressBlacklist(const QStringList &*list*) {#setMacAddressBlacklist}

*See also* [macAddressBlacklist](networkmanager-wirelesssetting.md#macAddressBlacklist)()

### void WirelessSetting::setMacAddressRandomization(NetworkManager::Setting::MacAddressRandomization *randomization*) {#setMacAddressRandomization}

*See also* [macAddressRandomization](networkmanager-wirelesssetting.md#macAddressRandomization)()

### void WirelessSetting::setMode(NetworkManager::WirelessSetting::NetworkMode *mode*) {#setMode}

*See also* [mode](networkmanager-wirelesssetting.md#mode)()

### void WirelessSetting::setMtu(quint32 *mtu*) {#setMtu}

*See also* [mtu](networkmanager-wirelesssetting.md#mtu)()

### void WirelessSetting::setPowerSave(NetworkManager::WirelessSetting::PowerSave *powersave*) {#setPowerSave}

*See also* [powerSave](networkmanager-wirelesssetting.md#powerSave)()

### void WirelessSetting::setRate(quint32 *rate*) {#setRate}

*See also* [rate](networkmanager-wirelesssetting.md#rate)()

### void WirelessSetting::setSeenBssids(const QStringList &*list*) {#setSeenBssids}

*See also* [seenBssids](networkmanager-wirelesssetting.md#seenBssids)()

### void WirelessSetting::setSsid(const QByteArray &*ssid*) {#setSsid}

*See also* [ssid](networkmanager-wirelesssetting.md#ssid)()

### void WirelessSetting::setTxPower(quint32 *power*) {#setTxPower}

*See also* [txPower](networkmanager-wirelesssetting.md#txPower)()

### QByteArray WirelessSetting::ssid() const {#ssid}

*See also* [setSsid](networkmanager-wirelesssetting.md#setSsid)()

### quint32 WirelessSetting::txPower() const {#txPower}

*See also* [setTxPower](networkmanager-wirelesssetting.md#setTxPower)()
