---
title: "NetworkManager::IpConfig Class"
description: "This class represents IP configuration."
---

# NetworkManager::IpConfig Class

This class represents IP configuration. [More...](#details)

- **Header:** `#include <NetworkManagerQt/IpConfig>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`

[List of all members, including inherited members](networkmanager-ipconfig-members.md)

## Public Functions

- [IpConfig()](#IpConfig)
- [IpConfig(const NetworkManager::IpAddresses &addresses, const QList\<QHostAddress\> &nameservers, const QStringList &domains, const NetworkManager::IpRoutes &routes)](#IpConfig-2)
- [IpConfig(const NetworkManager::IpConfig &other)](#IpConfig-1)
- [~IpConfig()](#dtor.IpConfig)
- [NetworkManager::IpAddresses addresses() const](#addresses)
- [QStringList dnsOptions() const](#dnsOptions)
- [QStringList domains() const](#domains)
- [QString gateway() const](#gateway)
- [bool isValid() const](#isValid)
- [QList\<QHostAddress\> nameservers() const](#nameservers)
- [NetworkManager::IpRoutes routes() const](#routes)
- [QStringList searches() const](#searches)
- [void setIPv4Path(const QString &path)](#setIPv4Path)
- [void setIPv6Path(const QString &path)](#setIPv6Path)
- [NetworkManager::IpConfig &IpConfig::operator=(const NetworkManager::IpConfig &other)](#operator-eq)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### IpConfig::IpConfig() {#IpConfig}

Constructs an empty [IpConfig](networkmanager-ipconfig.md) object.

### IpConfig::IpConfig(const NetworkManager::IpAddresses &*addresses*, const QList\<QHostAddress\> &*nameservers*, const QStringList &*domains*, const NetworkManager::IpRoutes &*routes*) {#IpConfig-2}

Constructs an IP config object with a list of `addresses`, `nameservers`, `domains` and `routes`.

### IpConfig::IpConfig(const NetworkManager::IpConfig &*other*) {#IpConfig-1}

Constructs an [IpConfig](networkmanager-ipconfig.md) object that is a copy of the object `other`.

### \[noexcept\] IpConfig::~IpConfig() {#dtor.IpConfig}

Destroys this [IpConfig](networkmanager-ipconfig.md) object.

### NetworkManager::IpAddresses IpConfig::addresses() const {#addresses}

Returns a list of IP addresses and gateway related to this configuration. Use [IpAddress::ip](https://doc.qt.io/qt-6/qnetworkaddressentry.html#ip)() to access the IP address and [IpAddress::gateway](networkmanager-ipaddress.md#gateway)() to access the gateway address.

### QStringList IpConfig::dnsOptions() const {#dnsOptions}

Returns a list of DNS options that modify the behaviour of the DNS resolver.

### QStringList IpConfig::domains() const {#domains}

Returns a list of domains related to this configuration.

### QString IpConfig::gateway() const {#gateway}

Returns the gateway in use

### bool IpConfig::isValid() const {#isValid}

Returns false if the list of IP addresses is empty

### QList\<QHostAddress\> IpConfig::nameservers() const {#nameservers}

Returns a list of nameservers related to this configuration.

### NetworkManager::IpRoutes IpConfig::routes() const {#routes}

Returns a list of static routes (not the default gateway) related to this configuration. Use [addresses](networkmanager-ipconfig.md#addresses)() to retrieve the default gateway.

### QStringList IpConfig::searches() const {#searches}

Returns a list of DNS searches.

### void IpConfig::setIPv4Path(const QString &*path*) {#setIPv4Path}

Configure this class using the information on the following `path`

### void IpConfig::setIPv6Path(const QString &*path*) {#setIPv6Path}

Configure this class using the information on the following `path`

### NetworkManager::IpConfig &IpConfig::operator=(const NetworkManager::IpConfig &*other*) {#operator-eq}

Makes a copy of the [IpConfig](networkmanager-ipconfig.md) object `other`.
