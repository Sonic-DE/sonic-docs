---
title: "BluezQt::GattApplication Class"
description: "Bluetooth GattApplication."
---

# BluezQt::GattApplication Class

Bluetooth [GattApplication](bluezqt-gattapplication.md). [More...](#details)

- **Header:** `#include <BluezQt/GattApplication>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-gattapplication-members.md)

## Public Functions

- [GattApplication(QObject \*parent = nullptr)](#GattApplication)
- [GattApplication(const QString &objectPathPrefix, QObject \*parent = nullptr)](#GattApplication-1)

## Detailed Description {#details}

This class represents a Bluetooth [GattApplication](bluezqt-gattapplication.md), which is the root node of a GATT object hierarchy. Its child nodes can be GattServices, GattCharacteristics and GattDescriptors that belong to that [GattApplication](bluezqt-gattapplication.md). The object path prefix for GattApplications is freely definable and its children's paths follow the application path hierarchy automatically, while all instances are enumerated automatically as well.

Object path: \[variable prefix\]/appXX/serviceYY/charZZ

## Member Function Documentation {#member-function-documentation}

### \[explicit\] GattApplication::GattApplication(QObject \**parent* = nullptr) {#GattApplication}

Creates a new [GattApplication](bluezqt-gattapplication.md) object with default object path prefix as a child of `parent`.

Object path: /org/kde/bluezqt/appXX/serviceYY/charZZ

### \[explicit\] GattApplication::GattApplication(const QString &*objectPathPrefix*, QObject \**parent* = nullptr) {#GattApplication-1}

Creates a new [GattApplication](bluezqt-gattapplication.md) object with custom object path prefix `objectPathPrefix` as a child of `parent`.

Object path: \[objectPathPrefix\]/appXX/serviceYY/charZZ
