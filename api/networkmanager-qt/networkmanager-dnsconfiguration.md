---
title: "NetworkManager::DnsConfiguration Class"
description: "This class represents IP configuration."
---

# NetworkManager::DnsConfiguration Class

This class represents IP configuration. [More...](#details)

- **Header:** `#include <NetworkManagerQt/DnsConfiguration>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`

[List of all members, including inherited members](networkmanager-dnsconfiguration-members.md)

## Public Functions

- [DnsConfiguration()](#DnsConfiguration)
- [DnsConfiguration(const QStringList &searches, const QStringList &options, const QList\<NetworkManager::DnsDomain\> domains)](#DnsConfiguration-2)
- [DnsConfiguration(const NetworkManager::DnsConfiguration &other)](#DnsConfiguration-1)
- [~DnsConfiguration()](#dtor.DnsConfiguration)
- [QList\<NetworkManager::DnsDomain\> domains() const](#domains)
- [void fromMap(const QVariantMap &map)](#fromMap)
- [QStringList options() const](#options)
- [QStringList searches() const](#searches)
- [void setDomains(const QList\<NetworkManager::DnsDomain\> &domains)](#setDomains)
- [void setOptions(const QStringList &list)](#setOptions)
- [void setSearches(const QStringList &list)](#setSearches)
- [QVariantMap toMap() const](#toMap)
- [NetworkManager::DnsConfiguration &DnsConfiguration::operator=(const NetworkManager::DnsConfiguration &other)](#operator-eq)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### DnsConfiguration::DnsConfiguration() {#DnsConfiguration}

Constructs an empty [DnsConfiguration](networkmanager-dnsconfiguration.md) object

### DnsConfiguration::DnsConfiguration(const QStringList &*searches*, const QStringList &*options*, const QList\<NetworkManager::DnsDomain\> *domains*) {#DnsConfiguration-2}

Constructs an initialized [DnsConfiguration](networkmanager-dnsconfiguration.md) object

### DnsConfiguration::DnsConfiguration(const NetworkManager::DnsConfiguration &*other*) {#DnsConfiguration-1}

Constructs a [DnsConfiguration](networkmanager-dnsconfiguration.md) object that is a copy of the object `other`.

### \[noexcept\] DnsConfiguration::~DnsConfiguration() {#dtor.DnsConfiguration}

Destroys this [DnsConfiguration](networkmanager-dnsconfiguration.md) object.

### QList\<NetworkManager::DnsDomain\> DnsConfiguration::domains() const {#domains}

Returns the list of domains

*See also* [setDomains](networkmanager-dnsconfiguration.md#setDomains)()

### void DnsConfiguration::fromMap(const QVariantMap &*map*) {#fromMap}

De-marshall from a map

### QStringList DnsConfiguration::options() const {#options}

Returns the list of resolver options

*See also* [setOptions](networkmanager-dnsconfiguration.md#setOptions)()

### QStringList DnsConfiguration::searches() const {#searches}

Returns the list of search domains

*See also* [setSearches](networkmanager-dnsconfiguration.md#setSearches)()

### void DnsConfiguration::setDomains(const QList\<NetworkManager::DnsDomain\> &*domains*) {#setDomains}

Sets the list of domains

*See also* [domains](networkmanager-dnsconfiguration.md#domains)()

### void DnsConfiguration::setOptions(const QStringList &*list*) {#setOptions}

Sets the list of resolver options

*See also* [options](networkmanager-dnsconfiguration.md#options)()

### void DnsConfiguration::setSearches(const QStringList &*list*) {#setSearches}

Sets the list of search domains

*See also* [searches](networkmanager-dnsconfiguration.md#searches)()

### QVariantMap DnsConfiguration::toMap() const {#toMap}

Marshall into a map

### NetworkManager::DnsConfiguration &DnsConfiguration::operator=(const NetworkManager::DnsConfiguration &*other*) {#operator-eq}

Makes a copy of the [DnsConfiguration](networkmanager-dnsconfiguration.md) object `other`.
