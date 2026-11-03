---
title: "NetworkManager::AccessPoint Class"
description: "Represents an access point."
---

# NetworkManager::AccessPoint Class

Represents an access point. [More...](#details)

- **Header:** `#include <NetworkManagerQt/AccessPoint>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](networkmanager-accesspoint-members.md)

## Public Types

- [enum AccessPoint::Capability](#Capability-enum)
- [AccessPoint::List](#List-typedef)
- [enum AccessPoint::OperationMode](#OperationMode-enum)
- [AccessPoint::Ptr](#Ptr-typedef)
- [enum AccessPoint::WpaFlag](#WpaFlag-enum)

## Public Functions

- [AccessPoint(const QString &path, QObject \*parent = nullptr)](#AccessPoint)
- [uint bandwidth() const](#bandwidth) (since 6.12.0.)
- [NetworkManager::AccessPoint::Capabilities capabilities() const](#capabilities)
- [uint frequency() const](#frequency)
- [QString hardwareAddress() const](#hardwareAddress)
- [int lastSeen() const](#lastSeen)
- [uint maxBitRate() const](#maxBitRate)
- [NetworkManager::AccessPoint::OperationMode mode() const](#mode)
- [QByteArray rawSsid() const](#rawSsid)
- [AccessPoint::WpaFlags rsnFlags() const](#rsnFlags)
- [int signalStrength() const](#signalStrength)
- [QString ssid() const](#ssid)
- [QString uni() const](#uni)
- [AccessPoint::WpaFlags wpaFlags() const](#wpaFlags)

## Signals

- [void bandwidthChanged(uint bandwidth)](#bandwidthChanged) (since 6.12.0)
- [void bitRateChanged(int bitrate)](#bitRateChanged)
- [void capabilitiesChanged(AccessPoint::Capabilities caps)](#capabilitiesChanged)
- [void frequencyChanged(uint frequency)](#frequencyChanged)
- [void lastSeenChanged(int lastSeen)](#lastSeenChanged)
- [void rsnFlagsChanged(AccessPoint::WpaFlags flags)](#rsnFlagsChanged)
- [void signalStrengthChanged(int strength)](#signalStrengthChanged)
- [void ssidChanged(const QString &ssid)](#ssidChanged)
- [void wpaFlagsChanged(AccessPoint::WpaFlags flags)](#wpaFlagsChanged)

## Static Public Members

- [NetworkManager::AccessPoint::OperationMode convertOperationMode(uint mode)](#convertOperationMode)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum AccessPoint::Capability {#Capability-enum}

**flags AccessPoint::Capabilities**

General capabilities of an access point

| Constant | Value | Description |
| --- | --- | --- |
| `NetworkManager::AccessPoint::None` | `0x0` | Null capability - says nothing about the access point |
| `NetworkManager::AccessPoint::Privacy` | `0x1` | Access point supports privacy measures |

The `Capabilities` type is a typedef for `QFlags<Capability>. `It stores an OR combination of `Capability` values.

### AccessPoint::List {#List-typedef}

### enum AccessPoint::OperationMode {#OperationMode-enum}

The access point's current operating mode

| Constant | Value | Description |
| --- | --- | --- |
| `NetworkManager::AccessPoint::Unknown` | `0` | Not associated with a network |
| `NetworkManager::AccessPoint::Adhoc` | `1` | A station in an infrastructure wireless network |
| `NetworkManager::AccessPoint::ApMode` | `3` | Access point in an infrastructure network |

### AccessPoint::Ptr {#Ptr-typedef}

### enum AccessPoint::WpaFlag {#WpaFlag-enum}

**flags AccessPoint::WpaFlags**

Flags describing the access point's capabilities according to WPA (Wifi Protected Access)

| Constant |   |
| --- | --- |
| `NetworkManager::AccessPoint::PairWep40` | `0x1` |
| `NetworkManager::AccessPoint::PairWep104` | `0x2` |
| `NetworkManager::AccessPoint::PairTkip` | `0x4` |
| `NetworkManager::AccessPoint::PairCcmp` | `0x8` |
| `NetworkManager::AccessPoint::GroupWep40` | `0x10` |
| `NetworkManager::AccessPoint::GroupWep104` | `0x20` |
| `NetworkManager::AccessPoint::GroupTkip` | `0x40` |
| `NetworkManager::AccessPoint::GroupCcmp` | `0x80` |
| `NetworkManager::AccessPoint::KeyMgmtPsk` | `0x100` |
| `NetworkManager::AccessPoint::KeyMgmt8021x` | `0x200` |
| `NetworkManager::AccessPoint::KeyMgmtSAE` | `0x400` |
| `NetworkManager::AccessPoint::KeyMgmtOWE` | `0x800` |
| `NetworkManager::AccessPoint::KeyMgmtOWETM` | `0x1000` |
| `NetworkManager::AccessPoint::KeyMgmtEapSuiteB192` | `0x2000` |

The `WpaFlags` type is a typedef for `QFlags<WpaFlag>. `It stores an OR combination of `WpaFlag` values.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] AccessPoint::AccessPoint(const QString &*path*, QObject \**parent* = nullptr) {#AccessPoint}

### \[since 6.12.0.\] uint AccessPoint::bandwidth() const {#bandwidth}

The bandwidth announced by the access point in MHz.

This function was introduced in Qt 6.12.0..

### \[signal, since 6.12.0\] void AccessPoint::bandwidthChanged(uint *bandwidth*) {#bandwidthChanged}

This signal is emitted when bandwidth announced by the access point changes.

`lastSeen` the bandwidth announced by the access point in MHz.

This function was introduced in Qt 6.12.0.

### \[signal\] void AccessPoint::bitRateChanged(int *bitrate*) {#bitRateChanged}

This signal is emitted when the bitrate of this network has changed.

`bitrate` the new bitrate value for this network

### NetworkManager::AccessPoint::Capabilities AccessPoint::capabilities() const {#capabilities}

Returns capabilities of an access point.

### \[signal\] void AccessPoint::capabilitiesChanged(AccessPoint::Capabilities *caps*) {#capabilitiesChanged}

This signal is emitted when the capabilities of this network have changed.

`caps` the new capabilities

### \[static\] NetworkManager::AccessPoint::OperationMode AccessPoint::convertOperationMode(uint *mode*) {#convertOperationMode}

Helper method to convert wire representation of operation `mode` to enum.

### uint AccessPoint::frequency() const {#frequency}

Returns The radio channel frequency in use by the access point, in MHz.

### \[signal\] void AccessPoint::frequencyChanged(uint *frequency*) {#frequencyChanged}

This signal is emitted when the frequency used by this Access Point changes.

`frequency` the new frequency

### QString AccessPoint::hardwareAddress() const {#hardwareAddress}

Returns The hardware address (BSSID) of the access point.

### int AccessPoint::lastSeen() const {#lastSeen}

Returns The timestamp (in CLOCK\_BOOTTIME seconds) for the last time the access point was found in scan results. A value of -1 means the access point has never been found in scan results.

### \[signal\] void AccessPoint::lastSeenChanged(int *lastSeen*) {#lastSeenChanged}

This signal is emitted when the timestamp for the last time the access point was found in scan results changes.

`lastSeen` the timestamp for the last time the access point was found in scan results.

### uint AccessPoint::maxBitRate() const {#maxBitRate}

Returns The maximum bitrate this access point is capable of, in kilobits/second (Kb/s).

### NetworkManager::AccessPoint::OperationMode AccessPoint::mode() const {#mode}

Returns Describes the operating mode of the access point.

### QByteArray AccessPoint::rawSsid() const {#rawSsid}

Returns raw SSID, encoded as a byte array.

### AccessPoint::WpaFlags AccessPoint::rsnFlags() const {#rsnFlags}

Returns Flags describing the access point's capabilities according to the RSN (Robust Secure Network) protocol.

*See also* [WpaFlag](networkmanager-accesspoint.md#WpaFlag-enum)

### \[signal\] void AccessPoint::rsnFlagsChanged(AccessPoint::WpaFlags *flags*) {#rsnFlagsChanged}

This signal is emitted when the RSN(WPA2) flags in use by this access point change.

`flags` the new flags

### int AccessPoint::signalStrength() const {#signalStrength}

Returns The current signal quality of the access point, in percent.

### \[signal\] void AccessPoint::signalStrengthChanged(int *strength*) {#signalStrengthChanged}

This signal is emitted when the signal strength of this network has changed.

`strength` the new signal strength value for this network

### QString AccessPoint::ssid() const {#ssid}

Returns The Service Set Identifier identifying the access point.

### \[signal\] void AccessPoint::ssidChanged(const QString &*ssid*) {#ssidChanged}

This signal is emitted when the ssid of this Access Point changes.

`ssid` the new SSID

### QString AccessPoint::uni() const {#uni}

Returns path of the access point.

### AccessPoint::WpaFlags AccessPoint::wpaFlags() const {#wpaFlags}

Returns flags describing the access point's capabilities according to WPA (Wifi Protected Access).

*See also* [WpaFlag](networkmanager-accesspoint.md#WpaFlag-enum)

### \[signal\] void AccessPoint::wpaFlagsChanged(AccessPoint::WpaFlags *flags*) {#wpaFlagsChanged}

This signal is emitted when the WPA flags in use by this access point change.

`flags` the new flags
