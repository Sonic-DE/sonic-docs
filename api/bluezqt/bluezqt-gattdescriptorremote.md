---
title: "BluezQt::GattDescriptorRemote Class"
description: "Bluetooth LE GATT descriptor."
---

# BluezQt::GattDescriptorRemote Class

Bluetooth LE GATT descriptor. [More...](#details)

- **Header:** `#include <BluezQt/GattDescriptorRemote>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-gattdescriptorremote-members.md)

## Properties

- [\[read-only\] characteristic : const GattCharacteristicRemotePtr](#characteristic-prop)
- [\[read-only\] flags : QStringList](#flags-prop)
- [\[read-only\] handle : quint16](#handle-prop)
- [\[read-only\] ubi : const QString](#ubi-prop)
- [\[read-only\] uuid : QString](#uuid-prop)
- [\[read-only\] value : QByteArray](#value-prop)

## Public Functions

- [BluezQt::GattCharacteristicRemotePtr characteristic() const](#characteristic)
- [QStringList flags() const](#flags)
- [quint16 handle() const](#handle)
- [BluezQt::PendingCall \*setHandle(quint16 handle)](#setHandle)
- [BluezQt::GattDescriptorRemotePtr toSharedPtr() const](#toSharedPtr)
- [QString ubi() const](#ubi)
- [QString uuid() const](#uuid)
- [QByteArray value() const](#value)

## Public Slots

- [BluezQt::PendingCall \*readValue(const QVariantMap &options)](#readValue)
- [BluezQt::PendingCall \*writeValue(const QByteArray &value, const QVariantMap &options)](#writeValue)

## Signals

- [void descriptorChanged(BluezQt::GattDescriptorRemotePtr descriptor)](#descriptorChanged)
- [void flagsChanged(QStringList flags)](#flagsChanged)
- [void handleChanged(quint16 handle)](#handleChanged)
- [void uuidChanged(const QString &uuid)](#uuidChanged)
- [void valueChanged(const QByteArray value)](#valueChanged)

## Detailed Description {#details}

This class represents a Bluetooth LE GATT descriptor for the clients.

## Property Documentation {#property-documentation}

### \[read-only\] characteristic : const GattCharacteristicRemotePtr {#characteristic-prop}

**Access functions:**

- `BluezQt::GattCharacteristicRemotePtr` **[characteristic](bluezqt-gattdescriptorremote.md#characteristic)**() const

### \[read-only\] flags : QStringList {#flags-prop}

**Access functions:**

- `QStringList` **[flags](bluezqt-gattdescriptorremote.md#flags)**() const

**Notifier signal:**

- `void` **[flagsChanged](bluezqt-gattdescriptorremote.md#flagsChanged)**(`QStringList` *flags*)

### \[read-only\] handle : quint16 {#handle-prop}

**Access functions:**

- `quint16` **[handle](bluezqt-gattdescriptorremote.md#handle)**() const

**Notifier signal:**

- `void` **[handleChanged](bluezqt-gattdescriptorremote.md#handleChanged)**(`quint16` *handle*)

### \[read-only\] ubi : const QString {#ubi-prop}

**Access functions:**

- `QString` **[ubi](bluezqt-gattdescriptorremote.md#ubi)**() const

### \[read-only\] uuid : QString {#uuid-prop}

**Access functions:**

- `QString` **[uuid](bluezqt-gattdescriptorremote.md#uuid)**() const

**Notifier signal:**

- `void` **[uuidChanged](bluezqt-gattdescriptorremote.md#uuidChanged)**(const `QString` &*uuid*)

### \[read-only\] value : QByteArray {#value-prop}

**Access functions:**

- `QByteArray` **[value](bluezqt-gattdescriptorremote.md#value)**() const

**Notifier signal:**

- `void` **[valueChanged](bluezqt-gattdescriptorremote.md#valueChanged)**(const `QByteArray` *value*)

## Member Function Documentation {#member-function-documentation}

### BluezQt::GattCharacteristicRemotePtr GattDescriptorRemote::characteristic() const {#characteristic}

Returns the characteristic that owns that descriptor.

> **Note:** Getter function for property [characteristic](bluezqt-gattdescriptorremote.md#characteristic-prop).

### \[signal\] void GattDescriptorRemote::descriptorChanged(BluezQt::GattDescriptorRemotePtr *descriptor*) {#descriptorChanged}

Indicates that at least one of the descriptors's properties has changed.

### QStringList GattDescriptorRemote::flags() const {#flags}

Returns flags the descriptor.

> **Note:** Getter function for property [flags](bluezqt-gattdescriptorremote.md#flags-prop).

### \[signal\] void GattDescriptorRemote::flagsChanged(QStringList *flags*) {#flagsChanged}

Indicates that descriptor's `flags` have changed.

> **Note:** Notifier signal for property [flags](bluezqt-gattdescriptorremote.md#flags-prop).

### quint16 GattDescriptorRemote::handle() const {#handle}

Returns descriptor handle.

> **Note:** Getter function for property [handle](bluezqt-gattdescriptorremote.md#handle-prop).

*See also* [setHandle](bluezqt-gattdescriptorremote.md#setHandle)()

### \[signal\] void GattDescriptorRemote::handleChanged(quint16 *handle*) {#handleChanged}

Indicates that descriptor's `handle` has changed.

> **Note:** Notifier signal for property [handle](bluezqt-gattdescriptorremote.md#handle-prop).

### \[slot\] BluezQt::PendingCall \*GattDescriptorRemote::readValue(const QVariantMap &*options*) {#readValue}

Read the value of the GATT descriptor.

Issues a request to read the value of the descriptor and returns the value if the operation was successful.

Possible errors:

- [PendingCall::NotReady](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::InProgress](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::AlreadyConnected](bluezqt-pendingcall.md#Error-enum)

Returns [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) pending call.

### BluezQt::PendingCall \*GattDescriptorRemote::setHandle(quint16 *handle*) {#setHandle}

Sets the descriptor `handle`.

Returns void pending call.

*See also* [handle](bluezqt-gattdescriptorremote.md#handle)()

### BluezQt::GattDescriptorRemotePtr GattDescriptorRemote::toSharedPtr() const {#toSharedPtr}

Returns a shared pointer from this.

### QString GattDescriptorRemote::ubi() const {#ubi}

Returns the UBI of the GATT descriptor.

Example UBI: "/org/bluez/hci0/dev\_40\_79\_6A\_0C\_39\_75"

> **Note:** Getter function for property [ubi](bluezqt-gattdescriptorremote.md#ubi-prop).

### QString GattDescriptorRemote::uuid() const {#uuid}

Returns the uuid of the descriptor.

> **Note:** Getter function for property [uuid](bluezqt-gattdescriptorremote.md#uuid-prop).

### \[signal\] void GattDescriptorRemote::uuidChanged(const QString &*uuid*) {#uuidChanged}

Indicates that descriptor's `uuid` has changed.

> **Note:** Notifier signal for property [uuid](bluezqt-gattdescriptorremote.md#uuid-prop).

### QByteArray GattDescriptorRemote::value() const {#value}

Returns the value of the descriptor.

> **Note:** Getter function for property [value](bluezqt-gattdescriptorremote.md#value-prop).

### \[signal\] void GattDescriptorRemote::valueChanged(const QByteArray *value*) {#valueChanged}

Indicates that descriptor's `value` has changed.

> **Note:** Notifier signal for property [value](bluezqt-gattdescriptorremote.md#value-prop).

### \[slot\] BluezQt::PendingCall \*GattDescriptorRemote::writeValue(const QByteArray &*value*, const QVariantMap &*options*) {#writeValue}

Write the value of the GATT descriptor.

Issues a request to write the value of the descriptor.

Possible errors:

- [PendingCall::NotReady](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::InProgress](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::AlreadyConnected](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.
