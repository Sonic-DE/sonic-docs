---
title: "NetworkManager::GreDevice Class"
description: "A gre device interface. renamed to IpTunnelDevice. This class is deprecated. We strongly advise against using it in new code."
---

# NetworkManager::GreDevice Class

A gre device interface. renamed to [IpTunnelDevice](networkmanager-iptunneldevice.md). **This class is deprecated. We strongly advise against using it in new code.** [More...](#details)

- **Header:** `#include <NetworkManagerQt/GreDevice>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Device](networkmanager-device.md)
- **Status:** Deprecated

[List of all members, including inherited members](networkmanager-gredevice-members.md)

## Public Types

- [GreDevice::List](#List-typedef)
- [GreDevice::Ptr](#Ptr-typedef)

## Properties

- [\[read-only\] inputFlags : ushort](#inputFlags-prop)
- [\[read-only\] inputKey : uint](#inputKey-prop)
- [\[read-only\] localEnd : QString](#localEnd-prop)
- [\[read-only\] outputFlags : ushort](#outputFlags-prop)
- [\[read-only\] outputKey : uint](#outputKey-prop)
- [\[read-only\] parent : QString](#parent-prop)
- [\[read-only\] pathMtuDiscovery : bool](#pathMtuDiscovery-prop)
- [\[read-only\] remoteEnd : QString](#remoteEnd-prop)
- [\[read-only\] tos : uchar](#tos-prop)
- [\[read-only\] ttl : uchar](#ttl-prop)

## Public Functions

- [GreDevice(const QString &path, QObject \*parent = nullptr)](#GreDevice)
- [ushort inputFlags() const](#inputFlags)
- [uint inputKey() const](#inputKey)
- [QString localEnd() const](#localEnd)
- [ushort outputFlags() const](#outputFlags)
- [uint outputKey() const](#outputKey)
- [QString parent() const](#parent)
- [bool pathMtuDiscovery() const](#pathMtuDiscovery)
- [QString remoteEnd() const](#remoteEnd)
- [uchar tos() const](#tos)
- [uchar ttl() const](#ttl)
- [NetworkManager::Device::Type type() const](#type)

## Signals

- [void inputFlagsChanged(ushort inputflags)](#inputFlagsChanged)
- [void inputKeyChanged(uint inputKey)](#inputKeyChanged)
- [void localEndChanged(const QString &localEnd)](#localEndChanged)
- [void outputFlagsChanged(ushort outputFlags)](#outputFlagsChanged)
- [void outputKeyChanged(uint outputKey)](#outputKeyChanged)
- [void parentChanged(const QString &parent)](#parentChanged)
- [void pathMtuDiscoveryChanged(bool pathMtuDiscovery)](#pathMtuDiscoveryChanged)
- [void remoteEndChanged(const QString &remoteEnd)](#remoteEndChanged)
- [void tosChanged(uchar tos)](#tosChanged)
- [void ttlChanged(uchar ttl)](#ttlChanged)

**This class is deprecated. We strongly advise against using it in new code.**

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### GreDevice::List {#List-typedef}

### GreDevice::Ptr {#Ptr-typedef}

## Property Documentation {#property-documentation}

### \[read-only\] inputFlags : ushort {#inputFlags-prop}

**Access functions:**

- `ushort` **[inputFlags](networkmanager-gredevice.md#inputFlags)**() const

**Notifier signal:**

- `void` **[inputFlagsChanged](networkmanager-gredevice.md#inputFlagsChanged)**(`ushort` *inputflags*)

### \[read-only\] inputKey : uint {#inputKey-prop}

**Access functions:**

- `uint` **[inputKey](networkmanager-gredevice.md#inputKey)**() const

**Notifier signal:**

- `void` **[inputKeyChanged](networkmanager-gredevice.md#inputKeyChanged)**(`uint` *inputKey*)

### \[read-only\] localEnd : QString {#localEnd-prop}

**Access functions:**

- `QString` **[localEnd](networkmanager-gredevice.md#localEnd)**() const

**Notifier signal:**

- `void` **[localEndChanged](networkmanager-gredevice.md#localEndChanged)**(const `QString` &*localEnd*)

### \[read-only\] outputFlags : ushort {#outputFlags-prop}

**Access functions:**

- `ushort` **[outputFlags](networkmanager-gredevice.md#outputFlags)**() const

**Notifier signal:**

- `void` **[outputFlagsChanged](networkmanager-gredevice.md#outputFlagsChanged)**(`ushort` *outputFlags*)

### \[read-only\] outputKey : uint {#outputKey-prop}

**Access functions:**

- `uint` **[outputKey](networkmanager-gredevice.md#outputKey)**() const

**Notifier signal:**

- `void` **[outputKeyChanged](networkmanager-gredevice.md#outputKeyChanged)**(`uint` *outputKey*)

### \[read-only\] parent : QString {#parent-prop}

**Access functions:**

- `QString` **[parent](networkmanager-gredevice.md#parent)**() const

**Notifier signal:**

- `void` **[parentChanged](networkmanager-gredevice.md#parentChanged)**(const `QString` &*parent*)

### \[read-only\] pathMtuDiscovery : bool {#pathMtuDiscovery-prop}

**Access functions:**

- `bool` **[pathMtuDiscovery](networkmanager-gredevice.md#pathMtuDiscovery)**() const

**Notifier signal:**

- `void` **[pathMtuDiscoveryChanged](networkmanager-gredevice.md#pathMtuDiscoveryChanged)**(`bool` *pathMtuDiscovery*)

### \[read-only\] remoteEnd : QString {#remoteEnd-prop}

**Access functions:**

- `QString` **[remoteEnd](networkmanager-gredevice.md#remoteEnd)**() const

**Notifier signal:**

- `void` **[remoteEndChanged](networkmanager-gredevice.md#remoteEndChanged)**(const `QString` &*remoteEnd*)

### \[read-only\] tos : uchar {#tos-prop}

**Access functions:**

- `uchar` **[tos](networkmanager-gredevice.md#tos)**() const

**Notifier signal:**

- `void` **[tosChanged](networkmanager-gredevice.md#tosChanged)**(`uchar` *tos*)

### \[read-only\] ttl : uchar {#ttl-prop}

**Access functions:**

- `uchar` **[ttl](networkmanager-gredevice.md#ttl)**() const

**Notifier signal:**

- `void` **[ttlChanged](networkmanager-gredevice.md#ttlChanged)**(`uchar` *ttl*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] GreDevice::GreDevice(const QString &*path*, QObject \**parent* = nullptr) {#GreDevice}

### ushort GreDevice::inputFlags() const {#inputFlags}

> **Note:** Getter function for property [inputFlags](networkmanager-gredevice.md#inputFlags-prop).

### \[signal\] void GreDevice::inputFlagsChanged(ushort *inputflags*) {#inputFlagsChanged}

> **Note:** Notifier signal for property [inputFlags](networkmanager-gredevice.md#inputFlags-prop).

### uint GreDevice::inputKey() const {#inputKey}

> **Note:** Getter function for property [inputKey](networkmanager-gredevice.md#inputKey-prop).

### \[signal\] void GreDevice::inputKeyChanged(uint *inputKey*) {#inputKeyChanged}

> **Note:** Notifier signal for property [inputKey](networkmanager-gredevice.md#inputKey-prop).

### QString GreDevice::localEnd() const {#localEnd}

> **Note:** Getter function for property [localEnd](networkmanager-gredevice.md#localEnd-prop).

### \[signal\] void GreDevice::localEndChanged(const QString &*localEnd*) {#localEndChanged}

> **Note:** Notifier signal for property [localEnd](networkmanager-gredevice.md#localEnd-prop).

### ushort GreDevice::outputFlags() const {#outputFlags}

> **Note:** Getter function for property [outputFlags](networkmanager-gredevice.md#outputFlags-prop).

### \[signal\] void GreDevice::outputFlagsChanged(ushort *outputFlags*) {#outputFlagsChanged}

> **Note:** Notifier signal for property [outputFlags](networkmanager-gredevice.md#outputFlags-prop).

### uint GreDevice::outputKey() const {#outputKey}

> **Note:** Getter function for property [outputKey](networkmanager-gredevice.md#outputKey-prop).

### \[signal\] void GreDevice::outputKeyChanged(uint *outputKey*) {#outputKeyChanged}

> **Note:** Notifier signal for property [outputKey](networkmanager-gredevice.md#outputKey-prop).

### QString GreDevice::parent() const {#parent}

> **Note:** Getter function for property [parent](networkmanager-gredevice.md#parent-prop).

### \[signal\] void GreDevice::parentChanged(const QString &*parent*) {#parentChanged}

> **Note:** Notifier signal for property [parent](networkmanager-gredevice.md#parent-prop).

### bool GreDevice::pathMtuDiscovery() const {#pathMtuDiscovery}

> **Note:** Getter function for property [pathMtuDiscovery](networkmanager-gredevice.md#pathMtuDiscovery-prop).

### \[signal\] void GreDevice::pathMtuDiscoveryChanged(bool *pathMtuDiscovery*) {#pathMtuDiscoveryChanged}

> **Note:** Notifier signal for property [pathMtuDiscovery](networkmanager-gredevice.md#pathMtuDiscovery-prop).

### QString GreDevice::remoteEnd() const {#remoteEnd}

> **Note:** Getter function for property [remoteEnd](networkmanager-gredevice.md#remoteEnd-prop).

### \[signal\] void GreDevice::remoteEndChanged(const QString &*remoteEnd*) {#remoteEndChanged}

> **Note:** Notifier signal for property [remoteEnd](networkmanager-gredevice.md#remoteEnd-prop).

### uchar GreDevice::tos() const {#tos}

> **Note:** Getter function for property [tos](networkmanager-gredevice.md#tos-prop).

### \[signal\] void GreDevice::tosChanged(uchar *tos*) {#tosChanged}

> **Note:** Notifier signal for property [tos](networkmanager-gredevice.md#tos-prop).

### uchar GreDevice::ttl() const {#ttl}

> **Note:** Getter function for property [ttl](networkmanager-gredevice.md#ttl-prop).

### \[signal\] void GreDevice::ttlChanged(uchar *ttl*) {#ttlChanged}

> **Note:** Notifier signal for property [ttl](networkmanager-gredevice.md#ttl-prop).

### \[override virtual\] NetworkManager::Device::Type GreDevice::type() const {#type}

Reimplements: [Device::type() const](networkmanager-device.md#type).
