---
title: "BluezQt::GattDescriptor Class"
description: "Bluetooth GATT Descriptor. This class was introduced in Qt 6.0."
---

# BluezQt::GattDescriptor Class

Bluetooth GATT Descriptor. This class was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <BluezQt/GattDescriptor>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-gattdescriptor-members.md)

## Public Functions

- [GattDescriptor(const QString &uuid, BluezQt::GattCharacteristic \*parent)](#GattDescriptor)
- [GattDescriptor(const QString &uuid, const QStringList &flags, BluezQt::GattCharacteristic \*parent)](#GattDescriptor-1)
- [GattDescriptor(const QString &uuid, const QStringList &flags, const QByteArray &initialValue, BluezQt::GattCharacteristic \*parent)](#GattDescriptor-2)
- [QDBusObjectPath characteristic() const](#characteristic)
- [QStringList flags() const](#flags)
- [QByteArray readValue()](#readValue)
- [QString uuid() const](#uuid)
- [void writeValue(const QByteArray &value)](#writeValue)

## Static Public Members

- [BluezQt::GattDescriptor \*createUserDescription(const QString &description, BluezQt::GattCharacteristic \*characteristic)](#createUserDescription)

## Protected Functions

- [QDBusObjectPath objectPath() const](#objectPath)

## Detailed Description {#details}

GATT Descriptors contain additional information and attributes of a GATT characteristic.

## Member Function Documentation {#member-function-documentation}

### GattDescriptor::GattDescriptor(const QString &*uuid*, BluezQt::GattCharacteristic \**parent*) {#GattDescriptor}

Creates a [GattDescriptor](bluezqt-gattdescriptor.md) with the given `uuid` as a child of a `parent` characteristic.

### GattDescriptor::GattDescriptor(const QString &*uuid*, const QStringList &*flags*, BluezQt::GattCharacteristic \**parent*) {#GattDescriptor-1}

Creates a [GattDescriptor](bluezqt-gattdescriptor.md) with the given `uuid` and `flags` as a child of a `parent` characteristic.

### GattDescriptor::GattDescriptor(const QString &*uuid*, const QStringList &*flags*, const QByteArray &*initialValue*, BluezQt::GattCharacteristic \**parent*) {#GattDescriptor-2}

Creates a [GattDescriptor](bluezqt-gattdescriptor.md) with the given `uuid`, `flags` and `initialValue` as a child of a `parent` characteristic.

### QDBusObjectPath GattDescriptor::characteristic() const {#characteristic}

Return the D-Bus object path of the parent characteristic.

### \[static\] BluezQt::GattDescriptor \*GattDescriptor::createUserDescription(const QString &*description*, BluezQt::GattCharacteristic \**characteristic*) {#createUserDescription}

Convenience method to create a User Description `description` for the given `charactersitic`.

Returns A pointer to the created descriptor.

### QStringList GattDescriptor::flags() const {#flags}

Return the flags of the descriptor.

### \[virtual protected\] QDBusObjectPath GattDescriptor::objectPath() const {#objectPath}

### QByteArray GattDescriptor::readValue() {#readValue}

Reads the current value of the descriptor.

### QString GattDescriptor::uuid() const {#uuid}

Returns the UUID of the descriptor.

### void GattDescriptor::writeValue(const QByteArray &*value*) {#writeValue}

Writes the new `value` of the descriptor.
