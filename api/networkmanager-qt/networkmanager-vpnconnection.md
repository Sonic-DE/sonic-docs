---
title: "NetworkManager::VpnConnection Class"
description: "An active VPN connection."
---

# NetworkManager::VpnConnection Class

An active VPN connection. [More...](#details)

- **Header:** `#include <NetworkManagerQt/VpnConnection>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::ActiveConnection](networkmanager-activeconnection.md)

[List of all members, including inherited members](networkmanager-vpnconnection-members.md)

## Public Types

- [VpnConnection::List](#List-typedef)
- [VpnConnection::Ptr](#Ptr-typedef)
- [enum VpnConnection::State](#State-enum)
- [enum VpnConnection::StateChangeReason](#StateChangeReason-enum)

## Public Functions

- [VpnConnection(const QString &path, QObject \*parent = nullptr)](#VpnConnection)
- [~VpnConnection()](#dtor.VpnConnection)
- [QString banner() const](#banner)
- [NetworkManager::VpnConnection::State state() const](#state)
- [VpnConnection::operator NetworkManager::VpnConnection \*()](#operator-NetworkManager-3a-3aVpnConnection--2a)

## Signals

- [void bannerChanged(const QString &banner)](#bannerChanged)
- [void stateChanged(NetworkManager::VpnConnection::State state, NetworkManager::VpnConnection::StateChangeReason reason)](#stateChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### VpnConnection::List {#List-typedef}

### VpnConnection::Ptr {#Ptr-typedef}

### enum VpnConnection::State {#State-enum}

Enum describing the possible VPN connection states

| Constant | Value | Description |
| --- | --- | --- |
| `NetworkManager::VpnConnection::Unknown` | `0` | The state of the VPN connection is unknown. |
| `NetworkManager::VpnConnection::Prepare` | `1` | The VPN connection is preparing to connect. |
| `NetworkManager::VpnConnection::NeedAuth` | `2` | The VPN connection needs authorization credentials. |
| `NetworkManager::VpnConnection::Connecting` | `3` | The VPN connection is being established. |
| `NetworkManager::VpnConnection::GettingIpConfig` | `4` | The VPN connection is getting an IP address. |
| `NetworkManager::VpnConnection::Activated` | `5` | The VPN connection is active. |
| `NetworkManager::VpnConnection::Failed` | `6` | The VPN connection failed. |
| `NetworkManager::VpnConnection::Disconnected` | `7` | The VPN connection is disconnected. |

### enum VpnConnection::StateChangeReason {#StateChangeReason-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `NetworkManager::VpnConnection::UnknownReason` | `0` | The reason for the VPN connection state change is unknown. |
| `NetworkManager::VpnConnection::NoneReason` | `1` | No reason was given for the VPN connection state change. |
| `NetworkManager::VpnConnection::UserDisconnectedReason` | `2` | The VPN connection changed state because the user disconnected it. |
| `NetworkManager::VpnConnection::DeviceDisconnectedReason` | `3` | The VPN connection changed state because the device it was using was disconnected. |
| `NetworkManager::VpnConnection::ServiceStoppedReason` | `4` | The service providing the VPN connection was stopped. |
| `NetworkManager::VpnConnection::IpConfigInvalidReason` | `5` | The IP config of the VPN connection was invalid. |
| `NetworkManager::VpnConnection::ConnectTimeoutReason` | `6` | The connection attempt to the VPN service timed out. |
| `NetworkManager::VpnConnection::ServiceStartTimeoutReason` | `7` | A timeout occurred while starting the service providing the VPN connection. |
| `NetworkManager::VpnConnection::ServiceStartFailedReason` | `8` | Starting the service starting the service providing the VPN connection failed. |
| `NetworkManager::VpnConnection::NoSecretsReason` | `9` | Necessary secrets for the VPN connection were not provided. |
| `NetworkManager::VpnConnection::LoginFailedReason` | `10` | Authentication to the VPN server failed. |
| `NetworkManager::VpnConnection::ConnectionRemovedReason` | `11` | The connection was deleted from settings. |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] VpnConnection::VpnConnection(const QString &*path*, QObject \**parent* = nullptr) {#VpnConnection}

Creates a new [VpnConnection](networkmanager-vpnconnection.md) object.

`path` the DBus path of the device

### \[override virtual noexcept\] VpnConnection::~VpnConnection() {#dtor.VpnConnection}

Destroys a [VpnConnection](networkmanager-vpnconnection.md) object.

### QString VpnConnection::banner() const {#banner}

Return the current login banner

### \[signal\] void VpnConnection::bannerChanged(const QString &*banner*) {#bannerChanged}

This signal is emitted when the connection `banner` has changed

### NetworkManager::VpnConnection::State VpnConnection::state() const {#state}

returns the current state

### \[signal\] void VpnConnection::stateChanged(NetworkManager::VpnConnection::State *state*, NetworkManager::VpnConnection::StateChangeReason *reason*) {#stateChanged}

This signal is emitted when the VPN connection `state` has changed

### VpnConnection::operator NetworkManager::VpnConnection \*() {#operator-NetworkManager-3a-3aVpnConnection--2a}

operator for casting an [ActiveConnection](networkmanager-activeconnection.md) into a [VpnConnection](networkmanager-vpnconnection.md). Returns 0 if this object is not a VPN connection. Introduced to make it possible to create a [VpnConnection](networkmanager-vpnconnection.md) object for every active connection, without creating an [ActiveConnection](networkmanager-activeconnection.md) object, checking if it's a VPN connection, deleting the [ActiveConnection](networkmanager-activeconnection.md) and creating a [VpnConnection](networkmanager-vpnconnection.md)
