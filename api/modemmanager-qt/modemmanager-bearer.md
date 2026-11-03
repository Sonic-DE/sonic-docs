---
title: "ModemManager::Bearer Class"
description: "The Bearer class."
---

# ModemManager::Bearer Class

The Bearer class. [More...](#details)

- **Header:** `#include <ModemManager::Bearer>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](modemmanager-bearer-members.md)

## Public Types

- [Bearer::List](#List-typedef)
- [Bearer::Ptr](#Ptr-typedef)

## Public Functions

- [Bearer(const QString &path, QObject \*parent = nullptr)](#Bearer)
- [MMBearerType bearerType() const](#bearerType) (since 6.24.0)
- [QDBusPendingReply\<void\> connectBearer()](#connectBearer)
- [ModemManager::ConnectionError connectionError() const](#connectionError) (since 6.24.0)
- [QDBusPendingReply\<void\> disconnectBearer()](#disconnectBearer)
- [QString interface() const](#interface)
- [ModemManager::IpConfig ip4Config() const](#ip4Config)
- [ModemManager::IpConfig ip6Config() const](#ip6Config)
- [uint ipTimeout() const](#ipTimeout)
- [bool isConnected() const](#isConnected)
- [bool isMultiplexed() const](#isMultiplexed) (since 6.24.0)
- [bool isSuspended() const](#isSuspended)
- [uint profileId() const](#profileId) (since 6.24.0)
- [QVariantMap properties() const](#properties)
- [bool reloadStatsSupported() const](#reloadStatsSupported) (since 6.24.0)
- [void setTimeout(int timeout)](#setTimeout)
- [QVariantMap stats() const](#stats) (since 6.24.0)
- [int timeout() const](#timeout)
- [QString uni() const](#uni)

## Signals

- [void bearerTypeChanged(MMBearerType bearerType)](#bearerTypeChanged) (since 6.24.0)
- [void connectedChanged(bool connected)](#connectedChanged)
- [void connectionErrorChanged(const ModemManager::ConnectionError &error)](#connectionErrorChanged) (since 6.24.0)
- [void interfaceChanged(const QString &iface)](#interfaceChanged)
- [void ip4ConfigChanged(const ModemManager::IpConfig &ipv4Config)](#ip4ConfigChanged)
- [void ip6ConfigChanged(const ModemManager::IpConfig &ipv6Config)](#ip6ConfigChanged)
- [void ipTimeoutChanged(uint ipTimeout)](#ipTimeoutChanged)
- [void multiplexedChanged(bool multiplexed)](#multiplexedChanged) (since 6.24.0)
- [void profileIdChanged(uint profileId)](#profileIdChanged) (since 6.24.0)
- [void propertiesChanged(const QVariantMap &properties)](#propertiesChanged)
- [void reloadStatsSupportedChanged(bool supported)](#reloadStatsSupportedChanged) (since 6.24.0)
- [void statsChanged(const QVariantMap &stats)](#statsChanged) (since 6.24.0)
- [void suspendedChanged(bool suspended)](#suspendedChanged)

## Detailed Description {#details}

This class provides access to specific actions that may be performed on available bearers.

## Member Type Documentation {#member-type-documentation}

### Bearer::List {#List-typedef}

### Bearer::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Bearer::Bearer(const QString &*path*, QObject \**parent* = nullptr) {#Bearer}

### \[since 6.24.0\] MMBearerType Bearer::bearerType() const {#bearerType}

Returns bearer type.

This function was introduced in Qt 6.24.0.

### \[signal, since 6.24.0\] void Bearer::bearerTypeChanged(MMBearerType *bearerType*) {#bearerTypeChanged}

This function was introduced in Qt 6.24.0.

### QDBusPendingReply\<void\> Bearer::connectBearer() {#connectBearer}

Requests activation of a packet data connection with the network using this bearer's properties. Upon successful activation, the modem can send and receive packet data and, depending on the addressing capability of the modem, a connection manager may need to start PPP, perform DHCP, or assign the IP address returned by the modem to the data interface. Upon successful return, the [ip4Config](modemmanager-bearer.md#ip4Config)() and/or [ip6Config](modemmanager-bearer.md#ip6Config)() properties become valid and may contain IP configuration information for the data interface associated with this bearer.

### \[signal\] void Bearer::connectedChanged(bool *connected*) {#connectedChanged}

### \[since 6.24.0\] ModemManager::ConnectionError Bearer::connectionError() const {#connectionError}

Returns additional information about the connection error.

This function was introduced in Qt 6.24.0.

### \[signal, since 6.24.0\] void Bearer::connectionErrorChanged(const ModemManager::ConnectionError &*error*) {#connectionErrorChanged}

This function was introduced in Qt 6.24.0.

### QDBusPendingReply\<void\> Bearer::disconnectBearer() {#disconnectBearer}

Disconnect and deactivate this packet data connection.

Any ongoing data session will be terminated and IP addresses become invalid when this method is called.

### QString Bearer::interface() const {#interface}

Returns the operating system name for the network data interface that provides packet data using this bearer.

Connection managers must configure this interface depending on the IP "method" given by the [ip4Config](modemmanager-bearer.md#ip4Config)() or [ip6Config](modemmanager-bearer.md#ip6Config)() properties set by bearer activation.

If MM\_BEARER\_IP\_METHOD\_STATIC or MM\_BEARER\_IP\_METHOD\_DHCP methods are given, the interface will be an ethernet-style interface suitable for DHCP or setting static IP configuration on, while if the MM\_BEARER\_IP\_METHOD\_PPP method is given, the interface will be a serial TTY which must then have PPP run over it.

### \[signal\] void Bearer::interfaceChanged(const QString &*iface*) {#interfaceChanged}

### ModemManager::IpConfig Bearer::ip4Config() const {#ip4Config}

If the bearer was configured for IPv4 addressing, upon activation this property contains the addressing details for assignment to the data interface.

### \[signal\] void Bearer::ip4ConfigChanged(const ModemManager::IpConfig &*ipv4Config*) {#ip4ConfigChanged}

### ModemManager::IpConfig Bearer::ip6Config() const {#ip6Config}

If the bearer was configured for IPv6 addressing, upon activation this property contains the addressing details for assignment to the data interface.

### \[signal\] void Bearer::ip6ConfigChanged(const ModemManager::IpConfig &*ipv6Config*) {#ip6ConfigChanged}

### uint Bearer::ipTimeout() const {#ipTimeout}

Returns maximum time to wait for a successful IP establishment, when PPP is used.

### \[signal\] void Bearer::ipTimeoutChanged(uint *ipTimeout*) {#ipTimeoutChanged}

### bool Bearer::isConnected() const {#isConnected}

Returns whether or not the bearer is connected and thus whether packet data communication using this bearer is possible.

### \[since 6.24.0\] bool Bearer::isMultiplexed() const {#isMultiplexed}

Returns whether the bearer is connected through a multiplexed network link.

This function was introduced in Qt 6.24.0.

### bool Bearer::isSuspended() const {#isSuspended}

In some devices, packet data service will be suspended while the device is handling other communication, like a voice call. If packet data service is suspended (but not deactivated) this property will be `true`

### \[signal, since 6.24.0\] void Bearer::multiplexedChanged(bool *multiplexed*) {#multiplexedChanged}

This function was introduced in Qt 6.24.0.

### \[since 6.24.0\] uint Bearer::profileId() const {#profileId}

Returns profile identifier.

This function was introduced in Qt 6.24.0.

### \[signal, since 6.24.0\] void Bearer::profileIdChanged(uint *profileId*) {#profileIdChanged}

This function was introduced in Qt 6.24.0.

### QVariantMap Bearer::properties() const {#properties}

Returns map of properties used when creating the bearer

*See also* [IpConfig](modemmanager-ipconfig.md)

### \[signal\] void Bearer::propertiesChanged(const QVariantMap &*properties*) {#propertiesChanged}

### \[since 6.24.0\] bool Bearer::reloadStatsSupported() const {#reloadStatsSupported}

Returns whether stats reload is supported.

This function was introduced in Qt 6.24.0.

### \[signal, since 6.24.0\] void Bearer::reloadStatsSupportedChanged(bool *supported*) {#reloadStatsSupportedChanged}

This function was introduced in Qt 6.24.0.

### void Bearer::setTimeout(int *timeout*) {#setTimeout}

Sets the timeout in milliseconds for all async method DBus calls. -1 means the default DBus timeout (usually 25 seconds).

*See also* [timeout](modemmanager-bearer.md#timeout)()

### \[since 6.24.0\] QVariantMap Bearer::stats() const {#stats}

Returns bearer statistics.

This function was introduced in Qt 6.24.0.

### \[signal, since 6.24.0\] void Bearer::statsChanged(const QVariantMap &*stats*) {#statsChanged}

This function was introduced in Qt 6.24.0.

### \[signal\] void Bearer::suspendedChanged(bool *suspended*) {#suspendedChanged}

### int Bearer::timeout() const {#timeout}

Returns the current value of the DBus timeout in milliseconds. -1 means the default DBus timeout (usually 25 seconds).

*See also* [setTimeout](modemmanager-bearer.md#setTimeout)()

### QString Bearer::uni() const {#uni}

Returns the DBUS path (uni) to the object
