---
title: "BluezQt::GattCharacteristicRemote Class"
description: "Bluetooth LE GATT characteristic."
---

# BluezQt::GattCharacteristicRemote Class

Bluetooth LE GATT characteristic. [More...](#details)

- **Header:** `#include <BluezQt/GattCharacteristicRemote>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-gattcharacteristicremote-members.md)

## Properties

- [\[read-only\] MTU : quint16](#MTU-prop)
- [\[read-only\] descriptors : QList\<GattDescriptorRemotePtr\>](#descriptors-prop)
- [\[read-only\] flags : QStringList](#flags-prop)
- [\[read-only\] handle : quint16](#handle-prop)
- [\[read-only\] notifyAcquired : bool](#notifyAcquired-prop)
- [\[read-only\] notifying : bool](#notifying-prop)
- [\[read-only\] service : const GattServiceRemotePtr](#service-prop)
- [\[read-only\] ubi : const QString](#ubi-prop)
- [\[read-only\] uuid : QString](#uuid-prop)
- [\[read-only\] value : QByteArray](#value-prop)
- [\[read-only\] writeAcquired : bool](#writeAcquired-prop)

## Public Functions

- [quint16 MTU() const](#MTU)
- [QList\<BluezQt::GattDescriptorRemotePtr\> descriptors() const](#descriptors)
- [QStringList flags() const](#flags)
- [quint16 handle() const](#handle)
- [bool isNotifyAcquired() const](#isNotifyAcquired)
- [bool isNotifying() const](#isNotifying)
- [bool isWriteAcquired() const](#isWriteAcquired)
- [BluezQt::GattServiceRemotePtr service() const](#service)
- [BluezQt::PendingCall \*setHandle(quint16 handle)](#setHandle)
- [BluezQt::GattCharacteristicRemotePtr toSharedPtr() const](#toSharedPtr)
- [QString ubi() const](#ubi)
- [QString uuid() const](#uuid)
- [QByteArray value() const](#value)

## Public Slots

- [BluezQt::PendingCall \*confirm()](#confirm)
- [BluezQt::PendingCall \*readValue(const QVariantMap &options)](#readValue)
- [BluezQt::PendingCall \*startNotify()](#startNotify)
- [BluezQt::PendingCall \*stopNotify()](#stopNotify)
- [BluezQt::PendingCall \*writeValue(const QByteArray &value, const QVariantMap &options)](#writeValue)

## Signals

- [void MTUChanged(quint16 MTU)](#MTUChanged)
- [void characteristicChanged(BluezQt::GattCharacteristicRemotePtr characteristic)](#characteristicChanged)
- [void descriptorsChanged(QList\<BluezQt::GattDescriptorRemotePtr\> descriptors)](#descriptorsChanged)
- [void flagsChanged(QStringList flags)](#flagsChanged)
- [void gattDescriptorAdded(BluezQt::GattDescriptorRemotePtr descriptor)](#gattDescriptorAdded)
- [void gattDescriptorChanged(BluezQt::GattDescriptorRemotePtr descriptor)](#gattDescriptorChanged)
- [void gattDescriptorRemoved(BluezQt::GattDescriptorRemotePtr descriptor)](#gattDescriptorRemoved)
- [void handleChanged(quint16 handle)](#handleChanged)
- [void notifyAcquiredChanged(bool notifyAcquired)](#notifyAcquiredChanged)
- [void notifyingChanged(bool notifying)](#notifyingChanged)
- [void uuidChanged(const QString &uuid)](#uuidChanged)
- [void valueChanged(const QByteArray value)](#valueChanged)
- [void writeAcquiredChanged(bool writeAcquired)](#writeAcquiredChanged)

## Detailed Description {#details}

This class represents a Bluetooth LE GATT characteristic for the clients.

## Property Documentation {#property-documentation}

### \[read-only\] MTU : quint16 {#MTU-prop}

**Access functions:**

- `quint16` **[MTU](bluezqt-gattcharacteristicremote.md#MTU)**() const

**Notifier signal:**

- `void` **[MTUChanged](bluezqt-gattcharacteristicremote.md#MTUChanged)**(`quint16` *MTU*)

### \[read-only\] descriptors : QList\<GattDescriptorRemotePtr\> {#descriptors-prop}

**Access functions:**

- `QList`\<`BluezQt::GattDescriptorRemotePtr`\> **[descriptors](bluezqt-gattcharacteristicremote.md#descriptors)**() const

**Notifier signal:**

- `void` **[descriptorsChanged](bluezqt-gattcharacteristicremote.md#descriptorsChanged)**(`QList`\<`BluezQt::GattDescriptorRemotePtr`\> *descriptors*)

### \[read-only\] flags : QStringList {#flags-prop}

**Access functions:**

- `QStringList` **[flags](bluezqt-gattcharacteristicremote.md#flags)**() const

**Notifier signal:**

- `void` **[flagsChanged](bluezqt-gattcharacteristicremote.md#flagsChanged)**(`QStringList` *flags*)

### \[read-only\] handle : quint16 {#handle-prop}

**Access functions:**

- `quint16` **[handle](bluezqt-gattcharacteristicremote.md#handle)**() const

**Notifier signal:**

- `void` **[handleChanged](bluezqt-gattcharacteristicremote.md#handleChanged)**(`quint16` *handle*)

### \[read-only\] notifyAcquired : bool {#notifyAcquired-prop}

**Access functions:**

- `bool` **[isNotifyAcquired](bluezqt-gattcharacteristicremote.md#isNotifyAcquired)**() const

**Notifier signal:**

- `void` **[notifyAcquiredChanged](bluezqt-gattcharacteristicremote.md#notifyAcquiredChanged)**(`bool` *notifyAcquired*)

### \[read-only\] notifying : bool {#notifying-prop}

**Access functions:**

- `bool` **[isNotifying](bluezqt-gattcharacteristicremote.md#isNotifying)**() const

**Notifier signal:**

- `void` **[notifyingChanged](bluezqt-gattcharacteristicremote.md#notifyingChanged)**(`bool` *notifying*)

### \[read-only\] service : const GattServiceRemotePtr {#service-prop}

**Access functions:**

- `BluezQt::GattServiceRemotePtr` **[service](bluezqt-gattcharacteristicremote.md#service)**() const

### \[read-only\] ubi : const QString {#ubi-prop}

**Access functions:**

- `QString` **[ubi](bluezqt-gattcharacteristicremote.md#ubi)**() const

### \[read-only\] uuid : QString {#uuid-prop}

**Access functions:**

- `QString` **[uuid](bluezqt-gattcharacteristicremote.md#uuid)**() const

**Notifier signal:**

- `void` **[uuidChanged](bluezqt-gattcharacteristicremote.md#uuidChanged)**(const `QString` &*uuid*)

### \[read-only\] value : QByteArray {#value-prop}

**Access functions:**

- `QByteArray` **[value](bluezqt-gattcharacteristicremote.md#value)**() const

**Notifier signal:**

- `void` **[valueChanged](bluezqt-gattcharacteristicremote.md#valueChanged)**(const `QByteArray` *value*)

### \[read-only\] writeAcquired : bool {#writeAcquired-prop}

**Access functions:**

- `bool` **[isWriteAcquired](bluezqt-gattcharacteristicremote.md#isWriteAcquired)**() const

**Notifier signal:**

- `void` **[writeAcquiredChanged](bluezqt-gattcharacteristicremote.md#writeAcquiredChanged)**(`bool` *writeAcquired*)

## Member Function Documentation {#member-function-documentation}

### quint16 GattCharacteristicRemote::MTU() const {#MTU}

Returns the characteristic's MTU.

> **Note:** Getter function for property [MTU](bluezqt-gattcharacteristicremote.md#MTU-prop).

### \[signal\] void GattCharacteristicRemote::MTUChanged(quint16 *MTU*) {#MTUChanged}

Indicates that the characteristic's `MTU` have changed.

> **Note:** Notifier signal for property [MTU](bluezqt-gattcharacteristicremote.md#MTU-prop).

### \[signal\] void GattCharacteristicRemote::characteristicChanged(BluezQt::GattCharacteristicRemotePtr *characteristic*) {#characteristicChanged}

Indicates that at least one of the `characteristic`'s properties has changed.

### \[slot\] BluezQt::PendingCall \*GattCharacteristicRemote::confirm() {#confirm}

Confirmation that value of the characteristic was received.

This method doesn't expect a reply so it is just a confirmation that value was received.

Possible errors:

- [PendingCall::NotReady](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::InProgress](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::AlreadyConnected](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### QList\<BluezQt::GattDescriptorRemotePtr\> GattCharacteristicRemote::descriptors() const {#descriptors}

Returns object paths representing the included services of this service.

> **Note:** Getter function for property [descriptors](bluezqt-gattcharacteristicremote.md#descriptors-prop).

### \[signal\] void GattCharacteristicRemote::descriptorsChanged(QList\<BluezQt::GattDescriptorRemotePtr\> *descriptors*) {#descriptorsChanged}

Indicates that the characteristic's `descriptors` list has changed.

> **Note:** Notifier signal for property [descriptors](bluezqt-gattcharacteristicremote.md#descriptors-prop).

### QStringList GattCharacteristicRemote::flags() const {#flags}

Returns the characteristic's flags.

> **Note:** Getter function for property [flags](bluezqt-gattcharacteristicremote.md#flags-prop).

### \[signal\] void GattCharacteristicRemote::flagsChanged(QStringList *flags*) {#flagsChanged}

Indicates that the characteristic's `flags` has changed.

> **Note:** Notifier signal for property [flags](bluezqt-gattcharacteristicremote.md#flags-prop).

### \[signal\] void GattCharacteristicRemote::gattDescriptorAdded(BluezQt::GattDescriptorRemotePtr *descriptor*) {#gattDescriptorAdded}

Indicates that a new `descriptor` was added (eg. found by connection).

### \[signal\] void GattCharacteristicRemote::gattDescriptorChanged(BluezQt::GattDescriptorRemotePtr *descriptor*) {#gattDescriptorChanged}

Indicates that at least one of the `descriptor` properties has changed.

### \[signal\] void GattCharacteristicRemote::gattDescriptorRemoved(BluezQt::GattDescriptorRemotePtr *descriptor*) {#gattDescriptorRemoved}

Indicates that a `descriptor` was removed.

### quint16 GattCharacteristicRemote::handle() const {#handle}

Returns the characteristic's handle.

> **Note:** Getter function for property [handle](bluezqt-gattcharacteristicremote.md#handle-prop).

*See also* [setHandle](bluezqt-gattcharacteristicremote.md#setHandle)()

### \[signal\] void GattCharacteristicRemote::handleChanged(quint16 *handle*) {#handleChanged}

Indicates that the characteristic's handle has changed.

> **Note:** Notifier signal for property [handle](bluezqt-gattcharacteristicremote.md#handle-prop).

### bool GattCharacteristicRemote::isNotifyAcquired() const {#isNotifyAcquired}

Returns whether notifyAcquired() is `true` for the characteristic.

> **Note:** Getter function for property [notifyAcquired](bluezqt-gattcharacteristicremote.md#notifyAcquired-prop).

### bool GattCharacteristicRemote::isNotifying() const {#isNotifying}

Returns whether the characteristic is notifying.

> **Note:** Getter function for property [notifying](bluezqt-gattcharacteristicremote.md#notifying-prop).

### bool GattCharacteristicRemote::isWriteAcquired() const {#isWriteAcquired}

Returns whether writeAcquired() is `true` for the characteristic.

> **Note:** Getter function for property [writeAcquired](bluezqt-gattcharacteristicremote.md#writeAcquired-prop).

### \[signal\] void GattCharacteristicRemote::notifyAcquiredChanged(bool *notifyAcquired*) {#notifyAcquiredChanged}

Indicates that the characteristic's `notifyAcquired` state has changed.

> **Note:** Notifier signal for property [notifyAcquired](bluezqt-gattcharacteristicremote.md#notifyAcquired-prop).

### \[signal\] void GattCharacteristicRemote::notifyingChanged(bool *notifying*) {#notifyingChanged}

Indicates that the characteristic's `notifying` state has changed.

> **Note:** Notifier signal for property [notifying](bluezqt-gattcharacteristicremote.md#notifying-prop).

### \[slot\] BluezQt::PendingCall \*GattCharacteristicRemote::readValue(const QVariantMap &*options*) {#readValue}

Read the value of the GATT characteristic.

Issues a request to read the value of the characteristic and returns the value if the operation was successful.

Possible errors:

- [PendingCall::NotReady](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::InProgress](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::AlreadyConnected](bluezqt-pendingcall.md#Error-enum)

Returns [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) pending call.

### BluezQt::GattServiceRemotePtr GattCharacteristicRemote::service() const {#service}

Returns a service that owns that characteristic.

> **Note:** Getter function for property [service](bluezqt-gattcharacteristicremote.md#service-prop).

### BluezQt::PendingCall \*GattCharacteristicRemote::setHandle(quint16 *handle*) {#setHandle}

Sets the characteristic's `handle`.

Returns void pending call.

*See also* [handle](bluezqt-gattcharacteristicremote.md#handle)()

### \[slot\] BluezQt::PendingCall \*GattCharacteristicRemote::startNotify() {#startNotify}

Start notifying the value of the GATT characteristic.

Starts a notification session from this characteristic if it supports value notifications or indications.

Possible errors:

- [PendingCall::NotReady](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::InProgress](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::AlreadyConnected](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### \[slot\] BluezQt::PendingCall \*GattCharacteristicRemote::stopNotify() {#stopNotify}

Stop notifying the value of the GATT characteristic.

This method will cancel any previous StartNotify transaction. Note that notifications from a characteristic are shared between sessions thus calling StopNotify will release a single session.

Possible errors:

- [PendingCall::NotReady](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::InProgress](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::AlreadyConnected](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### BluezQt::GattCharacteristicRemotePtr GattCharacteristicRemote::toSharedPtr() const {#toSharedPtr}

Returns a shared pointer from this.

### QString GattCharacteristicRemote::ubi() const {#ubi}

Returns the UBI of the GATT characteristic.

Example UBI: "/org/bluez/hci0/dev\_40\_79\_6A\_0C\_39\_75"

> **Note:** Getter function for property [ubi](bluezqt-gattcharacteristicremote.md#ubi-prop).

### QString GattCharacteristicRemote::uuid() const {#uuid}

Returns the UUID of the characteristic.

> **Note:** Getter function for property [uuid](bluezqt-gattcharacteristicremote.md#uuid-prop).

### \[signal\] void GattCharacteristicRemote::uuidChanged(const QString &*uuid*) {#uuidChanged}

Indicates that the characteristic's `uuid` has changed.

> **Note:** Notifier signal for property [uuid](bluezqt-gattcharacteristicremote.md#uuid-prop).

### QByteArray GattCharacteristicRemote::value() const {#value}

Returns the value of the characteristic.

> **Note:** Getter function for property [value](bluezqt-gattcharacteristicremote.md#value-prop).

### \[signal\] void GattCharacteristicRemote::valueChanged(const QByteArray *value*) {#valueChanged}

Indicates that the characteristic's `value` has changed.

> **Note:** Notifier signal for property [value](bluezqt-gattcharacteristicremote.md#value-prop).

### \[signal\] void GattCharacteristicRemote::writeAcquiredChanged(bool *writeAcquired*) {#writeAcquiredChanged}

Indicates that the characteristic's `writeAcquired` state has changed.

> **Note:** Notifier signal for property [writeAcquired](bluezqt-gattcharacteristicremote.md#writeAcquired-prop).

### \[slot\] BluezQt::PendingCall \*GattCharacteristicRemote::writeValue(const QByteArray &*value*, const QVariantMap &*options*) {#writeValue}

Write the value of the GATT characteristic.

Issues a request to write the value of the characteristic.

Possible errors:

- [PendingCall::NotReady](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::InProgress](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::AlreadyConnected](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.
