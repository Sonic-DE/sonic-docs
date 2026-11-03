---
title: "NetworkManager::WireGuardDevice Class"
description: "A WireGuard device interface."
---

# NetworkManager::WireGuardDevice Class

A WireGuard device interface. [More...](#details)

- **Header:** `#include <NetworkManagerQt/WireGuardDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Device](networkmanager-device.md)

[List of all members, including inherited members](networkmanager-wireguarddevice-members.md)

## Public Types

- [WireGuardDevice::List](#List-typedef)
- [WireGuardDevice::Ptr](#Ptr-typedef)

## Properties

- [\[read-only\] fwMark : uint](#fwMark-prop)
- [\[read-only\] listenPort : uint](#listenPort-prop)
- [\[read-only\] publicKey : QByteArray](#publicKey-prop)

## Public Functions

- [WireGuardDevice(const QString &path, QObject \*parent = nullptr)](#WireGuardDevice)
- [uint fwMark() const](#fwMark)
- [uint listenPort() const](#listenPort)
- [QByteArray publicKey() const](#publicKey)

## Signals

- [void fwMarkChanged(uint fwMark)](#fwMarkChanged)
- [void listenPortChanged(uint listenPort)](#listenPortChanged)
- [void publicKeyChanged(const QByteArray &publicKey)](#publicKeyChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### WireGuardDevice::List {#List-typedef}

### WireGuardDevice::Ptr {#Ptr-typedef}

## Property Documentation {#property-documentation}

### \[read-only\] fwMark : uint {#fwMark-prop}

**Access functions:**

- `uint` **[fwMark](networkmanager-wireguarddevice.md#fwMark)**() const

**Notifier signal:**

- `void` **[fwMarkChanged](networkmanager-wireguarddevice.md#fwMarkChanged)**(`uint` *fwMark*)

### \[read-only\] listenPort : uint {#listenPort-prop}

**Access functions:**

- `uint` **[listenPort](networkmanager-wireguarddevice.md#listenPort)**() const

**Notifier signal:**

- `void` **[listenPortChanged](networkmanager-wireguarddevice.md#listenPortChanged)**(`uint` *listenPort*)

### \[read-only\] publicKey : QByteArray {#publicKey-prop}

**Access functions:**

- `QByteArray` **[publicKey](networkmanager-wireguarddevice.md#publicKey)**() const

**Notifier signal:**

- `void` **[publicKeyChanged](networkmanager-wireguarddevice.md#publicKeyChanged)**(const `QByteArray` &*publicKey*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] WireGuardDevice::WireGuardDevice(const QString &*path*, QObject \**parent* = nullptr) {#WireGuardDevice}

### uint WireGuardDevice::fwMark() const {#fwMark}

Optional 32-bit mark used to set routing policy for outgoing encrypted packets. See: ip-rule(8)

> **Note:** Getter function for property [fwMark](networkmanager-wireguarddevice.md#fwMark-prop).

### \[signal\] void WireGuardDevice::fwMarkChanged(uint *fwMark*) {#fwMarkChanged}

Emitted when the fwmark of this device have changed

> **Note:** Notifier signal for property [fwMark](networkmanager-wireguarddevice.md#fwMark-prop).

### uint WireGuardDevice::listenPort() const {#listenPort}

Local UDP listening port.

> **Note:** Getter function for property [listenPort](networkmanager-wireguarddevice.md#listenPort-prop).

### \[signal\] void WireGuardDevice::listenPortChanged(uint *listenPort*) {#listenPortChanged}

Emitted when the listen port of this device has changed

> **Note:** Notifier signal for property [listenPort](networkmanager-wireguarddevice.md#listenPort-prop).

### QByteArray WireGuardDevice::publicKey() const {#publicKey}

32-byte public WireGuard key.

> **Note:** Getter function for property [publicKey](networkmanager-wireguarddevice.md#publicKey-prop).

### \[signal\] void WireGuardDevice::publicKeyChanged(const QByteArray &*publicKey*) {#publicKeyChanged}

Emitted when the public key of this device has changed

> **Note:** Notifier signal for property [publicKey](networkmanager-wireguarddevice.md#publicKey-prop).
