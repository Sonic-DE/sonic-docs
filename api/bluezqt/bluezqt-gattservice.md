---
title: "BluezQt::GattService Class"
description: "Bluetooth GattService."
---

# BluezQt::GattService Class

Bluetooth [GattService](bluezqt-gattservice.md). [More...](#details)

- **Header:** `#include <BluezQt/GattService>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-gattservice-members.md)

## Public Functions

- [GattService(const QString &uuid, bool isPrimary, BluezQt::GattApplication \*parent)](#GattService)
- [bool isPrimary() const](#isPrimary)
- [QString uuid() const](#uuid)

## Protected Functions

- [QDBusObjectPath objectPath() const](#objectPath)

## Detailed Description {#details}

This class represents a Bluetooth [GattService](bluezqt-gattservice.md).

## Member Function Documentation {#member-function-documentation}

### \[explicit\] GattService::GattService(const QString &*uuid*, bool *isPrimary*, BluezQt::GattApplication \**parent*) {#GattService}

Creates a new [GattService](bluezqt-gattservice.md) object as a child of a `parent` application.

### bool GattService::isPrimary() const {#isPrimary}

Indicates whether or not this GATT service is a primary service.

Returns `true` if this GATT service is primary, `false` if secondary.

### \[virtual protected\] QDBusObjectPath GattService::objectPath() const {#objectPath}

Returns the D-Bus object path registered for the [GattService](bluezqt-gattservice.md).

> **Note:** You must provide valid object path!

### QString GattService::uuid() const {#uuid}

Returns the 128-bit service UUID.
