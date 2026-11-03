---
title: "NetworkManager::Notifier Class"
description: "Qt wrapper for NetworkManager API."
---

# NetworkManager::Notifier Class

Qt wrapper for NetworkManager API. [More...](#details)

- **Header:** `#include <Notifier>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](networkmanager-notifier-members.md)  
[Deprecated members](networkmanager-notifier-obsolete.md)

## Signals

- [void activatingConnectionChanged(const QString &uni)](#activatingConnectionChanged)
- [void activeConnectionAdded(const QString &path)](#activeConnectionAdded)
- [void activeConnectionRemoved(const QString &path)](#activeConnectionRemoved)
- [void activeConnectionsChanged()](#activeConnectionsChanged)
- [void connectivityChanged(NetworkManager::Connectivity connectivity)](#connectivityChanged)
- [void connectivityCheckUriChanged(QString)](#connectivityCheckUriChanged)
- [void deviceAdded(const QString &uni)](#deviceAdded)
- [void deviceRemoved(const QString &uni)](#deviceRemoved)
- [void globalDnsConfigurationChanged(const NetworkManager::DnsConfiguration &configuration)](#globalDnsConfigurationChanged)
- [void isConnectivityCheckAvailableChanged(bool)](#isConnectivityCheckAvailableChanged)
- [void isConnectivityCheckEnabledChanged(bool)](#isConnectivityCheckEnabledChanged)
- [void isStartingUpChanged()](#isStartingUpChanged)
- [void meteredChanged(NetworkManager::Device::MeteredStatus metered)](#meteredChanged)
- [void networkingEnabledChanged(bool)](#networkingEnabledChanged)
- [void primaryConnectionChanged(const QString &uni)](#primaryConnectionChanged)
- [void primaryConnectionTypeChanged(NetworkManager::ConnectionSettings::ConnectionType type)](#primaryConnectionTypeChanged)
- [void serviceAppeared()](#serviceAppeared)
- [void serviceDisappeared()](#serviceDisappeared)
- [void statusChanged(NetworkManager::Status status)](#statusChanged)
- [void wirelessEnabledChanged(bool)](#wirelessEnabledChanged)
- [void wirelessHardwareEnabledChanged(bool)](#wirelessHardwareEnabledChanged)
- [void wwanEnabledChanged(bool)](#wwanEnabledChanged)
- [void wwanHardwareEnabledChanged(bool)](#wwanHardwareEnabledChanged)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[signal\] void Notifier::activatingConnectionChanged(const QString &*uni*) {#activatingConnectionChanged}

Emitted when the activating connection changes. `uni` path of the new activating connection

### \[signal\] void Notifier::activeConnectionAdded(const QString &*path*) {#activeConnectionAdded}

This signal is emitted when a new connection was made active

`path` the path of the new connection

### \[signal\] void Notifier::activeConnectionRemoved(const QString &*path*) {#activeConnectionRemoved}

This signal is emitted when an active connection is no longer active

`path` the path of the removed connection

### \[signal\] void Notifier::activeConnectionsChanged() {#activeConnectionsChanged}

This signal is emitted when the set of active connections changes

### \[signal\] void Notifier::connectivityChanged(NetworkManager::Connectivity *connectivity*) {#connectivityChanged}

Emitted when the global connectivity changes.

### \[signal\] void Notifier::connectivityCheckUriChanged(*QString*) {#connectivityCheckUriChanged}

Emitted when the connectivity check URI has changed @since 6.10.0

### \[signal\] void Notifier::deviceAdded(const QString &*uni*) {#deviceAdded}

This signal is emitted when a new network interface is available.

`uni` the network interface identifier

### \[signal\] void Notifier::deviceRemoved(const QString &*uni*) {#deviceRemoved}

This signal is emitted when a network interface is not available anymore.

`uni` the network interface identifier

### \[signal\] void Notifier::globalDnsConfigurationChanged(const NetworkManager::DnsConfiguration &*configuration*) {#globalDnsConfigurationChanged}

Emitted when the global DNS configuration has changed

*See also* [globalDnsConfiguration](networkmanager.md#globalDnsConfiguration)

### \[signal\] void Notifier::isConnectivityCheckAvailableChanged(*bool*) {#isConnectivityCheckAvailableChanged}

Emitted when the connectivity check availability has changed @since 6.10.0

### \[signal\] void Notifier::isConnectivityCheckEnabledChanged(*bool*) {#isConnectivityCheckEnabledChanged}

Emitted when the connectivity check statu has changed @since 6.10.0

### \[signal\] void Notifier::isStartingUpChanged() {#isStartingUpChanged}

Emitted when NM has started/finished its startup sequence

### \[signal\] void Notifier::meteredChanged(NetworkManager::Device::MeteredStatus *metered*) {#meteredChanged}

Emitted when metered property has changed

*See also* [metered](networkmanager.md#metered)

### \[signal\] void Notifier::networkingEnabledChanged(*bool*) {#networkingEnabledChanged}

This signal is emitted when the status of overall networking changed

### \[signal\] void Notifier::primaryConnectionChanged(const QString &*uni*) {#primaryConnectionChanged}

Emitted when the primary connection changes. `uni` path of the new primary connection

### \[signal\] void Notifier::primaryConnectionTypeChanged(NetworkManager::ConnectionSettings::ConnectionType *type*) {#primaryConnectionTypeChanged}

Emitted when the primary connection type changes. `connection` type of the new primary connection

### \[signal\] void Notifier::serviceAppeared() {#serviceAppeared}

This signal is emitted when the [NetworkManager](networkmanager.md) DBus service appears

### \[signal\] void Notifier::serviceDisappeared() {#serviceDisappeared}

This signal is emitted when the [NetworkManager](networkmanager.md) DBus service goes away

### \[signal\] void Notifier::statusChanged(NetworkManager::Status *status*) {#statusChanged}

This signal is emitted when the system's connection state changes

### \[signal\] void Notifier::wirelessEnabledChanged(*bool*) {#wirelessEnabledChanged}

This signal is emitted when the status of the wireless changed

### \[signal\] void Notifier::wirelessHardwareEnabledChanged(*bool*) {#wirelessHardwareEnabledChanged}

This signal is emitted when the status of the wireless changed

### \[signal\] void Notifier::wwanEnabledChanged(*bool*) {#wwanEnabledChanged}

This signal is emitted when the status of the wireless changed

### \[signal\] void Notifier::wwanHardwareEnabledChanged(*bool*) {#wwanHardwareEnabledChanged}

This signal is emitted when the status of the wireless changed
