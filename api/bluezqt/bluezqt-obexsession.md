---
title: "BluezQt::ObexSession Class"
description: "OBEX session."
---

# BluezQt::ObexSession Class

OBEX session. [More...](#details)

- **Header:** `#include <BluezQt/ObexSession>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-obexsession-members.md)

## Properties

- [\[read-only\] channel : quint8](#channel-prop)
- [\[read-only\] destination : QString](#destination-prop)
- [\[read-only\] root : QString](#root-prop)
- [\[read-only\] source : QString](#source-prop)
- [\[read-only\] target : QString](#target-prop)

## Public Functions

- [quint8 channel() const](#channel)
- [QString destination() const](#destination)
- [BluezQt::PendingCall \*getCapabilities()](#getCapabilities)
- [QDBusObjectPath objectPath() const](#objectPath)
- [QString root() const](#root)
- [QString source() const](#source)
- [QString target() const](#target)
- [BluezQt::ObexSessionPtr toSharedPtr() const](#toSharedPtr)

## Detailed Description {#details}

This class represents an OBEX session.

## Property Documentation {#property-documentation}

### \[read-only\] channel : quint8 {#channel-prop}

**Access functions:**

- `quint8` **[channel](bluezqt-obexsession.md#channel)**() const

### \[read-only\] destination : QString {#destination-prop}

**Access functions:**

- `QString` **[destination](bluezqt-obexsession.md#destination)**() const

### \[read-only\] root : QString {#root-prop}

**Access functions:**

- `QString` **[root](bluezqt-obexsession.md#root)**() const

### \[read-only\] source : QString {#source-prop}

**Access functions:**

- `QString` **[source](bluezqt-obexsession.md#source)**() const

### \[read-only\] target : QString {#target-prop}

**Access functions:**

- `QString` **[target](bluezqt-obexsession.md#target)**() const

## Member Function Documentation {#member-function-documentation}

### quint8 ObexSession::channel() const {#channel}

Returns the Bluetooth channel.

> **Note:** Getter function for property [channel](bluezqt-obexsession.md#channel-prop).

### QString ObexSession::destination() const {#destination}

Returns the address of the Bluetooth device.

> **Note:** Getter function for property [destination](bluezqt-obexsession.md#destination-prop).

*See also* [Manager::deviceForAddress](bluezqt-manager.md#deviceForAddress)()

### BluezQt::PendingCall \*ObexSession::getCapabilities() {#getCapabilities}

Returns the remote device capabilities.

Possible errors:

- [PendingCall::NotSupported](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns [QString](https://doc.qt.io/qt-6/qstring.html) pending call.

### QDBusObjectPath ObexSession::objectPath() const {#objectPath}

Returns the D-Bus object path of the session.

### QString ObexSession::root() const {#root}

Returns the root path.

> **Note:** Getter function for property [root](bluezqt-obexsession.md#root-prop).

### QString ObexSession::source() const {#source}

Returns the address of the Bluetooth adapter.

> **Note:** Getter function for property [source](bluezqt-obexsession.md#source-prop).

*See also* [Manager::adapterForAddress](bluezqt-manager.md#adapterForAddress)()

### QString ObexSession::target() const {#target}

Returns the target UUID.

> **Note:** Getter function for property [target](bluezqt-obexsession.md#target-prop).

### BluezQt::ObexSessionPtr ObexSession::toSharedPtr() const {#toSharedPtr}

Returns a shared pointer from this.
