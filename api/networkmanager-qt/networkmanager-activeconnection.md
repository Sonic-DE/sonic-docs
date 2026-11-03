---
title: "NetworkManager::ActiveConnection Class"
description: "An active connection."
---

# NetworkManager::ActiveConnection Class

An active connection. [More...](#details)

- **Header:** `#include <NetworkManagerQt/ActiveConnection>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)
- **Inherited By:** [NetworkManager::VpnConnection](networkmanager-vpnconnection.md)

[List of all members, including inherited members](networkmanager-activeconnection-members.md)

## Public Types

- [ActiveConnection::List](#List-typedef)
- [ActiveConnection::Ptr](#Ptr-typedef)
- [enum ActiveConnection::Reason](#Reason-enum)
- [enum ActiveConnection::State](#State-enum)

## Public Functions

- [ActiveConnection(const QString &path, QObject \*parent = nullptr)](#ActiveConnection-1)
- [~ActiveConnection()](#dtor.ActiveConnection)
- [Connection::Ptr connection() const](#connection)
- [bool default4() const](#default4)
- [bool default6() const](#default6)
- [QStringList devices() const](#devices)
- [Dhcp4Config::Ptr dhcp4Config() const](#dhcp4Config)
- [Dhcp6Config::Ptr dhcp6Config() const](#dhcp6Config)
- [QString id() const](#id)
- [NetworkManager::IpConfig ipV4Config() const](#ipV4Config)
- [NetworkManager::IpConfig ipV6Config() const](#ipV6Config)
- [bool isValid() const](#isValid)
- [QString master() const](#master)
- [QString path() const](#path)
- [QString specificObject() const](#specificObject)
- [NetworkManager::ActiveConnection::State state() const](#state)
- [NetworkManager::ConnectionSettings::ConnectionType type() const](#type)
- [QString uuid() const](#uuid)
- [bool vpn() const](#vpn)

## Signals

- [void connectionChanged(const NetworkManager::Connection::Ptr &connection)](#connectionChanged)
- [void default4Changed(bool isDefault)](#default4Changed)
- [void default6Changed(bool isDefault)](#default6Changed)
- [void devicesChanged()](#devicesChanged)
- [void dhcp4ConfigChanged()](#dhcp4ConfigChanged)
- [void dhcp6ConfigChanged()](#dhcp6ConfigChanged)
- [void idChanged(const QString &id)](#idChanged)
- [void ipV4ConfigChanged()](#ipV4ConfigChanged)
- [void ipV6ConfigChanged()](#ipV6ConfigChanged)
- [void masterChanged(const QString &uni)](#masterChanged)
- [void specificObjectChanged(const QString &path)](#specificObjectChanged)
- [void stateChanged(NetworkManager::ActiveConnection::State state)](#stateChanged)
- [void stateChangedReason(NetworkManager::ActiveConnection::State state, NetworkManager::ActiveConnection::Reason reason)](#stateChangedReason)
- [void typeChanged(NetworkManager::ConnectionSettings::ConnectionType type)](#typeChanged)
- [void uuidChanged(const QString &uuid)](#uuidChanged)
- [void vpnChanged(bool isVpn)](#vpnChanged)

## Protected Functions

- [ActiveConnection(NetworkManager::ActiveConnectionPrivate &dd, QObject \*parent = nullptr)](#ActiveConnection)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### ActiveConnection::List {#List-typedef}

### ActiveConnection::Ptr {#Ptr-typedef}

### enum ActiveConnection::Reason {#Reason-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `NetworkManager::ActiveConnection::UknownReason` | `0` | The reason for the active connection state change is unknown |
| `NetworkManager::ActiveConnection::None` | `1` | No reason was given for the active connection state change |
| `NetworkManager::ActiveConnection::UserDisconnected` | `2` | The active connection changed state because the user disconnected it |
| `NetworkManager::ActiveConnection::DeviceDisconnected` | `3` | The active connection changed state because the device it was using was disconnected |
| `NetworkManager::ActiveConnection::ServiceStopped` | `4` | The service providing the VPN connection was stopped |
| `NetworkManager::ActiveConnection::IpConfigInvalid` | `5` | The IP config of the active connection was invalid |
| `NetworkManager::ActiveConnection::ConnectTimeout` | `6` | The connection attempt to the VPN service timed out |
| `NetworkManager::ActiveConnection::ServiceStartTimeout` | `7` | A timeout occurred while starting the service providing the VPN connection |
| `NetworkManager::ActiveConnection::ServiceStartFailed` | `8` | Starting the service providing the VPN connection failed |
| `NetworkManager::ActiveConnection::NoSecrets` | `9` | Necessary secrets for the connection were not provided |
| `NetworkManager::ActiveConnection::LoginFailed` | `10` | Authentication to the server failed |
| `NetworkManager::ActiveConnection::ConnectionRemoved` | `11` | The connection was deleted from settings |
| `NetworkManager::ActiveConnection::DependencyFailed` | `12` | Master connection of this connection failed to activate |
| `NetworkManager::ActiveConnection::DeviceRealizeFailed` | `13` | Could not create the software device link |
| `NetworkManager::ActiveConnection::DeviceRemoved` | `14` | The device this connection depended on disappeared |

### enum ActiveConnection::State {#State-enum}

Enum describing possible active connection states

| Constant | Value | Description |
| --- | --- | --- |
| `NetworkManager::ActiveConnection::Unknown` | `0` | The active connection is in an unknown state |
| `NetworkManager::ActiveConnection::Activating` | `1` | The connection is activating |
| `NetworkManager::ActiveConnection::Activated` | `2` | The connection is activated |
| `NetworkManager::ActiveConnection::Deactivating` | `3` | The connection is being torn down and cleaned up |
| `NetworkManager::ActiveConnection::Deactivated` | `4` | The connection is no longer active |

## Member Function Documentation {#member-function-documentation}

### \[explicit protected\] ActiveConnection::ActiveConnection(NetworkManager::ActiveConnectionPrivate &*dd*, QObject \**parent* = nullptr) {#ActiveConnection}

### \[explicit\] ActiveConnection::ActiveConnection(const QString &*path*, QObject \**parent* = nullptr) {#ActiveConnection-1}

Creates a new [ActiveConnection](networkmanager-activeconnection.md) object.

`path` the DBus path of the device

### \[override virtual noexcept\] ActiveConnection::~ActiveConnection() {#dtor.ActiveConnection}

Destroys an [ActiveConnection](networkmanager-activeconnection.md) object.

### Connection::Ptr ActiveConnection::connection() const {#connection}

Returns a valid [NetworkManager::Connection](networkmanager-connection.md) object

### \[signal\] void ActiveConnection::connectionChanged(const NetworkManager::Connection::Ptr &*connection*) {#connectionChanged}

This signal is emitted when the connection path has changed

### bool ActiveConnection::default4() const {#default4}

Whether this connection has the default IPv4 route

### bool ActiveConnection::default6() const {#default6}

Whether this connection has the default IPv6 route

### \[signal\] void ActiveConnection::default4Changed(bool *isDefault*) {#default4Changed}

The state of the default IPv4 route changed

### \[signal\] void ActiveConnection::default6Changed(bool *isDefault*) {#default6Changed}

The state of the default IPv6 route changed

### QStringList ActiveConnection::devices() const {#devices}

List of devices UNIs which are part of this connection.

### \[signal\] void ActiveConnection::devicesChanged() {#devicesChanged}

The list of devices changed.

### Dhcp4Config::Ptr ActiveConnection::dhcp4Config() const {#dhcp4Config}

The [Dhcp4Config](networkmanager-dhcp4config.md) object describing the DHCP options returned by the DHCP server (assuming the connection used DHCP). Only valid when the connection is in the NM\_ACTIVE\_CONNECTION\_STATE\_ACTIVATED state

### \[signal\] void ActiveConnection::dhcp4ConfigChanged() {#dhcp4ConfigChanged}

Emitted when the DHCP configuration for IPv4 of this network has changed.

### Dhcp6Config::Ptr ActiveConnection::dhcp6Config() const {#dhcp6Config}

The [Dhcp6Config](networkmanager-dhcp6config.md) object describing the DHCP options returned by the DHCP server (assuming the connection used DHCP). Only valid when the connection is in the NM\_ACTIVE\_CONNECTION\_STATE\_ACTIVATED state

### \[signal\] void ActiveConnection::dhcp6ConfigChanged() {#dhcp6ConfigChanged}

Emitted when the DHCP configuration for IPv6 of this network has changed.

### QString ActiveConnection::id() const {#id}

The Id of the connection

### \[signal\] void ActiveConnection::idChanged(const QString &*id*) {#idChanged}

The `id` changed

### NetworkManager::IpConfig ActiveConnection::ipV4Config() const {#ipV4Config}

The Ip4Config object describing the configuration of the connection. Only valid when the connection is in the NM\_ACTIVE\_CONNECTION\_STATE\_ACTIVATED state

### \[signal\] void ActiveConnection::ipV4ConfigChanged() {#ipV4ConfigChanged}

Emitted when the IPv4 configuration of this network has changed.

### NetworkManager::IpConfig ActiveConnection::ipV6Config() const {#ipV6Config}

The Ip6Config object describing the configuration of the connection. Only valid when the connection is in the NM\_ACTIVE\_CONNECTION\_STATE\_ACTIVATED state

### \[signal\] void ActiveConnection::ipV6ConfigChanged() {#ipV6ConfigChanged}

Emitted when the IPv6 configuration of this network has changed.

### bool ActiveConnection::isValid() const {#isValid}

Returns true is this object holds a valid connection

### QString ActiveConnection::master() const {#master}

Returns the uni of master device if the connection is a slave.

### \[signal\] void ActiveConnection::masterChanged(const QString &*uni*) {#masterChanged}

The master device changed.

### QString ActiveConnection::path() const {#path}

Return path of the connection object

### QString ActiveConnection::specificObject() const {#specificObject}

The path of the specific object associated with the connection.

### \[signal\] void ActiveConnection::specificObjectChanged(const QString &*path*) {#specificObjectChanged}

The `path` to the specific object changed

### NetworkManager::ActiveConnection::State ActiveConnection::state() const {#state}

The current state of the connection

### \[signal\] void ActiveConnection::stateChanged(NetworkManager::ActiveConnection::State *state*) {#stateChanged}

The `state` changed

### \[signal\] void ActiveConnection::stateChangedReason(NetworkManager::ActiveConnection::State *state*, NetworkManager::ActiveConnection::Reason *reason*) {#stateChangedReason}

The `state` changed because of reason `reason` (never emitted in runtime NM \< 1.8.0)

### NetworkManager::ConnectionSettings::ConnectionType ActiveConnection::type() const {#type}

The type of the connection

### \[signal\] void ActiveConnection::typeChanged(NetworkManager::ConnectionSettings::ConnectionType *type*) {#typeChanged}

The `type` changed

### QString ActiveConnection::uuid() const {#uuid}

The UUID of the connection.

### \[signal\] void ActiveConnection::uuidChanged(const QString &*uuid*) {#uuidChanged}

The `uuid` changed.

### bool ActiveConnection::vpn() const {#vpn}

Whether this is a VPN connection

### \[signal\] void ActiveConnection::vpnChanged(bool *isVpn*) {#vpnChanged}

The VPN property changed.
