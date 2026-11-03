---
title: "NetworkManager::Ipv6Setting Class"
description: "Represents ipv6 setting."
---

# NetworkManager::Ipv6Setting Class

Represents ipv6 setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/Ipv6Setting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-ipv6setting-members.md)

## Public Types

- [enum Ipv6Setting::ConfigMethod](#ConfigMethod-enum)
- [enum Ipv6Setting::IPv6AddressGenMode](#IPv6AddressGenMode-enum)
- [enum Ipv6Setting::IPv6Privacy](#IPv6Privacy-enum)
- [Ipv6Setting::List](#List-typedef)
- [Ipv6Setting::Ptr](#Ptr-typedef)

## Public Functions

- [Ipv6Setting()](#Ipv6Setting)
- [Ipv6Setting(const NetworkManager::Ipv6Setting::Ptr &other)](#Ipv6Setting-1)
- [NMVariantMapList addressData() const](#addressData)
- [NetworkManager::Ipv6Setting::IPv6AddressGenMode addressGenMode() const](#addressGenMode)
- [QList\<NetworkManager::IpAddress\> addresses() const](#addresses)
- [qint32 dadTimeout() const](#dadTimeout)
- [QString dhcpDuid() const](#dhcpDuid)
- [QString dhcpHostname() const](#dhcpHostname)
- [qint32 dhcpTimeout() const](#dhcpTimeout)
- [QList\<QHostAddress\> dns() const](#dns)
- [QStringList dnsOptions() const](#dnsOptions)
- [QStringList dnsSearch() const](#dnsSearch)
- [bool ignoreAutoDns() const](#ignoreAutoDns)
- [bool ignoreAutoRoutes() const](#ignoreAutoRoutes)
- [bool mayFail() const](#mayFail)
- [NetworkManager::Ipv6Setting::ConfigMethod method() const](#method)
- [bool neverDefault() const](#neverDefault)
- [NetworkManager::Ipv6Setting::IPv6Privacy privacy() const](#privacy)
- [NMVariantMapList routeData() const](#routeData)
- [int routeMetric() const](#routeMetric)
- [quint32 routeTable() const](#routeTable)
- [QList\<NetworkManager::IpRoute\> routes() const](#routes)
- [void setAddressData(const NMVariantMapList &addressData)](#setAddressData)
- [void setAddressGenMode(NetworkManager::Ipv6Setting::IPv6AddressGenMode mode)](#setAddressGenMode)
- [void setAddresses(const QList\<NetworkManager::IpAddress\> ipv6addresses)](#setAddresses)
- [void setDadTimeout(qint32 timeout)](#setDadTimeout)
- [void setDhcpDuid(const QString &duid)](#setDhcpDuid)
- [void setDhcpHostname(const QString &hostname)](#setDhcpHostname)
- [void setDhcpTimeout(qint32 timeout)](#setDhcpTimeout)
- [void setDns(const QList\<QHostAddress\> &dns)](#setDns)
- [void setDnsOptions(const QStringList &options)](#setDnsOptions)
- [void setDnsSearch(const QStringList &domains)](#setDnsSearch)
- [void setIgnoreAutoDns(bool ignore)](#setIgnoreAutoDns)
- [void setIgnoreAutoRoutes(bool ignore)](#setIgnoreAutoRoutes)
- [void setMayFail(bool mayFail)](#setMayFail)
- [void setMethod(NetworkManager::Ipv6Setting::ConfigMethod method)](#setMethod)
- [void setNeverDefault(bool neverDefault)](#setNeverDefault)
- [void setPrivacy(NetworkManager::Ipv6Setting::IPv6Privacy privacy)](#setPrivacy)
- [void setRouteData(const NMVariantMapList &routeData)](#setRouteData)
- [void setRouteMetric(int metric)](#setRouteMetric)
- [void setRouteTable(quint32 routeTable)](#setRouteTable)
- [void setRoutes(const QList\<NetworkManager::IpRoute\> ipv6routes)](#setRoutes)
- [void setToken(const QString &token)](#setToken)
- [QString token() const](#token)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum Ipv6Setting::ConfigMethod {#ConfigMethod-enum}

| Constant | Value |   |
| --- | --- | --- |
| `NetworkManager::Ipv6Setting::Automatic` | `0` |   |
| `NetworkManager::Ipv6Setting::Dhcp` | `1` |   |
| `NetworkManager::Ipv6Setting::LinkLocal` | `2` |   |
| `NetworkManager::Ipv6Setting::Manual` | `3` |   |
| `NetworkManager::Ipv6Setting::Ignored` | `4` |   |
| `NetworkManager::Ipv6Setting::ConfigDisabled` | `5` | FIXME KF6: fix enum naming (possibly move to enum class) |

### enum Ipv6Setting::IPv6AddressGenMode {#IPv6AddressGenMode-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::Ipv6Setting::Eui64` | `0` |
| `NetworkManager::Ipv6Setting::StablePrivacy` | `1` |

### enum Ipv6Setting::IPv6Privacy {#IPv6Privacy-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::Ipv6Setting::Unknown` | `-1` |
| `NetworkManager::Ipv6Setting::Disabled` | `0` |
| `NetworkManager::Ipv6Setting::PreferPublic` | `1` |
| `NetworkManager::Ipv6Setting::PreferTemporary` | `2` |

### Ipv6Setting::List {#List-typedef}

### Ipv6Setting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### Ipv6Setting::Ipv6Setting() {#Ipv6Setting}

### \[explicit\] Ipv6Setting::Ipv6Setting(const NetworkManager::Ipv6Setting::Ptr &*other*) {#Ipv6Setting-1}

### NMVariantMapList Ipv6Setting::addressData() const {#addressData}

*See also* [setAddressData](networkmanager-ipv6setting.md#setAddressData)()

### NetworkManager::Ipv6Setting::IPv6AddressGenMode Ipv6Setting::addressGenMode() const {#addressGenMode}

*See also* [setAddressGenMode](networkmanager-ipv6setting.md#setAddressGenMode)()

### QList\<NetworkManager::IpAddress\> Ipv6Setting::addresses() const {#addresses}

*See also* [setAddresses](networkmanager-ipv6setting.md#setAddresses)()

### qint32 Ipv6Setting::dadTimeout() const {#dadTimeout}

*See also* [setDadTimeout](networkmanager-ipv6setting.md#setDadTimeout)()

### QString Ipv6Setting::dhcpDuid() const {#dhcpDuid}

*See also* [setDhcpDuid](networkmanager-ipv6setting.md#setDhcpDuid)()

### QString Ipv6Setting::dhcpHostname() const {#dhcpHostname}

*See also* [setDhcpHostname](networkmanager-ipv6setting.md#setDhcpHostname)()

### qint32 Ipv6Setting::dhcpTimeout() const {#dhcpTimeout}

*See also* [setDhcpTimeout](networkmanager-ipv6setting.md#setDhcpTimeout)()

### QList\<QHostAddress\> Ipv6Setting::dns() const {#dns}

*See also* [setDns](networkmanager-ipv6setting.md#setDns)()

### QStringList Ipv6Setting::dnsOptions() const {#dnsOptions}

*See also* [setDnsOptions](networkmanager-ipv6setting.md#setDnsOptions)()

### QStringList Ipv6Setting::dnsSearch() const {#dnsSearch}

*See also* [setDnsSearch](networkmanager-ipv6setting.md#setDnsSearch)()

### bool Ipv6Setting::ignoreAutoDns() const {#ignoreAutoDns}

*See also* [setIgnoreAutoDns](networkmanager-ipv6setting.md#setIgnoreAutoDns)()

### bool Ipv6Setting::ignoreAutoRoutes() const {#ignoreAutoRoutes}

*See also* [setIgnoreAutoRoutes](networkmanager-ipv6setting.md#setIgnoreAutoRoutes)()

### bool Ipv6Setting::mayFail() const {#mayFail}

*See also* [setMayFail](networkmanager-ipv6setting.md#setMayFail)()

### NetworkManager::Ipv6Setting::ConfigMethod Ipv6Setting::method() const {#method}

*See also* [setMethod](networkmanager-ipv6setting.md#setMethod)()

### bool Ipv6Setting::neverDefault() const {#neverDefault}

*See also* [setNeverDefault](networkmanager-ipv6setting.md#setNeverDefault)()

### NetworkManager::Ipv6Setting::IPv6Privacy Ipv6Setting::privacy() const {#privacy}

*See also* [setPrivacy](networkmanager-ipv6setting.md#setPrivacy)()

### NMVariantMapList Ipv6Setting::routeData() const {#routeData}

*See also* [setRouteData](networkmanager-ipv6setting.md#setRouteData)()

### int Ipv6Setting::routeMetric() const {#routeMetric}

*See also* [setRouteMetric](networkmanager-ipv6setting.md#setRouteMetric)()

### quint32 Ipv6Setting::routeTable() const {#routeTable}

*See also* [setRouteTable](networkmanager-ipv6setting.md#setRouteTable)()

### QList\<NetworkManager::IpRoute\> Ipv6Setting::routes() const {#routes}

*See also* [setRoutes](networkmanager-ipv6setting.md#setRoutes)()

### void Ipv6Setting::setAddressData(const NMVariantMapList &*addressData*) {#setAddressData}

*See also* [addressData](networkmanager-ipv6setting.md#addressData)()

### void Ipv6Setting::setAddressGenMode(NetworkManager::Ipv6Setting::IPv6AddressGenMode *mode*) {#setAddressGenMode}

*See also* [addressGenMode](networkmanager-ipv6setting.md#addressGenMode)()

### void Ipv6Setting::setAddresses(const QList\<NetworkManager::IpAddress\> *ipv6addresses*) {#setAddresses}

*See also* [addresses](networkmanager-ipv6setting.md#addresses)()

### void Ipv6Setting::setDadTimeout(qint32 *timeout*) {#setDadTimeout}

*See also* [dadTimeout](networkmanager-ipv6setting.md#dadTimeout)()

### void Ipv6Setting::setDhcpDuid(const QString &*duid*) {#setDhcpDuid}

*See also* [dhcpDuid](networkmanager-ipv6setting.md#dhcpDuid)()

### void Ipv6Setting::setDhcpHostname(const QString &*hostname*) {#setDhcpHostname}

*See also* [dhcpHostname](networkmanager-ipv6setting.md#dhcpHostname)()

### void Ipv6Setting::setDhcpTimeout(qint32 *timeout*) {#setDhcpTimeout}

*See also* [dhcpTimeout](networkmanager-ipv6setting.md#dhcpTimeout)()

### void Ipv6Setting::setDns(const QList\<QHostAddress\> &*dns*) {#setDns}

*See also* [dns](networkmanager-ipv6setting.md#dns)()

### void Ipv6Setting::setDnsOptions(const QStringList &*options*) {#setDnsOptions}

*See also* [dnsOptions](networkmanager-ipv6setting.md#dnsOptions)()

### void Ipv6Setting::setDnsSearch(const QStringList &*domains*) {#setDnsSearch}

*See also* [dnsSearch](networkmanager-ipv6setting.md#dnsSearch)()

### void Ipv6Setting::setIgnoreAutoDns(bool *ignore*) {#setIgnoreAutoDns}

*See also* [ignoreAutoDns](networkmanager-ipv6setting.md#ignoreAutoDns)()

### void Ipv6Setting::setIgnoreAutoRoutes(bool *ignore*) {#setIgnoreAutoRoutes}

*See also* [ignoreAutoRoutes](networkmanager-ipv6setting.md#ignoreAutoRoutes)()

### void Ipv6Setting::setMayFail(bool *mayFail*) {#setMayFail}

*See also* [mayFail](networkmanager-ipv6setting.md#mayFail)()

### void Ipv6Setting::setMethod(NetworkManager::Ipv6Setting::ConfigMethod *method*) {#setMethod}

*See also* [method](networkmanager-ipv6setting.md#method)()

### void Ipv6Setting::setNeverDefault(bool *neverDefault*) {#setNeverDefault}

*See also* [neverDefault](networkmanager-ipv6setting.md#neverDefault)()

### void Ipv6Setting::setPrivacy(NetworkManager::Ipv6Setting::IPv6Privacy *privacy*) {#setPrivacy}

*See also* [privacy](networkmanager-ipv6setting.md#privacy)()

### void Ipv6Setting::setRouteData(const NMVariantMapList &*routeData*) {#setRouteData}

*See also* [routeData](networkmanager-ipv6setting.md#routeData)()

### void Ipv6Setting::setRouteMetric(int *metric*) {#setRouteMetric}

*See also* [routeMetric](networkmanager-ipv6setting.md#routeMetric)()

### void Ipv6Setting::setRouteTable(quint32 *routeTable*) {#setRouteTable}

*See also* [routeTable](networkmanager-ipv6setting.md#routeTable)()

### void Ipv6Setting::setRoutes(const QList\<NetworkManager::IpRoute\> *ipv6routes*) {#setRoutes}

*See also* [routes](networkmanager-ipv6setting.md#routes)()

### void Ipv6Setting::setToken(const QString &*token*) {#setToken}

*See also* [token](networkmanager-ipv6setting.md#token)()

### QString Ipv6Setting::token() const {#token}

*See also* [setToken](networkmanager-ipv6setting.md#setToken)()
