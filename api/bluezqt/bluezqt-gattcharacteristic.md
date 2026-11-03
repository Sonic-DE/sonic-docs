---
title: "BluezQt::GattCharacteristic Class"
description: "Qt wrapper for BlueZ 5 DBus API."
---

# BluezQt::GattCharacteristic Class

Qt wrapper for BlueZ 5 DBus API. [More...](#details)

- **Header:** `#include <BluezQt/GattCharacteristic>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-gattcharacteristic-members.md)

## Public Types

- [\[alias\] GattCharacteristic::ReadCallback](#ReadCallback-typedef)

## Public Functions

- [GattCharacteristic(const QString &uuid, BluezQt::GattService \*service)](#GattCharacteristic)
- [GattCharacteristic(const QString &uuid, const QStringList &flags, BluezQt::GattService \*service)](#GattCharacteristic-1) (since 6.0)
- [QStringList flags() const](#flags) (since 6.0)
- [bool isNotifying() const](#isNotifying) (since 6.0)
- [QByteArray readValue()](#readValue)
- [const BluezQt::GattService \*service() const](#service)
- [void setReadCallback(BluezQt::GattCharacteristic::ReadCallback callback)](#setReadCallback)
- [void startNotify()](#startNotify) (since 6.0)
- [void stopNotify()](#stopNotify) (since 6.0)
- [QString uuid() const](#uuid)
- [void writeValue(const QByteArray &value)](#writeValue)

## Signals

- [void valueWritten(const QByteArray &value)](#valueWritten)

## Protected Functions

- [QDBusObjectPath objectPath() const](#objectPath)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### \[alias\] GattCharacteristic::ReadCallback {#ReadCallback-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] GattCharacteristic::GattCharacteristic(const QString &*uuid*, BluezQt::GattService \**service*) {#GattCharacteristic}

Creates a new [GattCharacteristic](bluezqt-gattcharacteristic.md) object with the given `uuid` and a parent `service`.

This constructor creates a characteristic with the Read and Write flags set.

### \[since 6.0\] GattCharacteristic::GattCharacteristic(const QString &*uuid*, const QStringList &*flags*, BluezQt::GattService \**service*) {#GattCharacteristic-1}

Creates a new [GattCharacteristic](bluezqt-gattcharacteristic.md) object with the given `uuid` and a parent `service`.

The `flags` can be used to indicate the characteristic usage.

This function was introduced in Qt 6.0.

### \[since 6.0\] QStringList GattCharacteristic::flags() const {#flags}

Returns flags associated with this characteristic.

This function was introduced in Qt 6.0.

### \[since 6.0\] bool GattCharacteristic::isNotifying() const {#isNotifying}

Indicates if this characteristic currently has notifications enabled.

This function was introduced in Qt 6.0.

### \[virtual protected\] QDBusObjectPath GattCharacteristic::objectPath() const {#objectPath}

Returns the D-Bus object path of the [GattCharacteristic](bluezqt-gattcharacteristic.md).

The path where the [GattCharacteristic](bluezqt-gattcharacteristic.md) will be registered.

> **Note:** You must provide valid object path!

### QByteArray GattCharacteristic::readValue() {#readValue}

Reads the value of the characteristic.

### const BluezQt::GattService \*GattCharacteristic::service() const {#service}

The GATT service the characteristic belongs to.

### void GattCharacteristic::setReadCallback(BluezQt::GattCharacteristic::ReadCallback *callback*) {#setReadCallback}

Provide a read `callback` to operate in *pull* mode.

### \[since 6.0\] void GattCharacteristic::startNotify() {#startNotify}

Enables notifications for this characteristic, if supported. Does nothing otherwise.

This function was introduced in Qt 6.0.

### \[since 6.0\] void GattCharacteristic::stopNotify() {#stopNotify}

Disables notifications for this characteristic.

This function was introduced in Qt 6.0.

### QString GattCharacteristic::uuid() const {#uuid}

Returns the 128-bit GATT characteristic UUID.

### \[signal\] void GattCharacteristic::valueWritten(const QByteArray &*value*) {#valueWritten}

Indicates that a `value` was written.

### void GattCharacteristic::writeValue(const QByteArray &*value*) {#writeValue}

Writes the `value` of the characteristic.
