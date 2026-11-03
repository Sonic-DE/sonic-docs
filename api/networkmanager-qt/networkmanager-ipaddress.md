---
title: "NetworkManager::IpAddress Class"
description: "This class represents IP address."
---

# NetworkManager::IpAddress Class

This class represents IP address. [More...](#details)

- **Header:** `#include <NetworkManagerQt/IpAddress>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [QNetworkAddressEntry](https://doc.qt.io/qt-6/qnetworkaddressentry.html)

[List of all members, including inherited members](networkmanager-ipaddress-members.md)

## Public Functions

- [IpAddress()](#IpAddress)
- [IpAddress(const NetworkManager::IpAddress &other)](#IpAddress-1)
- [~IpAddress()](#dtor.IpAddress)
- [QHostAddress gateway() const](#gateway)
- [bool isValid() const](#isValid)
- [void setGateway(const QHostAddress &gateway)](#setGateway)
- [NetworkManager::IpAddress &IpAddress::operator=(const NetworkManager::IpAddress &other)](#operator-eq)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### IpAddress::IpAddress() {#IpAddress}

Constructs an empty [IpAddress](networkmanager-ipaddress.md) object.

### IpAddress::IpAddress(const NetworkManager::IpAddress &*other*) {#IpAddress-1}

Constructs an [IpAddress](networkmanager-ipaddress.md) object that is a copy of the object other.

### \[noexcept\] IpAddress::~IpAddress() {#dtor.IpAddress}

Destroys this [IpAddress](networkmanager-ipaddress.md) object.

### QHostAddress IpAddress::gateway() const {#gateway}

Returns the default gateway of this object.

*See also* [setGateway](networkmanager-ipaddress.md#setGateway)()

### bool IpAddress::isValid() const {#isValid}

Return if the IP address is defined.

### void IpAddress::setGateway(const QHostAddress &*gateway*) {#setGateway}

Defines the default `gateway` of this object.

*See also* [gateway](networkmanager-ipaddress.md#gateway)()

### NetworkManager::IpAddress &IpAddress::operator=(const NetworkManager::IpAddress &*other*) {#operator-eq}

Makes a copy of the [IpAddress](networkmanager-ipaddress.md) object `other`.
