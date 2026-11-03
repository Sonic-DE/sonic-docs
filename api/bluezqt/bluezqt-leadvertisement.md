---
title: "BluezQt::LEAdvertisement Class"
description: "Bluetooth LE advertisement."
---

# BluezQt::LEAdvertisement Class

Bluetooth LE advertisement. [More...](#details)

- **Header:** `#include <BluezQt/LEAdvertisement>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-leadvertisement-members.md)

## Public Functions

- [LEAdvertisement(const QStringList &serviceUuids, QObject \*parent = nullptr)](#LEAdvertisement)
- [QHash\<quint16, QByteArray\> manufacturerData() const](#manufacturerData) (since 6.1)
- [void release()](#release)
- [QHash\<QString, QByteArray\> serviceData() const](#serviceData)
- [QStringList serviceUuids() const](#serviceUuids)
- [void setManufacturerData(const QHash\<quint16, QByteArray\> &data)](#setManufacturerData) (since 6.1)
- [void setServiceData(const QHash\<QString, QByteArray\> &data)](#setServiceData)

## Protected Functions

- [QDBusObjectPath objectPath() const](#objectPath)

## Detailed Description {#details}

This class represents a Bluetooth LE advertisement.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] LEAdvertisement::LEAdvertisement(const QStringList &*serviceUuids*, QObject \**parent* = nullptr) {#LEAdvertisement}

Creates a new [LEAdvertisement](bluezqt-leadvertisement.md) object with the given `serviceUuids` as a child of `parent`.

### \[since 6.1\] QHash\<quint16, QByteArray\> LEAdvertisement::manufacturerData() const {#manufacturerData}

Returns the manufacturer IDs and associated data included in the advertisement.

Keys are the manufacturer ID.

This function was introduced in Qt 6.1.

*See also* [setManufacturerData](bluezqt-leadvertisement.md#setManufacturerData)()

### \[virtual protected\] QDBusObjectPath LEAdvertisement::objectPath() const {#objectPath}

Returns the D-Bus object path of the advertisement.

The path where the advertisement will be registered.

> **Note:** You must provide valid object path!

### \[virtual\] void LEAdvertisement::release() {#release}

Indicates that the [LEAdvertisement](bluezqt-leadvertisement.md) was unregistered.

This method gets called when the service daemon removes the Advertisement.

A client can use it to do cleanup tasks.

There is no need to call UnregisterAdvertisement because when this method gets called it has already been unregistered.

### QHash\<QString, QByteArray\> LEAdvertisement::serviceData() const {#serviceData}

Returns the service data included in the advertisement.

*See also* [setServiceData](bluezqt-leadvertisement.md#setServiceData)()

### \[virtual\] QStringList LEAdvertisement::serviceUuids() const {#serviceUuids}

List of UUIDs to include in the "Service UUID" field of the Advertising Data.

### \[since 6.1\] void LEAdvertisement::setManufacturerData(const QHash\<quint16, QByteArray\> &*data*) {#setManufacturerData}

Sets the manufacturer IDs and associated `data` to be included in the advertisement.

Keys are the manufacturer ID.

This function was introduced in Qt 6.1.

*See also* [manufacturerData](bluezqt-leadvertisement.md#manufacturerData)()

### void LEAdvertisement::setServiceData(const QHash\<QString, QByteArray\> &*data*) {#setServiceData}

Sets the service data to include in the advertisement.

Keys are the UUIDs of the associated data.

*See also* [serviceData](bluezqt-leadvertisement.md#serviceData)()
