---
title: "NetworkManager::Dhcp4Config Class"
description: "This class represents dhcp4 configuration."
---

# NetworkManager::Dhcp4Config Class

This class represents dhcp4 configuration. [More...](#details)

- **Header:** `#include <NetworkManagerQt/Dhcp4Config>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](networkmanager-dhcp4config-members.md)

## Public Types

- [Dhcp4Config::List](#List-typedef)
- [Dhcp4Config::Ptr](#Ptr-typedef)

## Public Functions

- [Dhcp4Config(const QString &path, QObject \*owner = nullptr)](#Dhcp4Config)
- [QString optionValue(const QString &key) const](#optionValue)
- [QVariantMap options() const](#options)
- [QString path() const](#path)

## Signals

- [void optionsChanged(const QVariantMap &)](#optionsChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### Dhcp4Config::List {#List-typedef}

### Dhcp4Config::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Dhcp4Config::Dhcp4Config(const QString &*path*, QObject \**owner* = nullptr) {#Dhcp4Config}

### QString Dhcp4Config::optionValue(const QString &*key*) const {#optionValue}

### QVariantMap Dhcp4Config::options() const {#options}

### \[signal\] void Dhcp4Config::optionsChanged(*const QVariantMap &*) {#optionsChanged}

### QString Dhcp4Config::path() const {#path}
