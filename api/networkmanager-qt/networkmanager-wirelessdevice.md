---
title: "NetworkManager::WirelessDevice Class"
description: "A wireless network interface."
---

# NetworkManager::WirelessDevice Class

A wireless network interface. [More...](#details)

- **Header:** `#include <NetworkManagerQt/WirelessDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Device](networkmanager-device.md)

[List of all members, including inherited members](networkmanager-wirelessdevice-members.md)

## Public Types

- [enum WirelessDevice::Capability](#Capability-enum)
- [WirelessDevice::List](#List-typedef)
- [enum WirelessDevice::OperationMode](#OperationMode-enum)
- [WirelessDevice::Ptr](#Ptr-typedef)

## Public Functions

- [WirelessDevice(const QString &path, QObject \*parent = nullptr)](#WirelessDevice)
- [~WirelessDevice()](#dtor.WirelessDevice)
- [QStringList accessPoints() const](#accessPoints)
- [AccessPoint::Ptr activeAccessPoint() const](#activeAccessPoint)
- [int bitRate() const](#bitRate)
- [AccessPoint::Ptr findAccessPoint(const QString &uni)](#findAccessPoint)
- [WirelessNetwork::Ptr findNetwork(const QString &ssid) const](#findNetwork)
- [QString hardwareAddress() const](#hardwareAddress)
- [QDateTime lastRequestScan() const](#lastRequestScan)
- [QDateTime lastScan() const](#lastScan)
- [NetworkManager::WirelessDevice::OperationMode mode() const](#mode)
- [WirelessNetwork::List networks() const](#networks)
- [QString permanentHardwareAddress() const](#permanentHardwareAddress)
- [QDBusPendingReply\<\> requestScan(const QVariantMap &options = QVariantMap())](#requestScan)
- [NetworkManager::Device::Type type() const](#type)
- [WirelessDevice::Capabilities wirelessCapabilities() const](#wirelessCapabilities)

## Signals

- [void accessPointAppeared(const QString &uni)](#accessPointAppeared)
- [void accessPointDisappeared(const QString &uni)](#accessPointDisappeared)
- [void activeAccessPointChanged(const QString &)](#activeAccessPointChanged)
- [void bitRateChanged(int bitrate)](#bitRateChanged)
- [void hardwareAddressChanged(const QString &)](#hardwareAddressChanged)
- [void lastScanChanged(const QDateTime &dateTime)](#lastScanChanged)
- [void modeChanged(NetworkManager::WirelessDevice::OperationMode)](#modeChanged)
- [void networkAppeared(const QString &ssid)](#networkAppeared)
- [void networkDisappeared(const QString &ssid)](#networkDisappeared)
- [void permanentHardwareAddressChanged(const QString &)](#permanentHardwareAddressChanged)
- [void wirelessCapabilitiesChanged(NetworkManager::WirelessDevice::Capabilities)](#wirelessCapabilitiesChanged)
- [void wirelessPropertiesChanged(uint)](#wirelessPropertiesChanged)

## Static Public Members

- [WirelessDevice::Capabilities convertCapabilities(uint)](#convertCapabilities)
- [NetworkManager::WirelessDevice::OperationMode convertOperationMode(uint)](#convertOperationMode)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum WirelessDevice::Capability {#Capability-enum}

**flags WirelessDevice::Capabilities**

Capabilities (currently all encryption/authentication related) of the device

> **Note:** FreqValid, Freq2Ghz, Freq5Ghz are available in runtime NM \>= 1.0.2

The device's current operating mode

| Constant | Value | Description |
| --- | --- | --- |
| `NetworkManager::WirelessDevice::NoCapability` | `0x0` | Null capability |
| `NetworkManager::WirelessDevice::Wep40` | `0x1` | 40 bit WEP cipher |
| `NetworkManager::WirelessDevice::Wep104` | `0x2` | 104 bit WEP cipher |
| `NetworkManager::WirelessDevice::Tkip` | `0x4` | TKIP encryption cipher |
| `NetworkManager::WirelessDevice::Ccmp` | `0x8` | CCMP encryption cipher |
| `NetworkManager::WirelessDevice::WpaWpa` | ? | WPA authentication protocol |
| `NetworkManager::WirelessDevice::Rsn` | `0x20` | RSN authethication protocol |
| `NetworkManager::WirelessDevice::ApCap` | `0x40` | The device supports Access Point mode. |
| `NetworkManager::WirelessDevice::AdhocCap` | `0x80` | The device supports Ad-Hoc mode. |
| `NetworkManager::WirelessDevice::FreqValid` | `0x100` | The device properly reports information about supported frequencies |
| `NetworkManager::WirelessDevice::Freq2Ghz` | `0x200` | The device supports 2.4Ghz frequencies |
| `NetworkManager::WirelessDevice::Freq5Ghz` | `0x400` | The device supports 5Ghz frequencies |
| `NetworkManager::WirelessDevice::Mesh` | `0x1000` | The device supports acting as a mesh point |
| `NetworkManager::WirelessDevice::IBSSRsn` | `0x2000` | device supports WPA2/RSN in an IBSS network |

The `Capabilities` type is a typedef for `QFlags<Capability>. `It stores an OR combination of `Capability` values.

### WirelessDevice::List {#List-typedef}

### enum WirelessDevice::OperationMode {#OperationMode-enum}

The device's current operating mode

| Constant | Value | Description |
| --- | --- | --- |
| `NetworkManager::WirelessDevice::Unknown` | `0` | not associated with a network |
| `NetworkManager::WirelessDevice::Adhoc` | `1` | part of an adhoc network |
| `NetworkManager::WirelessDevice::Infra` | `2` | a station in an infrastructure wireless network |
| `NetworkManager::WirelessDevice::ApMode` | `3` | access point in an infrastructure network |

### WirelessDevice::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] WirelessDevice::WirelessDevice(const QString &*path*, QObject \**parent* = nullptr) {#WirelessDevice}

Creates a new [WirelessDevice](networkmanager-wirelessdevice.md) object.

`path` the DBus path of the devise

### \[override virtual noexcept\] WirelessDevice::~WirelessDevice() {#dtor.WirelessDevice}

Destroys a [WirelessDevice](networkmanager-wirelessdevice.md) object.

### \[signal\] void WirelessDevice::accessPointAppeared(const QString &*uni*) {#accessPointAppeared}

A new wireless access point appeared

### \[signal\] void WirelessDevice::accessPointDisappeared(const QString &*uni*) {#accessPointDisappeared}

A wireless access point disappeared

### QStringList WirelessDevice::accessPoints() const {#accessPoints}

List of wireless networks currently visible to the hardware

### AccessPoint::Ptr WirelessDevice::activeAccessPoint() const {#activeAccessPoint}

[AccessPoint](networkmanager-accesspoint.md) pointer this interface is currently associated with

### \[signal\] void WirelessDevice::activeAccessPointChanged(*const QString &*) {#activeAccessPointChanged}

The active network changed.

### int WirelessDevice::bitRate() const {#bitRate}

Retrieves the effective bit rate currently attainable by this device.

Returns the bitrate in Kbit/s

### \[signal\] void WirelessDevice::bitRateChanged(int *bitrate*) {#bitRateChanged}

This signal is emitted when the bitrate of this network has changed.

`bitrate` the new bitrate value for this network

### \[static\] WirelessDevice::Capabilities WirelessDevice::convertCapabilities(*uint*) {#convertCapabilities}

Helper method to convert wire representation of capabilities to enum

### \[static\] NetworkManager::WirelessDevice::OperationMode WirelessDevice::convertOperationMode(*uint*) {#convertOperationMode}

Helper method to convert wire representation of operation mode to enum

### AccessPoint::Ptr WirelessDevice::findAccessPoint(const QString &*uni*) {#findAccessPoint}

Finds access point object given its Unique Network Identifier.

`uni` the identifier of the AP to find from this network interface Returns a valid [AccessPoint](networkmanager-accesspoint.md) object if a network having the given UNI for this device is known to the system, 0 otherwise

### WirelessNetwork::Ptr WirelessDevice::findNetwork(const QString &*ssid*) const {#findNetwork}

Find a network with the given `ssid`, a Null object is returned if it can not be found

### QString WirelessDevice::hardwareAddress() const {#hardwareAddress}

The hardware address currently used by the network interface

### \[signal\] void WirelessDevice::hardwareAddressChanged(*const QString &*) {#hardwareAddressChanged}

The device changed its hardware address

### QDateTime WirelessDevice::lastRequestScan() const {#lastRequestScan}

The time the last RequestScan function was called Returns

### QDateTime WirelessDevice::lastScan() const {#lastScan}

The LastScan property value, converted to [QDateTime](https://doc.qt.io/qt-6/qdatetime.html)

> **Note:** will always return invalid [QDateTime](https://doc.qt.io/qt-6/qdatetime.html) when runtime NM \< 1.12 Returns

### \[signal\] void WirelessDevice::lastScanChanged(const QDateTime &*dateTime*) {#lastScanChanged}

\* The LastScan property has changed, meaning a scan has just finished \* \* ote will never be emitted when runtime NM \< 1.12 \*

*See also* lastScanTime

### NetworkManager::WirelessDevice::OperationMode WirelessDevice::mode() const {#mode}

Retrieves the operation mode of this network.

Returns the current mode

*See also* [OperationMode](networkmanager-wirelessdevice.md#OperationMode-enum)

### \[signal\] void WirelessDevice::modeChanged(*NetworkManager::WirelessDevice::OperationMode*) {#modeChanged}

The device switched operating mode.

### \[signal\] void WirelessDevice::networkAppeared(const QString &*ssid*) {#networkAppeared}

A wireless network appeared

### \[signal\] void WirelessDevice::networkDisappeared(const QString &*ssid*) {#networkDisappeared}

A wireless network disappeared

### WirelessNetwork::List WirelessDevice::networks() const {#networks}

Return the current list of networks

### QString WirelessDevice::permanentHardwareAddress() const {#permanentHardwareAddress}

The permanent hardware address of the network interface

### \[signal\] void WirelessDevice::permanentHardwareAddressChanged(*const QString &*) {#permanentHardwareAddressChanged}

The device changed its permanent hardware address

### QDBusPendingReply\<\> WirelessDevice::requestScan(const QVariantMap &*options* = QVariantMap()) {#requestScan}

Asks the device for a new scan of available wireless networks

`options` Options of scan

No documentation for options yet, see https://projects.gnome.org/[NetworkManager](networkmanager.md)/developers/api/09/spec.html\#org.freedesktop.[NetworkManager](networkmanager.md).Device.Wireless

### \[override virtual\] NetworkManager::Device::Type WirelessDevice::type() const {#type}

Reimplements: [Device::type() const](networkmanager-device.md#type).

Return the type

### WirelessDevice::Capabilities WirelessDevice::wirelessCapabilities() const {#wirelessCapabilities}

Retrieves the capabilities of this wifi network.

Returns the flag set describing the capabilities

*See also* [Capabilities](networkmanager-wirelessdevice.md#Capability-enum)

### \[signal\] void WirelessDevice::wirelessCapabilitiesChanged(*NetworkManager::WirelessDevice::Capabilities*) {#wirelessCapabilitiesChanged}

The device changed its capabilities

### \[signal\] void WirelessDevice::wirelessPropertiesChanged(*uint*) {#wirelessPropertiesChanged}

The device changed its properties
