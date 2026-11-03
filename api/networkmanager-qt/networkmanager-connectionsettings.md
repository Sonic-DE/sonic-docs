---
title: "NetworkManager::ConnectionSettings Class"
description: "Represents collection of all connection settings."
---

# NetworkManager::ConnectionSettings Class

Represents collection of all connection settings. [More...](#details)

- **Header:** `#include <NetworkManagerQt/ConnectionSettings>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`

[List of all members, including inherited members](networkmanager-connectionsettings-members.md)

## Public Types

- [enum ConnectionSettings::AutoconnectSlaves](#AutoconnectSlaves-enum)
- [enum ConnectionSettings::ConnectionType](#ConnectionType-enum)
- [ConnectionSettings::List](#List-typedef)
- [enum ConnectionSettings::Lldp](#Lldp-enum)
- [enum ConnectionSettings::Mdns](#Mdns-enum)
- [enum ConnectionSettings::Metered](#Metered-enum)
- [ConnectionSettings::Ptr](#Ptr-typedef)

## Public Functions

- [ConnectionSettings()](#ConnectionSettings)
- [ConnectionSettings(const ConnectionSettings::Ptr &other)](#ConnectionSettings-1)
- [ConnectionSettings(const NMVariantMapMap &map)](#ConnectionSettings-2)
- [ConnectionSettings(NetworkManager::ConnectionSettings::ConnectionType type, NMBluetoothCapabilities bt\_cap = NM\_BT\_CAPABILITY\_DUN)](#ConnectionSettings-3)
- [~ConnectionSettings()](#dtor.ConnectionSettings)
- [void addToPermissions(const QString &user, const QString &type)](#addToPermissions)
- [bool autoconnect() const](#autoconnect)
- [int autoconnectPriority() const](#autoconnectPriority)
- [int autoconnectRetries() const](#autoconnectRetries)
- [NetworkManager::ConnectionSettings::AutoconnectSlaves autoconnectSlaves() const](#autoconnectSlaves)
- [NetworkManager::ConnectionSettings::ConnectionType connectionType() const](#connectionType)
- [void fromMap(const NMVariantMapMap &map)](#fromMap)
- [void fromMeCard(const QVariantMap &map)](#fromMeCard)
- [quint32 gatewayPingTimeout() const](#gatewayPingTimeout)
- [QString id() const](#id)
- [QString interfaceName() const](#interfaceName)
- [bool isSlave() const](#isSlave)
- [NetworkManager::ConnectionSettings::Lldp lldp() const](#lldp)
- [QString master() const](#master)
- [NetworkManager::ConnectionSettings::Mdns mdns() const](#mdns)
- [NetworkManager::ConnectionSettings::Metered metered() const](#metered)
- [QString name() const](#name)
- [QHash\<QString, QString\> permissions() const](#permissions)
- [bool readOnly() const](#readOnly)
- [QStringList secondaries() const](#secondaries)
- [void setAutoconnect(bool autoconnect)](#setAutoconnect)
- [void setAutoconnectPriority(int priority)](#setAutoconnectPriority)
- [void setAutoconnectRetries(int retries)](#setAutoconnectRetries)
- [void setAutoconnectSlaves(NetworkManager::ConnectionSettings::AutoconnectSlaves autoconnectSlaves)](#setAutoconnectSlaves)
- [void setConnectionType(NetworkManager::ConnectionSettings::ConnectionType type, NMBluetoothCapabilities bt\_cap = NM\_BT\_CAPABILITY\_DUN)](#setConnectionType)
- [void setGatewayPingTimeout(quint32 timeout)](#setGatewayPingTimeout)
- [void setId(const QString &id)](#setId)
- [void setInterfaceName(const QString &interfaceName)](#setInterfaceName)
- [void setLldp(NetworkManager::ConnectionSettings::Lldp lldp)](#setLldp)
- [void setMaster(const QString &master)](#setMaster)
- [void setMdns(NetworkManager::ConnectionSettings::Mdns mdns)](#setMdns)
- [void setMetered(NetworkManager::ConnectionSettings::Metered metered)](#setMetered)
- [void setPermissions(const QHash\<QString, QString\> &perm)](#setPermissions)
- [void setReadOnly(bool readonly)](#setReadOnly)
- [void setSecondaries(const QStringList &secondaries)](#setSecondaries)
- [void setSlaveType(const QString &type)](#setSlaveType)
- [void setStableId(const QString &stableId)](#setStableId)
- [void setTimestamp(const QDateTime &timestamp)](#setTimestamp)
- [void setUuid(const QString &uuid)](#setUuid)
- [void setZone(const QString &zone)](#setZone)
- [Setting::Ptr setting(NetworkManager::Setting::SettingType type) const](#setting)
- [Setting::Ptr setting(const QString &type) const](#setting-1)
- [Setting::List settings() const](#settings)
- [QString slaveType() const](#slaveType)
- [QString stableId() const](#stableId)
- [QDateTime timestamp() const](#timestamp)
- [NMVariantMapMap toMap() const](#toMap)
- [QString uuid() const](#uuid)
- [QString zone() const](#zone)

## Static Public Members

- [QString createNewUuid()](#createNewUuid)
- [QString typeAsString(const NetworkManager::ConnectionSettings::ConnectionType type)](#typeAsString)
- [NetworkManager::ConnectionSettings::ConnectionType typeFromString(const QString &typeString)](#typeFromString)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum ConnectionSettings::AutoconnectSlaves {#AutoconnectSlaves-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::ConnectionSettings::SlavesDefault` | `-1` |
| `NetworkManager::ConnectionSettings::DoNotConnectSlaves` | `0` |
| `NetworkManager::ConnectionSettings::ConnectAllSlaves` | `1` |

### enum ConnectionSettings::ConnectionType {#ConnectionType-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::ConnectionSettings::Unknown` | `0` |
| `NetworkManager::ConnectionSettings::Adsl` | `1` |
| `NetworkManager::ConnectionSettings::Bluetooth` | `2` |
| `NetworkManager::ConnectionSettings::Bond` | `3` |
| `NetworkManager::ConnectionSettings::Bridge` | `4` |
| `NetworkManager::ConnectionSettings::Cdma` | `5` |
| `NetworkManager::ConnectionSettings::Gsm` | `6` |
| `NetworkManager::ConnectionSettings::Infiniband` | `7` |
| `NetworkManager::ConnectionSettings::OLPCMesh` | `8` |
| `NetworkManager::ConnectionSettings::Pppoe` | `9` |
| `NetworkManager::ConnectionSettings::Vlan` | `10` |
| `NetworkManager::ConnectionSettings::Vpn` | `11` |
| `NetworkManager::ConnectionSettings::Wimax` | `12` |
| `NetworkManager::ConnectionSettings::Wired` | `13` |
| `NetworkManager::ConnectionSettings::Wireless` | `14` |
| `NetworkManager::ConnectionSettings::Team` | `15` |
| `NetworkManager::ConnectionSettings::Generic` | `16` |
| `NetworkManager::ConnectionSettings::Tun` | `17` |
| `NetworkManager::ConnectionSettings::IpTunnel` | `18` |
| `NetworkManager::ConnectionSettings::WireGuard` | `19` |
| `NetworkManager::ConnectionSettings::Loopback` | `20` |
| `NetworkManager::ConnectionSettings::WifiP2P (since Qt 6.20)` | `21` |

### ConnectionSettings::List {#List-typedef}

### enum ConnectionSettings::Lldp {#Lldp-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::ConnectionSettings::LldpDefault` | `-1` |
| `NetworkManager::ConnectionSettings::LldpDisable` | `0` |
| `NetworkManager::ConnectionSettings::LldpEnableRx` | `1` |

### enum ConnectionSettings::Mdns {#Mdns-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::ConnectionSettings::MdnsDefault` | `-1` |
| `NetworkManager::ConnectionSettings::MdnsNo` | `0` |
| `NetworkManager::ConnectionSettings::MdnsResolve` | `1` |
| `NetworkManager::ConnectionSettings::MdnsResolveAndRespond` | `2` |

### enum ConnectionSettings::Metered {#Metered-enum}

FIXME same enum as in device.h, unfortunately it's not possible to use that one maybe in future move all enums into one header so they can be used across all classes

| Constant |   |
| --- | --- |
| `NetworkManager::ConnectionSettings::MeteredUnknown` | `0` |
| `NetworkManager::ConnectionSettings::MeteredYes` | `1` |
| `NetworkManager::ConnectionSettings::MeteredNo` | `2` |
| `NetworkManager::ConnectionSettings::MeteredGuessYes` | `3` |
| `NetworkManager::ConnectionSettings::MeteredGuessNo` | `4` |

### ConnectionSettings::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### ConnectionSettings::ConnectionSettings() {#ConnectionSettings}

### \[explicit\] ConnectionSettings::ConnectionSettings(const ConnectionSettings::Ptr &*other*) {#ConnectionSettings-1}

### \[explicit\] ConnectionSettings::ConnectionSettings(const NMVariantMapMap &*map*) {#ConnectionSettings-2}

### \[explicit\] ConnectionSettings::ConnectionSettings(NetworkManager::ConnectionSettings::ConnectionType *type*, NMBluetoothCapabilities *bt\_cap* = NM\_BT\_CAPABILITY\_DUN) {#ConnectionSettings-3}

### \[virtual noexcept\] ConnectionSettings::~ConnectionSettings() {#dtor.ConnectionSettings}

### void ConnectionSettings::addToPermissions(const QString &*user*, const QString &*type*) {#addToPermissions}

### bool ConnectionSettings::autoconnect() const {#autoconnect}

*See also* [setAutoconnect](networkmanager-connectionsettings.md#setAutoconnect)()

### int ConnectionSettings::autoconnectPriority() const {#autoconnectPriority}

*See also* [setAutoconnectPriority](networkmanager-connectionsettings.md#setAutoconnectPriority)()

### int ConnectionSettings::autoconnectRetries() const {#autoconnectRetries}

*See also* [setAutoconnectRetries](networkmanager-connectionsettings.md#setAutoconnectRetries)()

### NetworkManager::ConnectionSettings::AutoconnectSlaves ConnectionSettings::autoconnectSlaves() const {#autoconnectSlaves}

*See also* [setAutoconnectSlaves](networkmanager-connectionsettings.md#setAutoconnectSlaves)()

### NetworkManager::ConnectionSettings::ConnectionType ConnectionSettings::connectionType() const {#connectionType}

*See also* [setConnectionType](networkmanager-connectionsettings.md#setConnectionType)()

### \[static\] QString ConnectionSettings::createNewUuid() {#createNewUuid}

### void ConnectionSettings::fromMap(const NMVariantMapMap &*map*) {#fromMap}

### void ConnectionSettings::fromMeCard(const QVariantMap &*map*) {#fromMeCard}

### quint32 ConnectionSettings::gatewayPingTimeout() const {#gatewayPingTimeout}

*See also* [setGatewayPingTimeout](networkmanager-connectionsettings.md#setGatewayPingTimeout)()

### QString ConnectionSettings::id() const {#id}

*See also* [setId](networkmanager-connectionsettings.md#setId)()

### QString ConnectionSettings::interfaceName() const {#interfaceName}

*See also* [setInterfaceName](networkmanager-connectionsettings.md#setInterfaceName)()

### bool ConnectionSettings::isSlave() const {#isSlave}

### NetworkManager::ConnectionSettings::Lldp ConnectionSettings::lldp() const {#lldp}

*See also* [setLldp](networkmanager-connectionsettings.md#setLldp)()

### QString ConnectionSettings::master() const {#master}

*See also* [setMaster](networkmanager-connectionsettings.md#setMaster)()

### NetworkManager::ConnectionSettings::Mdns ConnectionSettings::mdns() const {#mdns}

*See also* [setMdns](networkmanager-connectionsettings.md#setMdns)()

### NetworkManager::ConnectionSettings::Metered ConnectionSettings::metered() const {#metered}

*See also* [setMetered](networkmanager-connectionsettings.md#setMetered)()

### QString ConnectionSettings::name() const {#name}

### QHash\<QString, QString\> ConnectionSettings::permissions() const {#permissions}

*See also* [setPermissions](networkmanager-connectionsettings.md#setPermissions)()

### bool ConnectionSettings::readOnly() const {#readOnly}

*See also* [setReadOnly](networkmanager-connectionsettings.md#setReadOnly)()

### QStringList ConnectionSettings::secondaries() const {#secondaries}

*See also* [setSecondaries](networkmanager-connectionsettings.md#setSecondaries)()

### void ConnectionSettings::setAutoconnect(bool *autoconnect*) {#setAutoconnect}

*See also* [autoconnect](networkmanager-connectionsettings.md#autoconnect)()

### void ConnectionSettings::setAutoconnectPriority(int *priority*) {#setAutoconnectPriority}

*See also* [autoconnectPriority](networkmanager-connectionsettings.md#autoconnectPriority)()

### void ConnectionSettings::setAutoconnectRetries(int *retries*) {#setAutoconnectRetries}

*See also* [autoconnectRetries](networkmanager-connectionsettings.md#autoconnectRetries)()

### void ConnectionSettings::setAutoconnectSlaves(NetworkManager::ConnectionSettings::AutoconnectSlaves *autoconnectSlaves*) {#setAutoconnectSlaves}

*See also* [autoconnectSlaves](networkmanager-connectionsettings.md#autoconnectSlaves)()

### void ConnectionSettings::setConnectionType(NetworkManager::ConnectionSettings::ConnectionType *type*, NMBluetoothCapabilities *bt\_cap* = NM\_BT\_CAPABILITY\_DUN) {#setConnectionType}

*See also* [connectionType](networkmanager-connectionsettings.md#connectionType)()

### void ConnectionSettings::setGatewayPingTimeout(quint32 *timeout*) {#setGatewayPingTimeout}

*See also* [gatewayPingTimeout](networkmanager-connectionsettings.md#gatewayPingTimeout)()

### void ConnectionSettings::setId(const QString &*id*) {#setId}

*See also* [id](networkmanager-connectionsettings.md#id)()

### void ConnectionSettings::setInterfaceName(const QString &*interfaceName*) {#setInterfaceName}

*See also* [interfaceName](networkmanager-connectionsettings.md#interfaceName)()

### void ConnectionSettings::setLldp(NetworkManager::ConnectionSettings::Lldp *lldp*) {#setLldp}

*See also* [lldp](networkmanager-connectionsettings.md#lldp)()

### void ConnectionSettings::setMaster(const QString &*master*) {#setMaster}

*See also* [master](networkmanager-connectionsettings.md#master)()

### void ConnectionSettings::setMdns(NetworkManager::ConnectionSettings::Mdns *mdns*) {#setMdns}

*See also* [mdns](networkmanager-connectionsettings.md#mdns)()

### void ConnectionSettings::setMetered(NetworkManager::ConnectionSettings::Metered *metered*) {#setMetered}

*See also* [metered](networkmanager-connectionsettings.md#metered)()

### void ConnectionSettings::setPermissions(const QHash\<QString, QString\> &*perm*) {#setPermissions}

*See also* [permissions](networkmanager-connectionsettings.md#permissions)()

### void ConnectionSettings::setReadOnly(bool *readonly*) {#setReadOnly}

*See also* [readOnly](networkmanager-connectionsettings.md#readOnly)()

### void ConnectionSettings::setSecondaries(const QStringList &*secondaries*) {#setSecondaries}

*See also* [secondaries](networkmanager-connectionsettings.md#secondaries)()

### void ConnectionSettings::setSlaveType(const QString &*type*) {#setSlaveType}

*See also* [slaveType](networkmanager-connectionsettings.md#slaveType)()

### void ConnectionSettings::setStableId(const QString &*stableId*) {#setStableId}

*See also* [stableId](networkmanager-connectionsettings.md#stableId)()

### void ConnectionSettings::setTimestamp(const QDateTime &*timestamp*) {#setTimestamp}

*See also* [timestamp](networkmanager-connectionsettings.md#timestamp)()

### void ConnectionSettings::setUuid(const QString &*uuid*) {#setUuid}

*See also* [uuid](networkmanager-connectionsettings.md#uuid)()

### void ConnectionSettings::setZone(const QString &*zone*) {#setZone}

*See also* [zone](networkmanager-connectionsettings.md#zone)()

### Setting::Ptr ConnectionSettings::setting(NetworkManager::Setting::SettingType *type*) const {#setting}

### Setting::Ptr ConnectionSettings::setting(const QString &*type*) const {#setting-1}

### Setting::List ConnectionSettings::settings() const {#settings}

### QString ConnectionSettings::slaveType() const {#slaveType}

*See also* [setSlaveType](networkmanager-connectionsettings.md#setSlaveType)()

### QString ConnectionSettings::stableId() const {#stableId}

*See also* [setStableId](networkmanager-connectionsettings.md#setStableId)()

### QDateTime ConnectionSettings::timestamp() const {#timestamp}

*See also* [setTimestamp](networkmanager-connectionsettings.md#setTimestamp)()

### NMVariantMapMap ConnectionSettings::toMap() const {#toMap}

### \[static\] QString ConnectionSettings::typeAsString(const NetworkManager::ConnectionSettings::ConnectionType *type*) {#typeAsString}

### \[static\] NetworkManager::ConnectionSettings::ConnectionType ConnectionSettings::typeFromString(const QString &*typeString*) {#typeFromString}

### QString ConnectionSettings::uuid() const {#uuid}

*See also* [setUuid](networkmanager-connectionsettings.md#setUuid)()

### QString ConnectionSettings::zone() const {#zone}

*See also* [setZone](networkmanager-connectionsettings.md#setZone)()
