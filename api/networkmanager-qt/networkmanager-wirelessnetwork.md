---
title: "NetworkManager::WirelessNetwork Class"
description: "This class represents a wireless network, which aggregates all access points with the same SSID."
---

# NetworkManager::WirelessNetwork Class

This class represents a wireless network, which aggregates all access points with the same SSID. [More...](#details)

- **Header:** `#include <NetworkManagerQt/WirelessNetwork>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](networkmanager-wirelessnetwork-members.md)

## Public Types

- [WirelessNetwork::List](#List-typedef)
- [WirelessNetwork::Ptr](#Ptr-typedef)

## Public Functions

- [AccessPoint::List accessPoints() const](#accessPoints)
- [QString device() const](#device)
- [AccessPoint::Ptr referenceAccessPoint() const](#referenceAccessPoint)
- [int signalStrength() const](#signalStrength)
- [QString ssid() const](#ssid)

## Signals

- [void disappeared(const QString &ssid)](#disappeared)
- [void referenceAccessPointChanged(const QString &apUni)](#referenceAccessPointChanged)
- [void signalStrengthChanged(int strength)](#signalStrengthChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### WirelessNetwork::List {#List-typedef}

### WirelessNetwork::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### AccessPoint::List WirelessNetwork::accessPoints() const {#accessPoints}

List of access points

> **Warning:** Subject to change, do not store!

### QString WirelessNetwork::device() const {#device}

The uni of device associated with this network.

### \[signal\] void WirelessNetwork::disappeared(const QString &*ssid*) {#disappeared}

Indicate that this network has no more access points (meaning the network has disappeared from view of the network interface)

`ssid` the SSID of this network

### AccessPoint::Ptr WirelessNetwork::referenceAccessPoint() const {#referenceAccessPoint}

The uni of the current 'best' (strongest) Access Point. Note that this may change or disappear over time. Get the Access Point object using [WirelessDevice::findAccessPoint](networkmanager-wirelessdevice.md#findAccessPoint)() on the NetworkInterface this network was obtained from. Use [WirelessDevice::accessPointDisappeared](networkmanager-wirelessdevice.md#accessPointDisappeared)() or [WirelessNetwork::referenceAccessPointChanged](networkmanager-wirelessnetwork.md#referenceAccessPointChanged)() to detect this.

### \[signal\] void WirelessNetwork::referenceAccessPointChanged(const QString &*apUni*) {#referenceAccessPointChanged}

Indicate that the reference access point changed

`apUni` new access point or empty string if none

### int WirelessNetwork::signalStrength() const {#signalStrength}

Signal strength of the network. Syntactic sugar around tracking the reference access point and watching its signal strength

### \[signal\] void WirelessNetwork::signalStrengthChanged(int *strength*) {#signalStrengthChanged}

Indicate that the signal strength changed

`strength` strength as a percentage.

### QString WirelessNetwork::ssid() const {#ssid}

ESSID of the network
