---
title: "NetworkManager::IpTunnelDevice Class"
description: "A Ip Tunnel device interface."
---

# NetworkManager::IpTunnelDevice Class

A Ip Tunnel device interface. [More...](#details)

- **Header:** `#include <NetworkManagerQt/IpTunnelDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Device](networkmanager-device.md)

[List of all members, including inherited members](networkmanager-iptunneldevice-members.md)

## Public Types

- [IpTunnelDevice::List](#List-typedef)
- [IpTunnelDevice::Ptr](#Ptr-typedef)

## Properties

- [\[read-only\] encapsulationLimit : uchar](#encapsulationLimit-prop)
- [\[read-only\] flowLabel : uint](#flowLabel-prop)
- [\[read-only\] inputKey : QString](#inputKey-prop)
- [\[read-only\] local : QString](#local-prop)
- [\[read-only\] mode : uint](#mode-prop)
- [\[read-only\] outputKey : QString](#outputKey-prop)
- [\[read-only\] parent : NetworkManager::Device::Ptr](#parent-prop)
- [\[read-only\] pathMtuDiscovery : bool](#pathMtuDiscovery-prop)
- [\[read-only\] remote : QString](#remote-prop)
- [\[read-only\] tos : uchar](#tos-prop)
- [\[read-only\] ttl : uchar](#ttl-prop)

## Public Functions

- [IpTunnelDevice(const QString &path, QObject \*parent = nullptr)](#IpTunnelDevice)
- [uchar encapsulationLimit() const](#encapsulationLimit)
- [uint flowLabel() const](#flowLabel)
- [QString inputKey() const](#inputKey)
- [QString local() const](#local)
- [uint mode() const](#mode)
- [QString outputKey() const](#outputKey)
- [NetworkManager::Device::Ptr parent() const](#parent)
- [bool pathMtuDiscovery() const](#pathMtuDiscovery)
- [QString remote() const](#remote)
- [uchar tos() const](#tos)
- [uchar ttl() const](#ttl)

## Signals

- [void encapsulationLimitChanged(uchar limit)](#encapsulationLimitChanged)
- [void flowLabelChanged(uint flowLabel)](#flowLabelChanged)
- [void inputKeyChanged(const QString &inputKey)](#inputKeyChanged)
- [void localChanged(const QString &local)](#localChanged)
- [void modeChanged(uint mode)](#modeChanged)
- [void outputKeyChanged(const QString &outputKey)](#outputKeyChanged)
- [void parentChanged(const QString &parent)](#parentChanged)
- [void pathMtuDiscoveryChanged(bool pathMtuDiscovery)](#pathMtuDiscoveryChanged)
- [void remoteChanged(const QString &remote)](#remoteChanged)
- [void tosChanged(uchar tos)](#tosChanged)
- [void ttlChanged(uchar ttl)](#ttlChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### IpTunnelDevice::List {#List-typedef}

### IpTunnelDevice::Ptr {#Ptr-typedef}

## Property Documentation {#property-documentation}

### \[read-only\] encapsulationLimit : uchar {#encapsulationLimit-prop}

**Access functions:**

- `uchar` **[encapsulationLimit](networkmanager-iptunneldevice.md#encapsulationLimit)**() const

**Notifier signal:**

- `void` **[encapsulationLimitChanged](networkmanager-iptunneldevice.md#encapsulationLimitChanged)**(`uchar` *limit*)

### \[read-only\] flowLabel : uint {#flowLabel-prop}

**Access functions:**

- `uint` **[flowLabel](networkmanager-iptunneldevice.md#flowLabel)**() const

**Notifier signal:**

- `void` **[flowLabelChanged](networkmanager-iptunneldevice.md#flowLabelChanged)**(`uint` *flowLabel*)

### \[read-only\] inputKey : QString {#inputKey-prop}

**Access functions:**

- `QString` **[inputKey](networkmanager-iptunneldevice.md#inputKey)**() const

**Notifier signal:**

- `void` **[inputKeyChanged](networkmanager-iptunneldevice.md#inputKeyChanged)**(const `QString` &*inputKey*)

### \[read-only\] local : QString {#local-prop}

**Access functions:**

- `QString` **[local](networkmanager-iptunneldevice.md#local)**() const

**Notifier signal:**

- `void` **[localChanged](networkmanager-iptunneldevice.md#localChanged)**(const `QString` &*local*)

### \[read-only\] mode : uint {#mode-prop}

**Access functions:**

- `uint` **[mode](networkmanager-iptunneldevice.md#mode)**() const

**Notifier signal:**

- `void` **[modeChanged](networkmanager-iptunneldevice.md#modeChanged)**(`uint` *mode*)

### \[read-only\] outputKey : QString {#outputKey-prop}

**Access functions:**

- `QString` **[outputKey](networkmanager-iptunneldevice.md#outputKey)**() const

**Notifier signal:**

- `void` **[outputKeyChanged](networkmanager-iptunneldevice.md#outputKeyChanged)**(const `QString` &*outputKey*)

### \[read-only\] parent : NetworkManager::Device::Ptr {#parent-prop}

**Access functions:**

- `NetworkManager::Device::Ptr` **[parent](networkmanager-iptunneldevice.md#parent)**() const

**Notifier signal:**

- `void` **[parentChanged](networkmanager-iptunneldevice.md#parentChanged)**(const `QString` &*parent*)

### \[read-only\] pathMtuDiscovery : bool {#pathMtuDiscovery-prop}

**Access functions:**

- `bool` **[pathMtuDiscovery](networkmanager-iptunneldevice.md#pathMtuDiscovery)**() const

**Notifier signal:**

- `void` **[pathMtuDiscoveryChanged](networkmanager-iptunneldevice.md#pathMtuDiscoveryChanged)**(`bool` *pathMtuDiscovery*)

### \[read-only\] remote : QString {#remote-prop}

**Access functions:**

- `QString` **[remote](networkmanager-iptunneldevice.md#remote)**() const

**Notifier signal:**

- `void` **[remoteChanged](networkmanager-iptunneldevice.md#remoteChanged)**(const `QString` &*remote*)

### \[read-only\] tos : uchar {#tos-prop}

**Access functions:**

- `uchar` **[tos](networkmanager-iptunneldevice.md#tos)**() const

**Notifier signal:**

- `void` **[tosChanged](networkmanager-iptunneldevice.md#tosChanged)**(`uchar` *tos*)

### \[read-only\] ttl : uchar {#ttl-prop}

**Access functions:**

- `uchar` **[ttl](networkmanager-iptunneldevice.md#ttl)**() const

**Notifier signal:**

- `void` **[ttlChanged](networkmanager-iptunneldevice.md#ttlChanged)**(`uchar` *ttl*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] IpTunnelDevice::IpTunnelDevice(const QString &*path*, QObject \**parent* = nullptr) {#IpTunnelDevice}

### uchar IpTunnelDevice::encapsulationLimit() const {#encapsulationLimit}

How many additional levels of encapsulation are permitted to be prepended to packets. This property applies only to IPv6 tunnels.

> **Note:** Getter function for property [encapsulationLimit](networkmanager-iptunneldevice.md#encapsulationLimit-prop).

### \[signal\] void IpTunnelDevice::encapsulationLimitChanged(uchar *limit*) {#encapsulationLimitChanged}

Emitted when the encapsulation limit has changed

> **Note:** Notifier signal for property [encapsulationLimit](networkmanager-iptunneldevice.md#encapsulationLimit-prop).

### uint IpTunnelDevice::flowLabel() const {#flowLabel}

The flow label to assign to tunnel packets. This property applies only to IPv6 tunnels.

> **Note:** Getter function for property [flowLabel](networkmanager-iptunneldevice.md#flowLabel-prop).

### \[signal\] void IpTunnelDevice::flowLabelChanged(uint *flowLabel*) {#flowLabelChanged}

Emitted when the flow label has changed

> **Note:** Notifier signal for property [flowLabel](networkmanager-iptunneldevice.md#flowLabel-prop).

### QString IpTunnelDevice::inputKey() const {#inputKey}

The key used for incoming packets.

> **Note:** Getter function for property [inputKey](networkmanager-iptunneldevice.md#inputKey-prop).

### \[signal\] void IpTunnelDevice::inputKeyChanged(const QString &*inputKey*) {#inputKeyChanged}

Emitted when the key used for incoming packets has changed

> **Note:** Notifier signal for property [inputKey](networkmanager-iptunneldevice.md#inputKey-prop).

### QString IpTunnelDevice::local() const {#local}

The local endpoint of the tunnel.

> **Note:** Getter function for property [local](networkmanager-iptunneldevice.md#local-prop).

### \[signal\] void IpTunnelDevice::localChanged(const QString &*local*) {#localChanged}

Emitted when the local endpoint of the tunnel has changed

> **Note:** Notifier signal for property [local](networkmanager-iptunneldevice.md#local-prop).

### uint IpTunnelDevice::mode() const {#mode}

The tunneling mode.

> **Note:** Getter function for property [mode](networkmanager-iptunneldevice.md#mode-prop).

### \[signal\] void IpTunnelDevice::modeChanged(uint *mode*) {#modeChanged}

Emitted when the tunneling mode has changed

> **Note:** Notifier signal for property [mode](networkmanager-iptunneldevice.md#mode-prop).

### QString IpTunnelDevice::outputKey() const {#outputKey}

The key used for outgoing packets.

> **Note:** Getter function for property [outputKey](networkmanager-iptunneldevice.md#outputKey-prop).

### \[signal\] void IpTunnelDevice::outputKeyChanged(const QString &*outputKey*) {#outputKeyChanged}

Emitted when the key used for outgoing packets has changed

> **Note:** Notifier signal for property [outputKey](networkmanager-iptunneldevice.md#outputKey-prop).

### NetworkManager::Device::Ptr IpTunnelDevice::parent() const {#parent}

The object path of the parent device.

> **Note:** Getter function for property [parent](networkmanager-iptunneldevice.md#parent-prop).

### \[signal\] void IpTunnelDevice::parentChanged(const QString &*parent*) {#parentChanged}

Emitted when the parent of this device has changed

> **Note:** Notifier signal for property [parent](networkmanager-iptunneldevice.md#parent-prop).

### bool IpTunnelDevice::pathMtuDiscovery() const {#pathMtuDiscovery}

Whether path MTU discovery is enabled on this tunnel.

> **Note:** Getter function for property [pathMtuDiscovery](networkmanager-iptunneldevice.md#pathMtuDiscovery-prop).

### \[signal\] void IpTunnelDevice::pathMtuDiscoveryChanged(bool *pathMtuDiscovery*) {#pathMtuDiscoveryChanged}

Emitted when the path MTU discovery enablemened has changed

> **Note:** Notifier signal for property [pathMtuDiscovery](networkmanager-iptunneldevice.md#pathMtuDiscovery-prop).

### QString IpTunnelDevice::remote() const {#remote}

The remote endpoint of the tunnel.

> **Note:** Getter function for property [remote](networkmanager-iptunneldevice.md#remote-prop).

### \[signal\] void IpTunnelDevice::remoteChanged(const QString &*remote*) {#remoteChanged}

Emitted when the remote endpoint of the tunnel has changed

> **Note:** Notifier signal for property [remote](networkmanager-iptunneldevice.md#remote-prop).

### uchar IpTunnelDevice::tos() const {#tos}

The type of service (IPv4) or traffic class (IPv6) assigned to tunneled packets.

> **Note:** Getter function for property [tos](networkmanager-iptunneldevice.md#tos-prop).

### \[signal\] void IpTunnelDevice::tosChanged(uchar *tos*) {#tosChanged}

Emitted when the type of service or traffic class assigned to tunneled packets has changed

> **Note:** Notifier signal for property [tos](networkmanager-iptunneldevice.md#tos-prop).

### uchar IpTunnelDevice::ttl() const {#ttl}

The TTL assigned to tunneled packets. 0 is a special value meaning that packets inherit the TTL value

> **Note:** Getter function for property [ttl](networkmanager-iptunneldevice.md#ttl-prop).

### \[signal\] void IpTunnelDevice::ttlChanged(uchar *ttl*) {#ttlChanged}

Emitted when the TTL assigned to tunneled packets has changed

> **Note:** Notifier signal for property [ttl](networkmanager-iptunneldevice.md#ttl-prop).
