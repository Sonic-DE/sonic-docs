---
title: "NetworkManager::DnsDomain Class"
description: "This class represents the configuration for a DNS domain."
---

# NetworkManager::DnsDomain Class

This class represents the configuration for a DNS domain. [More...](#details)

- **Header:** `#include <NetworkManagerQt/DnsDomain>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`

[List of all members, including inherited members](networkmanager-dnsdomain-members.md)

## Public Functions

- [DnsDomain()](#DnsDomain)
- [DnsDomain(const QString &name, const QList\<QHostAddress\> &servers, const QStringList &options)](#DnsDomain-2)
- [DnsDomain(const NetworkManager::DnsDomain &other)](#DnsDomain-1)
- [~DnsDomain()](#dtor.DnsDomain)
- [QString name() const](#name)
- [QStringList options() const](#options)
- [QList\<QHostAddress\> servers() const](#servers)
- [void setName(const QString &name)](#setName)
- [void setOptions(const QStringList &list)](#setOptions)
- [void setServers(const QList\<QHostAddress\> &list)](#setServers)
- [NetworkManager::DnsDomain &DnsDomain::operator=(const NetworkManager::DnsDomain &other)](#operator-eq)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### DnsDomain::DnsDomain() {#DnsDomain}

Constructs a [DnsDomain](networkmanager-dnsdomain.md) object

### DnsDomain::DnsDomain(const QString &*name*, const QList\<QHostAddress\> &*servers*, const QStringList &*options*) {#DnsDomain-2}

Constructs a [DnsDomain](networkmanager-dnsdomain.md) object with a list of

### DnsDomain::DnsDomain(const NetworkManager::DnsDomain &*other*) {#DnsDomain-1}

Constructs a [DnsDomain](networkmanager-dnsdomain.md) object that is a copy of the object `other`.

### \[noexcept\] DnsDomain::~DnsDomain() {#dtor.DnsDomain}

Destroys this [DnsDomain](networkmanager-dnsdomain.md) object.

### QString DnsDomain::name() const {#name}

Returns the domain name

*See also* [setName](networkmanager-dnsdomain.md#setName)()

### QStringList DnsDomain::options() const {#options}

Returns the list of resolver options

*See also* [setOptions](networkmanager-dnsdomain.md#setOptions)()

### QList\<QHostAddress\> DnsDomain::servers() const {#servers}

Returns the list of servers

*See also* [setServers](networkmanager-dnsdomain.md#setServers)()

### void DnsDomain::setName(const QString &*name*) {#setName}

Sets the domain name

*See also* [name](networkmanager-dnsdomain.md#name)()

### void DnsDomain::setOptions(const QStringList &*list*) {#setOptions}

Sets the list of resolver options

*See also* [options](networkmanager-dnsdomain.md#options)()

### void DnsDomain::setServers(const QList\<QHostAddress\> &*list*) {#setServers}

Sets the list of servers

*See also* [servers](networkmanager-dnsdomain.md#servers)()

### NetworkManager::DnsDomain &DnsDomain::operator=(const NetworkManager::DnsDomain &*other*) {#operator-eq}

Makes a copy of the [DnsDomain](networkmanager-dnsdomain.md) object `other`.
