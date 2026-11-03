---
title: "NetworkManager::WimaxDevice Class"
description: "Wimax network interface."
---

# NetworkManager::WimaxDevice Class

Wimax network interface. [More...](#details)

- **Header:** `#include <NetworkManagerQt/WimaxDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Device](networkmanager-device.md)

[List of all members, including inherited members](networkmanager-wimaxdevice-members.md)

## Public Types

- [WimaxDevice::List](#List-typedef)
- [WimaxDevice::Ptr](#Ptr-typedef)

## Public Functions

- [WimaxDevice(const QString &path, QObject \*parent = nullptr)](#WimaxDevice)
- [~WimaxDevice()](#dtor.WimaxDevice)
- [WimaxNsp::Ptr activeNsp() const](#activeNsp)
- [QString bsid() const](#bsid)
- [uint centerFrequency() const](#centerFrequency)
- [int cinr() const](#cinr)
- [NetworkManager::WimaxNsp::Ptr findNsp(const QString &uni) const](#findNsp)
- [QString hardwareAddress() const](#hardwareAddress)
- [QStringList nsps() const](#nsps)
- [int rssi() const](#rssi)
- [int txPower() const](#txPower)
- [NetworkManager::Device::Type type() const](#type)

## Signals

- [void activeNspChanged(const QString &)](#activeNspChanged)
- [void bitRateChanged(int bitrate)](#bitRateChanged)
- [void bsidChanged(const QString &)](#bsidChanged)
- [void centerFrequencyChanged(uint)](#centerFrequencyChanged)
- [void cinrChanged(int)](#cinrChanged)
- [void hardwareAddressChanged(const QString &)](#hardwareAddressChanged)
- [void nspAppeared(const QString &)](#nspAppeared)
- [void nspDisappeared(const QString &)](#nspDisappeared)
- [void rssiChanged(int)](#rssiChanged)
- [void txPowerChanged(int)](#txPowerChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### WimaxDevice::List {#List-typedef}

### WimaxDevice::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] WimaxDevice::WimaxDevice(const QString &*path*, QObject \**parent* = nullptr) {#WimaxDevice}

Creates a new [WimaxDevice](networkmanager-wimaxdevice.md) object.

`path` the DBus path of the device

### \[override virtual noexcept\] WimaxDevice::~WimaxDevice() {#dtor.WimaxDevice}

Destroys a [WimaxDevice](networkmanager-wimaxdevice.md) object.

### WimaxNsp::Ptr WimaxDevice::activeNsp() const {#activeNsp}

Identifier of the NSP this interface is currently associated with

### \[signal\] void WimaxDevice::activeNspChanged(*const QString &*) {#activeNspChanged}

The active NSP changed.

### \[signal\] void WimaxDevice::bitRateChanged(int *bitrate*) {#bitRateChanged}

This signal is emitted when the bitrate of this network has changed.

`bitrate` the new bitrate value for this network

### QString WimaxDevice::bsid() const {#bsid}

The ID of the serving base station as received from the network.

### \[signal\] void WimaxDevice::bsidChanged(*const QString &*) {#bsidChanged}

The BSID changed.

### uint WimaxDevice::centerFrequency() const {#centerFrequency}

Center frequency (in KHz) of the radio channel the device is using to communicate with the network when connected.

### \[signal\] void WimaxDevice::centerFrequencyChanged(*uint*) {#centerFrequencyChanged}

The device changed its center frequency

### int WimaxDevice::cinr() const {#cinr}

CINR (Carrier to Interference + Noise Ratio) of the current radio link in dB.

### \[signal\] void WimaxDevice::cinrChanged(*int*) {#cinrChanged}

The device changed its signal/noise ratio

### NetworkManager::WimaxNsp::Ptr WimaxDevice::findNsp(const QString &*uni*) const {#findNsp}

Finds NSP object given its Unique Network Identifier.

`uni` the identifier of the AP to find from this network interface Returns a valid [WimaxNsp](networkmanager-wimaxnsp.md) object if a network having the given UNI for this device is known to the system, 0 otherwise

### QString WimaxDevice::hardwareAddress() const {#hardwareAddress}

The hardware address currently used by the network interface

### \[signal\] void WimaxDevice::hardwareAddressChanged(*const QString &*) {#hardwareAddressChanged}

The device changed its hardware address

### \[signal\] void WimaxDevice::nspAppeared(*const QString &*) {#nspAppeared}

A new NSP appeared

### \[signal\] void WimaxDevice::nspDisappeared(*const QString &*) {#nspDisappeared}

A wireless access point disappeared

### QStringList WimaxDevice::nsps() const {#nsps}

List of network service providers currently visible to the hardware

### int WimaxDevice::rssi() const {#rssi}

RSSI of the current radio link in dBm. This value indicates how strong the raw received RF signal from the base station is, but does not indicate the overall quality of the radio link.

### \[signal\] void WimaxDevice::rssiChanged(*int*) {#rssiChanged}

The device changed its RSSI

### int WimaxDevice::txPower() const {#txPower}

Average power of the last burst transmitted by the device, in units of 0.5 dBm. i.e. a TxPower of -11 represents an actual device TX power of -5.5 dBm.

### \[signal\] void WimaxDevice::txPowerChanged(*int*) {#txPowerChanged}

The device changed its TxPower.

### \[override virtual\] NetworkManager::Device::Type WimaxDevice::type() const {#type}

Reimplements: [Device::type() const](networkmanager-device.md#type).

Return the type
