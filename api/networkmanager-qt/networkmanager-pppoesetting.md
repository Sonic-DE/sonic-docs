---
title: "NetworkManager::PppoeSetting Class"
description: "Represents pppoe setting."
---

# NetworkManager::PppoeSetting Class

Represents pppoe setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/PppoeSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-pppoesetting-members.md)

## Public Types

- [PppoeSetting::List](#List-typedef)
- [PppoeSetting::Ptr](#Ptr-typedef)

## Public Functions

- [PppoeSetting()](#PppoeSetting)
- [PppoeSetting(const NetworkManager::PppoeSetting::Ptr &other)](#PppoeSetting-1)
- [QString parent() const](#parent)
- [QString password() const](#password)
- [Setting::SecretFlags passwordFlags() const](#passwordFlags)
- [QString service() const](#service)
- [void setParent(const QString &parent)](#setParent)
- [void setPassword(const QString &password)](#setPassword)
- [void setPasswordFlags(Setting::SecretFlags flags)](#setPasswordFlags)
- [void setService(const QString &service)](#setService)
- [void setUsername(const QString &username)](#setUsername)
- [QString username() const](#username)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### PppoeSetting::List {#List-typedef}

### PppoeSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### PppoeSetting::PppoeSetting() {#PppoeSetting}

### \[explicit\] PppoeSetting::PppoeSetting(const NetworkManager::PppoeSetting::Ptr &*other*) {#PppoeSetting-1}

### QString PppoeSetting::parent() const {#parent}

*See also* [setParent](networkmanager-pppoesetting.md#setParent)()

### QString PppoeSetting::password() const {#password}

*See also* [setPassword](networkmanager-pppoesetting.md#setPassword)()

### Setting::SecretFlags PppoeSetting::passwordFlags() const {#passwordFlags}

*See also* [setPasswordFlags](networkmanager-pppoesetting.md#setPasswordFlags)()

### QString PppoeSetting::service() const {#service}

*See also* [setService](networkmanager-pppoesetting.md#setService)()

### void PppoeSetting::setParent(const QString &*parent*) {#setParent}

*See also* [parent](networkmanager-pppoesetting.md#parent)()

### void PppoeSetting::setPassword(const QString &*password*) {#setPassword}

*See also* [password](networkmanager-pppoesetting.md#password)()

### void PppoeSetting::setPasswordFlags(Setting::SecretFlags *flags*) {#setPasswordFlags}

*See also* [passwordFlags](networkmanager-pppoesetting.md#passwordFlags)()

### void PppoeSetting::setService(const QString &*service*) {#setService}

*See also* [service](networkmanager-pppoesetting.md#service)()

### void PppoeSetting::setUsername(const QString &*username*) {#setUsername}

*See also* [username](networkmanager-pppoesetting.md#username)()

### QString PppoeSetting::username() const {#username}

*See also* [setUsername](networkmanager-pppoesetting.md#setUsername)()
