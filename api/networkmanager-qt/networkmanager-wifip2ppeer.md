---
title: "NetworkManager::WifiP2PPeer Class"
description: "Represents a wifip2p peer. This class was introduced in Qt 6.20."
---

# NetworkManager::WifiP2PPeer Class

Represents a wifip2p peer. This class was introduced in Qt 6.20. [More...](#details)

- **Header:** `#include <NetworkManagerQt/WifiP2PPeer>`
- **Since:** Qt 6.20
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](networkmanager-wifip2ppeer-members.md)

## Public Types

- [\[alias\] WifiP2PPeer::Ptr](#Ptr-typedef)

## Properties

- [\[read-only\] flags : uint](#flags-prop)
- [\[read-only\] hardwareAddress : QString](#hardwareAddress-prop)
- [\[read-only\] lastSeen : int](#lastSeen-prop)
- [\[read-only\] manufacturer : QString](#manufacturer-prop)
- [\[read-only\] model : QString](#model-prop)
- [\[read-only\] modelNumber : QString](#modelNumber-prop)
- [\[read-only\] name : QString](#name-prop)
- [\[read-only\] serial : QString](#serial-prop)
- [\[read-only\] strength : uchar](#strength-prop)
- [\[read-only\] wfdIEs : QByteArray](#wfdIEs-prop)

## Public Functions

- [WifiP2PPeer(const QString &path, QObject \*parent = nullptr)](#WifiP2PPeer)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### \[alias\] WifiP2PPeer::Ptr {#Ptr-typedef}

## Property Documentation {#property-documentation}

### \[read-only\] flags : uint {#flags-prop}

**Access functions:**

- `uint` **flags**() const

**Notifier signal:**

- `void` **flagsChanged**(`uint` *flags*)

### \[read-only\] hardwareAddress : QString {#hardwareAddress-prop}

**Access functions:**

- `QString` **hardwareAddress**() const

**Notifier signal:**

- `void` **hardwareAddressChanged**(const `QString` &*hardwareAddress*)

### \[read-only\] lastSeen : int {#lastSeen-prop}

**Access functions:**

- `int` **lastSeen**() const

**Notifier signal:**

- `void` **lastSeenChanged**(`int` *lastSeen*)

### \[read-only\] manufacturer : QString {#manufacturer-prop}

**Access functions:**

- `QString` **manufacturer**() const

**Notifier signal:**

- `void` **manufacturerChanged**(const `QString` &*manufacturer*)

### \[read-only\] model : QString {#model-prop}

**Access functions:**

- `QString` **model**() const

**Notifier signal:**

- `void` **modelChanged**(const `QString` &*model*)

### \[read-only\] modelNumber : QString {#modelNumber-prop}

**Access functions:**

- `QString` **modelNumber**() const

**Notifier signal:**

- `void` **modelNumberChanged**(const `QString` &*modelNumber*)

### \[read-only\] name : QString {#name-prop}

**Access functions:**

- `QString` **name**() const

**Notifier signal:**

- `void` **nameChanged**(const `QString` &*name*)

### \[read-only\] serial : QString {#serial-prop}

**Access functions:**

- `QString` **serial**() const

**Notifier signal:**

- `void` **serialChanged**(const `QString` &*serial*)

### \[read-only\] strength : uchar {#strength-prop}

**Access functions:**

- `uchar` **strength**() const

**Notifier signal:**

- `void` **strengthChanged**(`uchar` *strength*)

### \[read-only\] wfdIEs : QByteArray {#wfdIEs-prop}

**Access functions:**

- `QByteArray` **wfdIEs**() const

**Notifier signal:**

- `void` **wfdIEsChanged**(const `QByteArray` &*wfdIEs*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] WifiP2PPeer::WifiP2PPeer(const QString &*path*, QObject \**parent* = nullptr) {#WifiP2PPeer}
