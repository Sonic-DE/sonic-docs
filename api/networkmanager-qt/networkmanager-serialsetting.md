---
title: "NetworkManager::SerialSetting Class"
description: "Represents serial setting."
---

# NetworkManager::SerialSetting Class

Represents serial setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/SerialSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-serialsetting-members.md)

## Public Types

- [SerialSetting::List](#List-typedef)
- [enum SerialSetting::Parity](#Parity-enum)
- [SerialSetting::Ptr](#Ptr-typedef)

## Public Functions

- [SerialSetting()](#SerialSetting)
- [SerialSetting(const NetworkManager::SerialSetting::Ptr &other)](#SerialSetting-1)
- [quint32 baud() const](#baud)
- [quint32 bits() const](#bits)
- [NetworkManager::SerialSetting::Parity parity() const](#parity)
- [quint64 sendDelay() const](#sendDelay)
- [void setBaud(quint32 speed)](#setBaud)
- [void setBits(quint32 byteWidth)](#setBits)
- [void setParity(NetworkManager::SerialSetting::Parity paritysetting)](#setParity)
- [void setSendDelay(quint64 delay)](#setSendDelay)
- [void setStopbits(quint32 number)](#setStopbits)
- [quint32 stopbits() const](#stopbits)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### SerialSetting::List {#List-typedef}

### enum SerialSetting::Parity {#Parity-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::SerialSetting::NoParity` | `0` |
| `NetworkManager::SerialSetting::EvenParity` | `1` |
| `NetworkManager::SerialSetting::OddParity` | `2` |

### SerialSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### SerialSetting::SerialSetting() {#SerialSetting}

### \[explicit\] SerialSetting::SerialSetting(const NetworkManager::SerialSetting::Ptr &*other*) {#SerialSetting-1}

### quint32 SerialSetting::baud() const {#baud}

*See also* [setBaud](networkmanager-serialsetting.md#setBaud)()

### quint32 SerialSetting::bits() const {#bits}

*See also* [setBits](networkmanager-serialsetting.md#setBits)()

### NetworkManager::SerialSetting::Parity SerialSetting::parity() const {#parity}

*See also* [setParity](networkmanager-serialsetting.md#setParity)()

### quint64 SerialSetting::sendDelay() const {#sendDelay}

*See also* [setSendDelay](networkmanager-serialsetting.md#setSendDelay)()

### void SerialSetting::setBaud(quint32 *speed*) {#setBaud}

*See also* [baud](networkmanager-serialsetting.md#baud)()

### void SerialSetting::setBits(quint32 *byteWidth*) {#setBits}

*See also* [bits](networkmanager-serialsetting.md#bits)()

### void SerialSetting::setParity(NetworkManager::SerialSetting::Parity *paritysetting*) {#setParity}

*See also* [parity](networkmanager-serialsetting.md#parity)()

### void SerialSetting::setSendDelay(quint64 *delay*) {#setSendDelay}

*See also* [sendDelay](networkmanager-serialsetting.md#sendDelay)()

### void SerialSetting::setStopbits(quint32 *number*) {#setStopbits}

*See also* [stopbits](networkmanager-serialsetting.md#stopbits)()

### quint32 SerialSetting::stopbits() const {#stopbits}

*See also* [setStopbits](networkmanager-serialsetting.md#setStopbits)()
