---
title: "ModemManager::IpConfig Class"
description: "This class represents IP configuration."
---

# ModemManager::IpConfig Class

This class represents IP configuration. [More...](#details)

- **Header:** `#include <ModemManagerQt/Bearer>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ModemManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::ModemManagerQt)`

[List of all members, including inherited members](modemmanager-ipconfig-members.md)

## Public Functions

- [IpConfig()](#IpConfig)
- [IpConfig(const ModemManager::IpConfig &other)](#IpConfig-1)
- [~IpConfig()](#dtor.IpConfig)
- [QString address() const](#address)
- [QString dns1() const](#dns1)
- [QString dns2() const](#dns2)
- [QString dns3() const](#dns3)
- [QString gateway() const](#gateway)
- [MMBearerIpMethod method() const](#method)
- [uint prefix() const](#prefix)
- [void setAddress(const QString &address)](#setAddress)
- [void setDns1(const QString &dns1)](#setDns1)
- [void setDns2(const QString &dns2)](#setDns2)
- [void setDns3(const QString &dns3)](#setDns3)
- [void setGateway(const QString &gateway)](#setGateway)
- [void setMethod(MMBearerIpMethod method)](#setMethod)
- [void setPrefix(uint prefix)](#setPrefix)
- [ModemManager::IpConfig &IpConfig::operator=(const ModemManager::IpConfig &other)](#operator-eq)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### IpConfig::IpConfig() {#IpConfig}

Constructs an empty IP config object

### IpConfig::IpConfig(const ModemManager::IpConfig &*other*) {#IpConfig-1}

Constructs an [IpConfig](modemmanager-ipconfig.md) object that is a copy of the object `other`.

### \[noexcept\] IpConfig::~IpConfig() {#dtor.IpConfig}

Destroys this [IpConfig](modemmanager-ipconfig.md) object.

### QString IpConfig::address() const {#address}

Returns the IP address

*See also* [setAddress](modemmanager-ipconfig.md#setAddress)()

### QString IpConfig::dns1() const {#dns1}

Returns the IP address of the first DNS server

*See also* [setDns1](modemmanager-ipconfig.md#setDns1)()

### QString IpConfig::dns2() const {#dns2}

Returns the IP address of the second DNS server

*See also* [setDns2](modemmanager-ipconfig.md#setDns2)()

### QString IpConfig::dns3() const {#dns3}

Returns the IP address of the third DNS server

*See also* [setDns3](modemmanager-ipconfig.md#setDns3)()

### QString IpConfig::gateway() const {#gateway}

Returns the IP address of the default gateway

*See also* [setGateway](modemmanager-ipconfig.md#setGateway)()

### MMBearerIpMethod IpConfig::method() const {#method}

Returns the MMBearerIpMethod

*See also* [setMethod](modemmanager-ipconfig.md#setMethod)()

### uint IpConfig::prefix() const {#prefix}

Returns the numeric CIDR network prefix (ie, 24, 32, etc)

*See also* [setPrefix](modemmanager-ipconfig.md#setPrefix)()

### void IpConfig::setAddress(const QString &*address*) {#setAddress}

Sets the IP address

*See also* [address](modemmanager-ipconfig.md#address)()

### void IpConfig::setDns1(const QString &*dns1*) {#setDns1}

Sets the IP address of the first DNS server

*See also* [dns1](modemmanager-ipconfig.md#dns1)()

### void IpConfig::setDns2(const QString &*dns2*) {#setDns2}

Sets the IP address of the second DNS server

*See also* [dns2](modemmanager-ipconfig.md#dns2)()

### void IpConfig::setDns3(const QString &*dns3*) {#setDns3}

Sets the IP address of the third DNS server

*See also* [dns3](modemmanager-ipconfig.md#dns3)()

### void IpConfig::setGateway(const QString &*gateway*) {#setGateway}

Sets the IP address of the default gateway

*See also* [gateway](modemmanager-ipconfig.md#gateway)()

### void IpConfig::setMethod(MMBearerIpMethod *method*) {#setMethod}

Sets the MMBearerIpMethod

*See also* [method](modemmanager-ipconfig.md#method)()

### void IpConfig::setPrefix(uint *prefix*) {#setPrefix}

Sets the numeric CIDR network prefix

*See also* [prefix](modemmanager-ipconfig.md#prefix)()

### ModemManager::IpConfig &IpConfig::operator=(const ModemManager::IpConfig &*other*) {#operator-eq}

Makes a copy of the [IpConfig](modemmanager-ipconfig.md) object `other`.
