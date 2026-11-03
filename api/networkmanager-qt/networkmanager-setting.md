---
title: "NetworkManager::Setting Class"
description: "Base class for all kinds of setting."
---

# NetworkManager::Setting Class

Base class for all kinds of setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/Setting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherited By:** [NetworkManager::AdslSetting](networkmanager-adslsetting.md), [NetworkManager::BluetoothSetting](networkmanager-bluetoothsetting.md), [NetworkManager::BondSetting](networkmanager-bondsetting.md), [NetworkManager::BridgePortSetting](networkmanager-bridgeportsetting.md), [NetworkManager::BridgeSetting](networkmanager-bridgesetting.md), [NetworkManager::CdmaSetting](networkmanager-cdmasetting.md), [NetworkManager::DcbSetting](networkmanager-dcbsetting.md), [NetworkManager::GenericSetting](networkmanager-genericsetting.md), [NetworkManager::GsmSetting](networkmanager-gsmsetting.md), [NetworkManager::InfinibandSetting](networkmanager-infinibandsetting.md), [NetworkManager::IpTunnelSetting](networkmanager-iptunnelsetting.md), [NetworkManager::Ipv4Setting](networkmanager-ipv4setting.md), [NetworkManager::Ipv6Setting](networkmanager-ipv6setting.md), [NetworkManager::MacsecSetting](networkmanager-macsecsetting.md), [NetworkManager::MatchSetting](networkmanager-matchsetting.md), [NetworkManager::OlpcMeshSetting](networkmanager-olpcmeshsetting.md), [NetworkManager::OvsBridgeSetting](networkmanager-ovsbridgesetting.md), [NetworkManager::OvsInterfaceSetting](networkmanager-ovsinterfacesetting.md), [NetworkManager::OvsPatchSetting](networkmanager-ovspatchsetting.md), [NetworkManager::OvsPortSetting](networkmanager-ovsportsetting.md), [NetworkManager::PppoeSetting](networkmanager-pppoesetting.md), [NetworkManager::PppSetting](networkmanager-pppsetting.md), [NetworkManager::ProxySetting](networkmanager-proxysetting.md), [NetworkManager::Security8021xSetting](networkmanager-security8021xsetting.md), [NetworkManager::SerialSetting](networkmanager-serialsetting.md), [NetworkManager::TcSetting](networkmanager-tcsetting.md), [NetworkManager::TeamPortSetting](networkmanager-teamportsetting.md), [NetworkManager::TeamSetting](networkmanager-teamsetting.md), [NetworkManager::TemplateSetting](networkmanager-templatesetting.md), [NetworkManager::TunSetting](networkmanager-tunsetting.md), [NetworkManager::UserSetting](networkmanager-usersetting.md), [NetworkManager::VlanSetting](networkmanager-vlansetting.md), [NetworkManager::VpnSetting](networkmanager-vpnsetting.md), [NetworkManager::VxlanSetting](networkmanager-vxlansetting.md), [NetworkManager::WifiP2PSetting](networkmanager-wifip2psetting.md), [NetworkManager::WimaxSetting](networkmanager-wimaxsetting.md), [NetworkManager::WiredSetting](networkmanager-wiredsetting.md), [NetworkManager::WireGuardSetting](networkmanager-wireguardsetting.md), [NetworkManager::WirelessSecuritySetting](networkmanager-wirelesssecuritysetting.md), and [NetworkManager::WirelessSetting](networkmanager-wirelesssetting.md)

[List of all members, including inherited members](networkmanager-setting-members.md)

## Public Types

- [enum Setting::MacAddressRandomization](#MacAddressRandomization-enum)
- [enum Setting::SecretFlagType](#SecretFlagType-enum)
- [enum Setting::SettingType](#SettingType-enum)

## Public Functions

- [Setting(NetworkManager::Setting::SettingType type)](#Setting)
- [Setting(const NetworkManager::Setting::Ptr &setting)](#Setting-1)
- [~Setting()](#dtor.Setting)
- [void fromMap(const QVariantMap &map)](#fromMap)
- [bool isNull() const](#isNull)
- [QString name() const](#name)
- [QStringList needSecrets(bool requestNew = false) const](#needSecrets)
- [void secretsFromMap(const QVariantMap &map)](#secretsFromMap)
- [void secretsFromStringMap(const NMStringMap &map)](#secretsFromStringMap)
- [QVariantMap secretsToMap() const](#secretsToMap)
- [NMStringMap secretsToStringMap() const](#secretsToStringMap)
- [void setInitialized(bool initialized)](#setInitialized)
- [void setType(NetworkManager::Setting::SettingType type)](#setType)
- [QVariantMap toMap() const](#toMap)
- [NetworkManager::Setting::SettingType type() const](#type)

## Static Public Members

- [QString typeAsString(NetworkManager::Setting::SettingType type)](#typeAsString)
- [NetworkManager::Setting::SettingType typeFromString(const QString &type)](#typeFromString)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum Setting::MacAddressRandomization {#MacAddressRandomization-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::Setting::MacAddressRandomizationDefault` | `0` |
| `NetworkManager::Setting::MacAddressRandomizationNever` | `1` |
| `NetworkManager::Setting::MacAddressRandomizationAlways` | `2` |

### enum Setting::SecretFlagType {#SecretFlagType-enum}

**flags Setting::SecretFlags**

| Constant |   |
| --- | --- |
| `NetworkManager::Setting::None` | `0` |
| `NetworkManager::Setting::AgentOwned` | `0x01` |
| `NetworkManager::Setting::NotSaved` | `0x02` |
| `NetworkManager::Setting::NotRequired` | `0x04` |

The `SecretFlags` type is a typedef for `QFlags<SecretFlagType>. `It stores an OR combination of `SecretFlagType` values.

### enum Setting::SettingType {#SettingType-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::Setting::Adsl` | `0` |
| `NetworkManager::Setting::Cdma` | `1` |
| `NetworkManager::Setting::Gsm` | `2` |
| `NetworkManager::Setting::Infiniband` | `3` |
| `NetworkManager::Setting::Ipv4` | `4` |
| `NetworkManager::Setting::Ipv6` | `5` |
| `NetworkManager::Setting::Ppp` | `6` |
| `NetworkManager::Setting::Pppoe` | `7` |
| `NetworkManager::Setting::Security8021x` | `8` |
| `NetworkManager::Setting::Serial` | `9` |
| `NetworkManager::Setting::Vpn` | `10` |
| `NetworkManager::Setting::Wired` | `11` |
| `NetworkManager::Setting::Wireless` | `12` |
| `NetworkManager::Setting::WirelessSecurity` | `13` |
| `NetworkManager::Setting::Bluetooth` | `14` |
| `NetworkManager::Setting::OlpcMesh` | `15` |
| `NetworkManager::Setting::Vlan` | `16` |
| `NetworkManager::Setting::Wimax` | `17` |
| `NetworkManager::Setting::Bond` | `18` |
| `NetworkManager::Setting::Bridge` | `19` |
| `NetworkManager::Setting::BridgePort` | `20` |
| `NetworkManager::Setting::Team` | `21` |
| `NetworkManager::Setting::Generic` | `22` |
| `NetworkManager::Setting::Tun` | `23` |
| `NetworkManager::Setting::Vxlan` | `24` |
| `NetworkManager::Setting::IpTunnel` | `25` |
| `NetworkManager::Setting::Proxy` | `26` |
| `NetworkManager::Setting::User` | `27` |
| `NetworkManager::Setting::OvsBridge` | `28` |
| `NetworkManager::Setting::OvsInterface` | `29` |
| `NetworkManager::Setting::OvsPatch` | `30` |
| `NetworkManager::Setting::OvsPort` | `31` |
| `NetworkManager::Setting::Match` | `32` |
| `NetworkManager::Setting::Tc` | `33` |
| `NetworkManager::Setting::TeamPort` | `34` |
| `NetworkManager::Setting::Macsec` | `35` |
| `NetworkManager::Setting::Dcb` | `36` |
| `NetworkManager::Setting::WireGuard` | `37` |
| `NetworkManager::Setting::WifiP2P (since Qt 6.20)` | `38` |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Setting::Setting(NetworkManager::Setting::SettingType *type*) {#Setting}

### \[explicit\] Setting::Setting(const NetworkManager::Setting::Ptr &*setting*) {#Setting-1}

### \[virtual noexcept\] Setting::~Setting() {#dtor.Setting}

### \[virtual\] void Setting::fromMap(const QVariantMap &*map*) {#fromMap}

Must be reimplemented, default implementation does nothing.

### bool Setting::isNull() const {#isNull}

### \[virtual\] QString Setting::name() const {#name}

Must be reimplemented, default implementationd does nothing.

### \[virtual\] QStringList Setting::needSecrets(bool *requestNew* = false) const {#needSecrets}

### \[virtual\] void Setting::secretsFromMap(const QVariantMap &*map*) {#secretsFromMap}

### \[virtual\] void Setting::secretsFromStringMap(const NMStringMap &*map*) {#secretsFromStringMap}

secretsFromStringMap is a convenience function to set the secrets from a map of strings. `map` to extract secrets from

### \[virtual\] QVariantMap Setting::secretsToMap() const {#secretsToMap}

### \[virtual\] NMStringMap Setting::secretsToStringMap() const {#secretsToStringMap}

secretsToStringMap is a convenience function to get the secrets to map of strings. Returns string map with current secrets

### void Setting::setInitialized(bool *initialized*) {#setInitialized}

### void Setting::setType(NetworkManager::Setting::SettingType *type*) {#setType}

*See also* [type](networkmanager-setting.md#type)()

### \[virtual\] QVariantMap Setting::toMap() const {#toMap}

Must be reimplemented, default implementationd does nothing.

### NetworkManager::Setting::SettingType Setting::type() const {#type}

*See also* [setType](networkmanager-setting.md#setType)()

### \[static\] QString Setting::typeAsString(NetworkManager::Setting::SettingType *type*) {#typeAsString}

### \[static\] NetworkManager::Setting::SettingType Setting::typeFromString(const QString &*type*) {#typeFromString}
