---
title: "NetworkManager::BridgeSetting Class"
description: "Represents bridge setting."
---

# NetworkManager::BridgeSetting Class

Represents bridge setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/BridgeSetting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-bridgesetting-members.md)

## Public Types

- [BridgeSetting::List](#List-typedef)
- [BridgeSetting::Ptr](#Ptr-typedef)

## Public Functions

- [BridgeSetting()](#BridgeSetting)
- [BridgeSetting(const NetworkManager::BridgeSetting::Ptr &other)](#BridgeSetting-1)
- [quint32 agingTime() const](#agingTime)
- [quint32 forwardDelay() const](#forwardDelay)
- [quint32 helloTime() const](#helloTime)
- [QString interfaceName() const](#interfaceName)
- [QByteArray macAddress() const](#macAddress)
- [quint32 maxAge() const](#maxAge)
- [bool multicastSnooping() const](#multicastSnooping)
- [quint32 priority() const](#priority)
- [void setAgingTime(quint32 time)](#setAgingTime)
- [void setForwardDelay(quint32 delay)](#setForwardDelay)
- [void setHelloTime(quint32 time)](#setHelloTime)
- [void setInterfaceName(const QString &name)](#setInterfaceName)
- [void setMacAddress(const QByteArray &address)](#setMacAddress)
- [void setMaxAge(quint32 age)](#setMaxAge)
- [void setMulticastSnooping(bool snooping)](#setMulticastSnooping)
- [void setPriority(quint32 priority)](#setPriority)
- [void setStp(bool enabled)](#setStp)
- [bool stp() const](#stp)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### BridgeSetting::List {#List-typedef}

### BridgeSetting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### BridgeSetting::BridgeSetting() {#BridgeSetting}

### \[explicit\] BridgeSetting::BridgeSetting(const NetworkManager::BridgeSetting::Ptr &*other*) {#BridgeSetting-1}

### quint32 BridgeSetting::agingTime() const {#agingTime}

*See also* [setAgingTime](networkmanager-bridgesetting.md#setAgingTime)()

### quint32 BridgeSetting::forwardDelay() const {#forwardDelay}

*See also* [setForwardDelay](networkmanager-bridgesetting.md#setForwardDelay)()

### quint32 BridgeSetting::helloTime() const {#helloTime}

*See also* [setHelloTime](networkmanager-bridgesetting.md#setHelloTime)()

### QString BridgeSetting::interfaceName() const {#interfaceName}

*See also* [setInterfaceName](networkmanager-bridgesetting.md#setInterfaceName)()

### QByteArray BridgeSetting::macAddress() const {#macAddress}

*See also* [setMacAddress](networkmanager-bridgesetting.md#setMacAddress)()

### quint32 BridgeSetting::maxAge() const {#maxAge}

*See also* [setMaxAge](networkmanager-bridgesetting.md#setMaxAge)()

### bool BridgeSetting::multicastSnooping() const {#multicastSnooping}

*See also* [setMulticastSnooping](networkmanager-bridgesetting.md#setMulticastSnooping)()

### quint32 BridgeSetting::priority() const {#priority}

*See also* [setPriority](networkmanager-bridgesetting.md#setPriority)()

### void BridgeSetting::setAgingTime(quint32 *time*) {#setAgingTime}

*See also* [agingTime](networkmanager-bridgesetting.md#agingTime)()

### void BridgeSetting::setForwardDelay(quint32 *delay*) {#setForwardDelay}

*See also* [forwardDelay](networkmanager-bridgesetting.md#forwardDelay)()

### void BridgeSetting::setHelloTime(quint32 *time*) {#setHelloTime}

*See also* [helloTime](networkmanager-bridgesetting.md#helloTime)()

### void BridgeSetting::setInterfaceName(const QString &*name*) {#setInterfaceName}

*See also* [interfaceName](networkmanager-bridgesetting.md#interfaceName)()

### void BridgeSetting::setMacAddress(const QByteArray &*address*) {#setMacAddress}

*See also* [macAddress](networkmanager-bridgesetting.md#macAddress)()

### void BridgeSetting::setMaxAge(quint32 *age*) {#setMaxAge}

*See also* [maxAge](networkmanager-bridgesetting.md#maxAge)()

### void BridgeSetting::setMulticastSnooping(bool *snooping*) {#setMulticastSnooping}

*See also* [multicastSnooping](networkmanager-bridgesetting.md#multicastSnooping)()

### void BridgeSetting::setPriority(quint32 *priority*) {#setPriority}

*See also* [priority](networkmanager-bridgesetting.md#priority)()

### void BridgeSetting::setStp(bool *enabled*) {#setStp}

*See also* [stp](networkmanager-bridgesetting.md#stp)()

### bool BridgeSetting::stp() const {#stp}

*See also* [setStp](networkmanager-bridgesetting.md#setStp)()
