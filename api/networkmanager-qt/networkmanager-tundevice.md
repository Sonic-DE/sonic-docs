---
title: "NetworkManager::TunDevice Class"
description: "A tun device interface."
---

# NetworkManager::TunDevice Class

A tun device interface. [More...](#details)

- **Header:** `#include <NetworkManagerQt/TunDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Device](networkmanager-device.md)

[List of all members, including inherited members](networkmanager-tundevice-members.md)

## Public Types

- [TunDevice::List](#List-typedef)
- [TunDevice::Ptr](#Ptr-typedef)

## Properties

- [\[read-only\] group : qlonglong](#group-prop)
- [\[read-only\] hwAddress : QString](#hwAddress-prop)
- [\[read-only\] mode : QString](#mode-prop)
- [\[read-only\] multiQueue : bool](#multiQueue-prop)
- [\[read-only\] noPi : bool](#noPi-prop)
- [\[read-only\] owner : qlonglong](#owner-prop)
- [\[read-only\] vnetHdr : bool](#vnetHdr-prop)

## Public Functions

- [TunDevice(const QString &path, QObject \*parent = nullptr)](#TunDevice)
- [qlonglong group() const](#group)
- [QString hwAddress() const](#hwAddress)
- [QString mode() const](#mode)
- [bool multiQueue() const](#multiQueue)
- [bool noPi() const](#noPi)
- [qlonglong owner() const](#owner)
- [bool vnetHdr() const](#vnetHdr)

## Signals

- [void groupChanged(qlonglong group)](#groupChanged)
- [void hwAddressChanged(const QString &hwAddress)](#hwAddressChanged)
- [void modeChanged(const QString &mode)](#modeChanged)
- [void multiQueueChanged(bool multiQueue)](#multiQueueChanged)
- [void noPiChanged(bool noPi)](#noPiChanged)
- [void ownerChanged(qlonglong owner)](#ownerChanged)
- [void vnetHdrChanged(bool vnetHdr)](#vnetHdrChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### TunDevice::List {#List-typedef}

### TunDevice::Ptr {#Ptr-typedef}

## Property Documentation {#property-documentation}

### \[read-only\] group : qlonglong {#group-prop}

**Access functions:**

- `qlonglong` **[group](networkmanager-tundevice.md#group)**() const

**Notifier signal:**

- `void` **[groupChanged](networkmanager-tundevice.md#groupChanged)**(`qlonglong` *group*)

### \[read-only\] hwAddress : QString {#hwAddress-prop}

**Access functions:**

- `QString` **[hwAddress](networkmanager-tundevice.md#hwAddress)**() const

**Notifier signal:**

- `void` **[hwAddressChanged](networkmanager-tundevice.md#hwAddressChanged)**(const `QString` &*hwAddress*)

### \[read-only\] mode : QString {#mode-prop}

**Access functions:**

- `QString` **[mode](networkmanager-tundevice.md#mode)**() const

**Notifier signal:**

- `void` **[modeChanged](networkmanager-tundevice.md#modeChanged)**(const `QString` &*mode*)

### \[read-only\] multiQueue : bool {#multiQueue-prop}

**Access functions:**

- `bool` **[multiQueue](networkmanager-tundevice.md#multiQueue)**() const

**Notifier signal:**

- `void` **[multiQueueChanged](networkmanager-tundevice.md#multiQueueChanged)**(`bool` *multiQueue*)

### \[read-only\] noPi : bool {#noPi-prop}

**Access functions:**

- `bool` **[noPi](networkmanager-tundevice.md#noPi)**() const

**Notifier signal:**

- `void` **[noPiChanged](networkmanager-tundevice.md#noPiChanged)**(`bool` *noPi*)

### \[read-only\] owner : qlonglong {#owner-prop}

**Access functions:**

- `qlonglong` **[owner](networkmanager-tundevice.md#owner)**() const

**Notifier signal:**

- `void` **[ownerChanged](networkmanager-tundevice.md#ownerChanged)**(`qlonglong` *owner*)

### \[read-only\] vnetHdr : bool {#vnetHdr-prop}

**Access functions:**

- `bool` **[vnetHdr](networkmanager-tundevice.md#vnetHdr)**() const

**Notifier signal:**

- `void` **[vnetHdrChanged](networkmanager-tundevice.md#vnetHdrChanged)**(`bool` *vnetHdr*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] TunDevice::TunDevice(const QString &*path*, QObject \**parent* = nullptr) {#TunDevice}

### qlonglong TunDevice::group() const {#group}

The gid of the tunnel group, or -1 if it has no owner.

> **Note:** Getter function for property [group](networkmanager-tundevice.md#group-prop).

### \[signal\] void TunDevice::groupChanged(qlonglong *group*) {#groupChanged}

Emitted when the gid of the tunnel group has changed

> **Note:** Notifier signal for property [group](networkmanager-tundevice.md#group-prop).

### QString TunDevice::hwAddress() const {#hwAddress}

Hardware address of the device.

> **Note:** Getter function for property [hwAddress](networkmanager-tundevice.md#hwAddress-prop).

### \[signal\] void TunDevice::hwAddressChanged(const QString &*hwAddress*) {#hwAddressChanged}

Emitted when the hardware address of the device has changed

> **Note:** Notifier signal for property [hwAddress](networkmanager-tundevice.md#hwAddress-prop).

### QString TunDevice::mode() const {#mode}

The tunnel mode, either "tun" or "tap".

> **Note:** Getter function for property [mode](networkmanager-tundevice.md#mode-prop).

### \[signal\] void TunDevice::modeChanged(const QString &*mode*) {#modeChanged}

Emitted when the tunnel mode has changed

> **Note:** Notifier signal for property [mode](networkmanager-tundevice.md#mode-prop).

### bool TunDevice::multiQueue() const {#multiQueue}

The tunnel's "TUN\_TAP\_MQ" flag; true if callers can connect to the tap device multiple times, for multiple send/receive queues.

> **Note:** Getter function for property [multiQueue](networkmanager-tundevice.md#multiQueue-prop).

### \[signal\] void TunDevice::multiQueueChanged(bool *multiQueue*) {#multiQueueChanged}

Emitted when the tunnel's "TUN\_TAP\_MQ" flag has changed

> **Note:** Notifier signal for property [multiQueue](networkmanager-tundevice.md#multiQueue-prop).

### bool TunDevice::noPi() const {#noPi}

The tunnel's "TUN\_NO\_PI" flag; true if no protocol info is prepended to the tunnel packets.

> **Note:** Getter function for property [noPi](networkmanager-tundevice.md#noPi-prop).

### \[signal\] void TunDevice::noPiChanged(bool *noPi*) {#noPiChanged}

Emitted when the tunnel's "TUN\_NO\_PI" flag has changed

> **Note:** Notifier signal for property [noPi](networkmanager-tundevice.md#noPi-prop).

### qlonglong TunDevice::owner() const {#owner}

The uid of the tunnel owner, or -1 if it has no owner.

> **Note:** Getter function for property [owner](networkmanager-tundevice.md#owner-prop).

### \[signal\] void TunDevice::ownerChanged(qlonglong *owner*) {#ownerChanged}

Emitted when the uid of the tunnel owner has changed

> **Note:** Notifier signal for property [owner](networkmanager-tundevice.md#owner-prop).

### bool TunDevice::vnetHdr() const {#vnetHdr}

The tunnel's "TUN\_VNET\_HDR" flag; true if the tunnel packets include a virtio network header.

> **Note:** Getter function for property [vnetHdr](networkmanager-tundevice.md#vnetHdr-prop).

### \[signal\] void TunDevice::vnetHdrChanged(bool *vnetHdr*) {#vnetHdrChanged}

Emitted when the tunnel's "TUN\_VNET\_HDR" flag has changed

> **Note:** Notifier signal for property [vnetHdr](networkmanager-tundevice.md#vnetHdr-prop).
