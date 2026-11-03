---
title: "NetworkManager::Dhcp6Config Class"
description: "This class represents dhcp4 configuration."
---

# NetworkManager::Dhcp6Config Class

This class represents dhcp4 configuration. [More...](#details)

- **Header:** `#include <NetworkManagerQt/Dhcp6Config>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](networkmanager-dhcp6config-members.md)

## Public Types

- [Dhcp6Config::List](#List-typedef)
- [Dhcp6Config::Ptr](#Ptr-typedef)

## Public Functions

- [Dhcp6Config(const QString &path, QObject \*owner = nullptr)](#Dhcp6Config)
- [QString optionValue(const QString &key) const](#optionValue)
- [QVariantMap options() const](#options)
- [QString path() const](#path)

## Signals

- [void optionsChanged(const QVariantMap &)](#optionsChanged)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### Dhcp6Config::List {#List-typedef}

### Dhcp6Config::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Dhcp6Config::Dhcp6Config(const QString &*path*, QObject \**owner* = nullptr) {#Dhcp6Config}

### QString Dhcp6Config::optionValue(const QString &*key*) const {#optionValue}

### QVariantMap Dhcp6Config::options() const {#options}

### \[signal\] void Dhcp6Config::optionsChanged(*const QVariantMap &*) {#optionsChanged}

### QString Dhcp6Config::path() const {#path}
