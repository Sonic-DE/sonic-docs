---
title: "BluezQt::GattServiceRemote Class"
description: "Bluetooth LE GATT service."
---

# BluezQt::GattServiceRemote Class

Bluetooth LE GATT service. [More...](#details)

- **Header:** `#include <BluezQt/GattServiceRemote>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-gattserviceremote-members.md)

## Properties

- [\[read-only\] characteristics : QList\<GattCharacteristicRemotePtr\>](#characteristics-prop)
- [\[read-only\] device : const DevicePtr](#device-prop)
- [handle : quint16](#handle-prop)
- [\[read-only\] includes : QList\<QDBusObjectPath\>](#includes-prop)
- [\[read-only\] primary : bool](#primary-prop)
- [\[read-only\] uuid : QString](#uuid-prop)

## Public Functions

- [QList\<BluezQt::GattCharacteristicRemotePtr\> characteristics() const](#characteristics)
- [BluezQt::DevicePtr device() const](#device)
- [quint16 handle() const](#handle)
- [QList\<QDBusObjectPath\> includes() const](#includes)
- [bool isPrimary() const](#isPrimary)
- [BluezQt::PendingCall \*setHandle(quint16 handle)](#setHandle)
- [BluezQt::GattServiceRemotePtr toSharedPtr() const](#toSharedPtr)
- [QString ubi() const](#ubi)
- [QString uuid() const](#uuid)

## Signals

- [void characteristicsChanged(QList\<BluezQt::GattCharacteristicRemotePtr\> characteristics)](#characteristicsChanged)
- [void gattCharacteristicAdded(BluezQt::GattCharacteristicRemotePtr characteristic)](#gattCharacteristicAdded)
- [void gattCharacteristicChanged(BluezQt::GattCharacteristicRemotePtr characteristic)](#gattCharacteristicChanged)
- [void gattCharacteristicRemoved(BluezQt::GattCharacteristicRemotePtr characteristic)](#gattCharacteristicRemoved)
- [void handleChanged(quint16 handle)](#handleChanged)
- [void includesChanged(const QList\<QDBusObjectPath\> &includes)](#includesChanged)
- [void primaryChanged(bool primary)](#primaryChanged)
- [void serviceChanged(BluezQt::GattServiceRemotePtr service)](#serviceChanged)
- [void uuidChanged(const QString &uuid)](#uuidChanged)

## Detailed Description {#details}

This class represents a Bluetooth LE GATT service.

## Property Documentation {#property-documentation}

### \[read-only\] characteristics : QList\<GattCharacteristicRemotePtr\> {#characteristics-prop}

**Access functions:**

- `QList`\<`BluezQt::GattCharacteristicRemotePtr`\> **[characteristics](bluezqt-gattserviceremote.md#characteristics)**() const

**Notifier signal:**

- `void` **[characteristicsChanged](bluezqt-gattserviceremote.md#characteristicsChanged)**(`QList`\<`BluezQt::GattCharacteristicRemotePtr`\> *characteristics*)

### \[read-only\] device : const DevicePtr {#device-prop}

**Access functions:**

- `BluezQt::DevicePtr` **[device](bluezqt-gattserviceremote.md#device)**() const

### handle : quint16 {#handle-prop}

**Access functions:**

- `quint16` **[handle](bluezqt-gattserviceremote.md#handle)**() const
- `BluezQt::PendingCall` \***[setHandle](bluezqt-gattserviceremote.md#setHandle)**(`quint16` *handle*)

**Notifier signal:**

- `void` **[handleChanged](bluezqt-gattserviceremote.md#handleChanged)**(`quint16` *handle*)

### \[read-only\] includes : QList\<QDBusObjectPath\> {#includes-prop}

**Access functions:**

- `QList`\<`QDBusObjectPath`\> **[includes](bluezqt-gattserviceremote.md#includes)**() const

**Notifier signal:**

- `void` **[includesChanged](bluezqt-gattserviceremote.md#includesChanged)**(const `QList`\<`QDBusObjectPath`\> &*includes*)

### \[read-only\] primary : bool {#primary-prop}

**Access functions:**

- `bool` **[isPrimary](bluezqt-gattserviceremote.md#isPrimary)**() const

**Notifier signal:**

- `void` **[primaryChanged](bluezqt-gattserviceremote.md#primaryChanged)**(`bool` *primary*)

### \[read-only\] uuid : QString {#uuid-prop}

**Access functions:**

- `QString` **[uuid](bluezqt-gattserviceremote.md#uuid)**() const

**Notifier signal:**

- `void` **[uuidChanged](bluezqt-gattserviceremote.md#uuidChanged)**(const `QString` &*uuid*)

## Member Function Documentation {#member-function-documentation}

### QList\<BluezQt::GattCharacteristicRemotePtr\> GattServiceRemote::characteristics() const {#characteristics}

Returns object paths representing the included services of this service.

> **Note:** Getter function for property [characteristics](bluezqt-gattserviceremote.md#characteristics-prop).

### \[signal\] void GattServiceRemote::characteristicsChanged(QList\<BluezQt::GattCharacteristicRemotePtr\> *characteristics*) {#characteristicsChanged}

Indicates that the service `characteristics` list has changed.

> **Note:** Notifier signal for property [characteristics](bluezqt-gattserviceremote.md#characteristics-prop).

### BluezQt::DevicePtr GattServiceRemote::device() const {#device}

Returns the device that has this service.

> **Note:** Getter function for property [device](bluezqt-gattserviceremote.md#device-prop).

### \[signal\] void GattServiceRemote::gattCharacteristicAdded(BluezQt::GattCharacteristicRemotePtr *characteristic*) {#gattCharacteristicAdded}

Indicates that a new `characteristic` was added (eg. found by connection).

### \[signal\] void GattServiceRemote::gattCharacteristicChanged(BluezQt::GattCharacteristicRemotePtr *characteristic*) {#gattCharacteristicChanged}

Indicates that at least one of the `characteristic`'s properties has changed.

### \[signal\] void GattServiceRemote::gattCharacteristicRemoved(BluezQt::GattCharacteristicRemotePtr *characteristic*) {#gattCharacteristicRemoved}

Indicates that a `characteristic` was removed.

### quint16 GattServiceRemote::handle() const {#handle}

Returns service handle.

Returns qint16 service handle

> **Note:** Getter function for property [handle](bluezqt-gattserviceremote.md#handle-prop).

*See also* [setHandle](bluezqt-gattserviceremote.md#setHandle)()

### \[signal\] void GattServiceRemote::handleChanged(quint16 *handle*) {#handleChanged}

Indicates that the services's `handle` has changed.

> **Note:** Notifier signal for property [handle](bluezqt-gattserviceremote.md#handle-prop).

### QList\<QDBusObjectPath\> GattServiceRemote::includes() const {#includes}

Returns object paths representing the included services of this service.

> **Note:** Getter function for property [includes](bluezqt-gattserviceremote.md#includes-prop).

### \[signal\] void GattServiceRemote::includesChanged(const QList\<QDBusObjectPath\> &*includes*) {#includesChanged}

Indicates that the object paths representing the included services `includes` have changed.

> **Note:** Notifier signal for property [includes](bluezqt-gattserviceremote.md#includes-prop).

### bool GattServiceRemote::isPrimary() const {#isPrimary}

Returns whether the service is primary.

> **Note:** Getter function for property [primary](bluezqt-gattserviceremote.md#primary-prop).

### \[signal\] void GattServiceRemote::primaryChanged(bool *primary*) {#primaryChanged}

Indicates that the services's `primary` state has changed.

> **Note:** Notifier signal for property [primary](bluezqt-gattserviceremote.md#primary-prop).

### \[signal\] void GattServiceRemote::serviceChanged(BluezQt::GattServiceRemotePtr *service*) {#serviceChanged}

Indicates that at least one of the `service`'s properties has changed.

### BluezQt::PendingCall \*GattServiceRemote::setHandle(quint16 *handle*) {#setHandle}

Sets the service `handle`.

Returns void pending call.

> **Note:** Setter function for property [handle](bluezqt-gattserviceremote.md#handle-prop).

*See also* [handle](bluezqt-gattserviceremote.md#handle)()

### BluezQt::GattServiceRemotePtr GattServiceRemote::toSharedPtr() const {#toSharedPtr}

Returns a shared pointer from this.

### QString GattServiceRemote::ubi() const {#ubi}

Returns the UBI of the gatt service.

Example UBI: "/org/bluez/hci0/dev\_40\_79\_6A\_0C\_39\_75/service01"

### QString GattServiceRemote::uuid() const {#uuid}

Returns the UUID of the service.

> **Note:** Getter function for property [uuid](bluezqt-gattserviceremote.md#uuid-prop).

### \[signal\] void GattServiceRemote::uuidChanged(const QString &*uuid*) {#uuidChanged}

Indicates that the service's `uuid` has changed.

> **Note:** Notifier signal for property [uuid](bluezqt-gattserviceremote.md#uuid-prop).
