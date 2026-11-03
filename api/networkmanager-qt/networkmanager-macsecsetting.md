---
title: "NetworkManager::MacsecSetting Class"
description: "Represents Macsec setting."
---

# NetworkManager::MacsecSetting Class

Represents Macsec setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/MacsecSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-macsecsetting-members.md)

## Public Types

- [MacsecSetting::List](#List-typedef)
- [enum MacsecSetting::Mode](#Mode-enum)
- [MacsecSetting::Ptr](#Ptr-typedef)
- [enum MacsecSetting::Validation](#Validation-enum)

## Public Functions

- [MacsecSetting()](#MacsecSetting)
- [MacsecSetting(const NetworkManager::MacsecSetting::Ptr &other)](#MacsecSetting-1)
- [bool encrypt() const](#encrypt)
- [QString mkaCak() const](#mkaCak)
- [Setting::SecretFlags mkaCakFlags() const](#mkaCakFlags)
- [QString mkaCkn() const](#mkaCkn)
- [NetworkManager::MacsecSetting::Mode mode() const](#mode)
- [QString parent() const](#parent)
- [qint32 port() const](#port)
- [bool sendSci() const](#sendSci)
- [void setEncrypt(bool encrypt)](#setEncrypt)
- [void setMkaCak(const QString &mkaCak)](#setMkaCak)
- [void setMkaCakFlags(Setting::SecretFlags flags)](#setMkaCakFlags)
- [void setMkaCkn(const QString &mkaCkn)](#setMkaCkn)
- [void setMode(NetworkManager::MacsecSetting::Mode mode)](#setMode)
- [void setParent(const QString &parent)](#setParent)
- [void setPort(qint32 port)](#setPort)
- [void setSendSci(bool sendSci)](#setSendSci)
- [void setValidation(NetworkManager::MacsecSetting::Validation validation)](#setValidation)
- [NetworkManager::MacsecSetting::Validation validation() const](#validation)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### MacsecSetting::List {#List-typedef}

### enum MacsecSetting::Mode {#Mode-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::MacsecSetting::Psk` | `0` |
| `NetworkManager::MacsecSetting::Eap` | `1` |

### MacsecSetting::Ptr {#Ptr-typedef}

### enum MacsecSetting::Validation {#Validation-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::MacsecSetting::Disable` | `0` |
| `NetworkManager::MacsecSetting::Check` | `1` |
| `NetworkManager::MacsecSetting::Strict` | `2` |

## Member Function Documentation {#member-function-documentation}

### MacsecSetting::MacsecSetting() {#MacsecSetting}

### \[explicit\] MacsecSetting::MacsecSetting(const NetworkManager::MacsecSetting::Ptr &*other*) {#MacsecSetting-1}

### bool MacsecSetting::encrypt() const {#encrypt}

*See also* [setEncrypt](networkmanager-macsecsetting.md#setEncrypt)()

### QString MacsecSetting::mkaCak() const {#mkaCak}

*See also* [setMkaCak](networkmanager-macsecsetting.md#setMkaCak)()

### Setting::SecretFlags MacsecSetting::mkaCakFlags() const {#mkaCakFlags}

*See also* [setMkaCakFlags](networkmanager-macsecsetting.md#setMkaCakFlags)()

### QString MacsecSetting::mkaCkn() const {#mkaCkn}

*See also* [setMkaCkn](networkmanager-macsecsetting.md#setMkaCkn)()

### NetworkManager::MacsecSetting::Mode MacsecSetting::mode() const {#mode}

*See also* [setMode](networkmanager-macsecsetting.md#setMode)()

### QString MacsecSetting::parent() const {#parent}

*See also* [setParent](networkmanager-macsecsetting.md#setParent)()

### qint32 MacsecSetting::port() const {#port}

*See also* [setPort](networkmanager-macsecsetting.md#setPort)()

### bool MacsecSetting::sendSci() const {#sendSci}

*See also* [setSendSci](networkmanager-macsecsetting.md#setSendSci)()

### void MacsecSetting::setEncrypt(bool *encrypt*) {#setEncrypt}

*See also* [encrypt](networkmanager-macsecsetting.md#encrypt)()

### void MacsecSetting::setMkaCak(const QString &*mkaCak*) {#setMkaCak}

*See also* [mkaCak](networkmanager-macsecsetting.md#mkaCak)()

### void MacsecSetting::setMkaCakFlags(Setting::SecretFlags *flags*) {#setMkaCakFlags}

*See also* [mkaCakFlags](networkmanager-macsecsetting.md#mkaCakFlags)()

### void MacsecSetting::setMkaCkn(const QString &*mkaCkn*) {#setMkaCkn}

*See also* [mkaCkn](networkmanager-macsecsetting.md#mkaCkn)()

### void MacsecSetting::setMode(NetworkManager::MacsecSetting::Mode *mode*) {#setMode}

*See also* [mode](networkmanager-macsecsetting.md#mode)()

### void MacsecSetting::setParent(const QString &*parent*) {#setParent}

*See also* [parent](networkmanager-macsecsetting.md#parent)()

### void MacsecSetting::setPort(qint32 *port*) {#setPort}

*See also* [port](networkmanager-macsecsetting.md#port)()

### void MacsecSetting::setSendSci(bool *sendSci*) {#setSendSci}

*See also* [sendSci](networkmanager-macsecsetting.md#sendSci)()

### void MacsecSetting::setValidation(NetworkManager::MacsecSetting::Validation *validation*) {#setValidation}

*See also* [validation](networkmanager-macsecsetting.md#validation)()

### NetworkManager::MacsecSetting::Validation MacsecSetting::validation() const {#validation}

*See also* [setValidation](networkmanager-macsecsetting.md#setValidation)()
