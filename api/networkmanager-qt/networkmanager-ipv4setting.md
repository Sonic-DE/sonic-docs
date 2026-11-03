---
title: "NetworkManager::Ipv4Setting Class"
description: "Represents ipv4 setting."
---

# NetworkManager::Ipv4Setting Class

Represents ipv4 setting. [More...](#details)

- **Header:** `#include <NetworkManagerQt/Ipv4Setting>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [NetworkManager::Setting](networkmanager-setting.md)

[List of all members, including inherited members](networkmanager-ipv4setting-members.md)

## Public Types

- [enum Ipv4Setting::ConfigMethod](#ConfigMethod-enum)
- [Ipv4Setting::List](#List-typedef)
- [Ipv4Setting::Ptr](#Ptr-typedef)

## Public Functions

- [Ipv4Setting()](#Ipv4Setting)
- [Ipv4Setting(const NetworkManager::Ipv4Setting::Ptr &other)](#Ipv4Setting-1)
- [NMVariantMapList addressData() const](#addressData)
- [QList\<NetworkManager::IpAddress\> addresses() const](#addresses)
- [qint32 dadTimeout() const](#dadTimeout)
- [QString dhcpClientId() const](#dhcpClientId)
- [QString dhcpFqdn() const](#dhcpFqdn)
- [QString dhcpHostname() const](#dhcpHostname)
- [bool dhcpSendHostname() const](#dhcpSendHostname)
- [QList\<QHostAddress\> dns() const](#dns)
- [QStringList dnsOptions() const](#dnsOptions)
- [qint32 dnsPriority() const](#dnsPriority)
- [QStringList dnsSearch() const](#dnsSearch)
- [QString gateway() const](#gateway)
- [bool ignoreAutoDns() const](#ignoreAutoDns)
- [bool ignoreAutoRoutes() const](#ignoreAutoRoutes)
- [bool mayFail() const](#mayFail)
- [NetworkManager::Ipv4Setting::ConfigMethod method() const](#method)
- [bool neverDefault() const](#neverDefault)
- [NMVariantMapList routeData() const](#routeData)
- [int routeMetric() const](#routeMetric)
- [QList\<NetworkManager::IpRoute\> routes() const](#routes)
- [void setAddressData(const NMVariantMapList &addressData)](#setAddressData)
- [void setAddresses(const QList\<NetworkManager::IpAddress\> &ipv4addresses)](#setAddresses)
- [void setDadTimeout(qint32 timeout)](#setDadTimeout)
- [void setDhcpClientId(const QString &id)](#setDhcpClientId)
- [void setDhcpFqdn(const QString &fqdn)](#setDhcpFqdn)
- [void setDhcpHostname(const QString &hostname)](#setDhcpHostname)
- [void setDhcpSendHostname(bool send)](#setDhcpSendHostname)
- [void setDns(const QList\<QHostAddress\> &dns)](#setDns)
- [void setDnsOptions(const QStringList &options)](#setDnsOptions)
- [void setDnsPriority(qint32 priority)](#setDnsPriority)
- [void setDnsSearch(const QStringList &domains)](#setDnsSearch)
- [void setGateway(const QString &gateway)](#setGateway)
- [void setIgnoreAutoDns(bool ignore)](#setIgnoreAutoDns)
- [void setIgnoreAutoRoutes(bool ignore)](#setIgnoreAutoRoutes)
- [void setMayFail(bool mayFail)](#setMayFail)
- [void setMethod(NetworkManager::Ipv4Setting::ConfigMethod method)](#setMethod)
- [void setNeverDefault(bool neverDefault)](#setNeverDefault)
- [void setRouteData(const NMVariantMapList &routeData)](#setRouteData)
- [void setRouteMetric(int metric)](#setRouteMetric)
- [void setRoutes(const QList\<NetworkManager::IpRoute\> &ipv4routes)](#setRoutes)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum Ipv4Setting::ConfigMethod {#ConfigMethod-enum}

| Constant |   |
| --- | --- |
| `NetworkManager::Ipv4Setting::Automatic` | `0` |
| `NetworkManager::Ipv4Setting::LinkLocal` | `1` |
| `NetworkManager::Ipv4Setting::Manual` | `2` |
| `NetworkManager::Ipv4Setting::Shared` | `3` |
| `NetworkManager::Ipv4Setting::Disabled` | `4` |

### Ipv4Setting::List {#List-typedef}

### Ipv4Setting::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### Ipv4Setting::Ipv4Setting() {#Ipv4Setting}

### \[explicit\] Ipv4Setting::Ipv4Setting(const NetworkManager::Ipv4Setting::Ptr &*other*) {#Ipv4Setting-1}

### NMVariantMapList Ipv4Setting::addressData() const {#addressData}

*See also* [setAddressData](networkmanager-ipv4setting.md#setAddressData)()

### QList\<NetworkManager::IpAddress\> Ipv4Setting::addresses() const {#addresses}

*See also* [setAddresses](networkmanager-ipv4setting.md#setAddresses)()

### qint32 Ipv4Setting::dadTimeout() const {#dadTimeout}

*See also* [setDadTimeout](networkmanager-ipv4setting.md#setDadTimeout)()

### QString Ipv4Setting::dhcpClientId() const {#dhcpClientId}

*See also* [setDhcpClientId](networkmanager-ipv4setting.md#setDhcpClientId)()

### QString Ipv4Setting::dhcpFqdn() const {#dhcpFqdn}

*See also* [setDhcpFqdn](networkmanager-ipv4setting.md#setDhcpFqdn)()

### QString Ipv4Setting::dhcpHostname() const {#dhcpHostname}

*See also* [setDhcpHostname](networkmanager-ipv4setting.md#setDhcpHostname)()

### bool Ipv4Setting::dhcpSendHostname() const {#dhcpSendHostname}

*See also* [setDhcpSendHostname](networkmanager-ipv4setting.md#setDhcpSendHostname)()

### QList\<QHostAddress\> Ipv4Setting::dns() const {#dns}

*See also* [setDns](networkmanager-ipv4setting.md#setDns)()

### QStringList Ipv4Setting::dnsOptions() const {#dnsOptions}

*See also* [setDnsOptions](networkmanager-ipv4setting.md#setDnsOptions)()

### qint32 Ipv4Setting::dnsPriority() const {#dnsPriority}

*See also* [setDnsPriority](networkmanager-ipv4setting.md#setDnsPriority)()

### QStringList Ipv4Setting::dnsSearch() const {#dnsSearch}

*See also* [setDnsSearch](networkmanager-ipv4setting.md#setDnsSearch)()

### QString Ipv4Setting::gateway() const {#gateway}

*See also* [setGateway](networkmanager-ipv4setting.md#setGateway)()

### bool Ipv4Setting::ignoreAutoDns() const {#ignoreAutoDns}

*See also* [setIgnoreAutoDns](networkmanager-ipv4setting.md#setIgnoreAutoDns)()

### bool Ipv4Setting::ignoreAutoRoutes() const {#ignoreAutoRoutes}

*See also* [setIgnoreAutoRoutes](networkmanager-ipv4setting.md#setIgnoreAutoRoutes)()

### bool Ipv4Setting::mayFail() const {#mayFail}

*See also* [setMayFail](networkmanager-ipv4setting.md#setMayFail)()

### NetworkManager::Ipv4Setting::ConfigMethod Ipv4Setting::method() const {#method}

*See also* [setMethod](networkmanager-ipv4setting.md#setMethod)()

### bool Ipv4Setting::neverDefault() const {#neverDefault}

*See also* [setNeverDefault](networkmanager-ipv4setting.md#setNeverDefault)()

### NMVariantMapList Ipv4Setting::routeData() const {#routeData}

*See also* [setRouteData](networkmanager-ipv4setting.md#setRouteData)()

### int Ipv4Setting::routeMetric() const {#routeMetric}

*See also* [setRouteMetric](networkmanager-ipv4setting.md#setRouteMetric)()

### QList\<NetworkManager::IpRoute\> Ipv4Setting::routes() const {#routes}

*See also* [setRoutes](networkmanager-ipv4setting.md#setRoutes)()

### void Ipv4Setting::setAddressData(const NMVariantMapList &*addressData*) {#setAddressData}

*See also* [addressData](networkmanager-ipv4setting.md#addressData)()

### void Ipv4Setting::setAddresses(const QList\<NetworkManager::IpAddress\> &*ipv4addresses*) {#setAddresses}

*See also* [addresses](networkmanager-ipv4setting.md#addresses)()

### void Ipv4Setting::setDadTimeout(qint32 *timeout*) {#setDadTimeout}

*See also* [dadTimeout](networkmanager-ipv4setting.md#dadTimeout)()

### void Ipv4Setting::setDhcpClientId(const QString &*id*) {#setDhcpClientId}

*See also* [dhcpClientId](networkmanager-ipv4setting.md#dhcpClientId)()

### void Ipv4Setting::setDhcpFqdn(const QString &*fqdn*) {#setDhcpFqdn}

*See also* [dhcpFqdn](networkmanager-ipv4setting.md#dhcpFqdn)()

### void Ipv4Setting::setDhcpHostname(const QString &*hostname*) {#setDhcpHostname}

*See also* [dhcpHostname](networkmanager-ipv4setting.md#dhcpHostname)()

### void Ipv4Setting::setDhcpSendHostname(bool *send*) {#setDhcpSendHostname}

*See also* [dhcpSendHostname](networkmanager-ipv4setting.md#dhcpSendHostname)()

### void Ipv4Setting::setDns(const QList\<QHostAddress\> &*dns*) {#setDns}

*See also* [dns](networkmanager-ipv4setting.md#dns)()

### void Ipv4Setting::setDnsOptions(const QStringList &*options*) {#setDnsOptions}

*See also* [dnsOptions](networkmanager-ipv4setting.md#dnsOptions)()

### void Ipv4Setting::setDnsPriority(qint32 *priority*) {#setDnsPriority}

*See also* [dnsPriority](networkmanager-ipv4setting.md#dnsPriority)()

### void Ipv4Setting::setDnsSearch(const QStringList &*domains*) {#setDnsSearch}

*See also* [dnsSearch](networkmanager-ipv4setting.md#dnsSearch)()

### void Ipv4Setting::setGateway(const QString &*gateway*) {#setGateway}

*See also* [gateway](networkmanager-ipv4setting.md#gateway)()

### void Ipv4Setting::setIgnoreAutoDns(bool *ignore*) {#setIgnoreAutoDns}

*See also* [ignoreAutoDns](networkmanager-ipv4setting.md#ignoreAutoDns)()

### void Ipv4Setting::setIgnoreAutoRoutes(bool *ignore*) {#setIgnoreAutoRoutes}

*See also* [ignoreAutoRoutes](networkmanager-ipv4setting.md#ignoreAutoRoutes)()

### void Ipv4Setting::setMayFail(bool *mayFail*) {#setMayFail}

*See also* [mayFail](networkmanager-ipv4setting.md#mayFail)()

### void Ipv4Setting::setMethod(NetworkManager::Ipv4Setting::ConfigMethod *method*) {#setMethod}

*See also* [method](networkmanager-ipv4setting.md#method)()

### void Ipv4Setting::setNeverDefault(bool *neverDefault*) {#setNeverDefault}

*See also* [neverDefault](networkmanager-ipv4setting.md#neverDefault)()

### void Ipv4Setting::setRouteData(const NMVariantMapList &*routeData*) {#setRouteData}

*See also* [routeData](networkmanager-ipv4setting.md#routeData)()

### void Ipv4Setting::setRouteMetric(int *metric*) {#setRouteMetric}

*See also* [routeMetric](networkmanager-ipv4setting.md#routeMetric)()

### void Ipv4Setting::setRoutes(const QList\<NetworkManager::IpRoute\> &*ipv4routes*) {#setRoutes}

*See also* [routes](networkmanager-ipv4setting.md#routes)()
