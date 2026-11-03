---
title: "NetworkManager::IpRoute Class"
description: "This class represents IP route."
---

# NetworkManager::IpRoute Class

This class represents IP route. [More...](#details)

- **Header:** `#include <NetworkManagerQt/IpRoute>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NetworkManagerQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::NetworkManagerQt)`
- **Inherits:** [QNetworkAddressEntry](https://doc.qt.io/qt-6/qnetworkaddressentry.html)

[List of all members, including inherited members](networkmanager-iproute-members.md)

## Public Functions

- [IpRoute()](#IpRoute)
- [IpRoute(const NetworkManager::IpRoute &other)](#IpRoute-1)
- [~IpRoute()](#dtor.IpRoute)
- [bool isValid() const](#isValid)
- [quint32 metric() const](#metric)
- [QHostAddress nextHop() const](#nextHop)
- [void setMetric(quint32 metric)](#setMetric)
- [void setNextHop(const QHostAddress &nextHop) const](#setNextHop)
- [NetworkManager::IpRoute &IpRoute::operator=(const NetworkManager::IpRoute &other)](#operator-eq)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### IpRoute::IpRoute() {#IpRoute}

Constructs an empty [IpRoute](networkmanager-iproute.md) object.

### IpRoute::IpRoute(const NetworkManager::IpRoute &*other*) {#IpRoute-1}

Constructs an [IpRoute](networkmanager-iproute.md) object that is a copy of the object `other`.

### \[noexcept\] IpRoute::~IpRoute() {#dtor.IpRoute}

Destroys this [IpRoute](networkmanager-iproute.md) object.

### bool IpRoute::isValid() const {#isValid}

Returns true if the route IP is defined.

### quint32 IpRoute::metric() const {#metric}

Returns the route metric number of the given route.

*See also* [setMetric](networkmanager-iproute.md#setMetric)()

### QHostAddress IpRoute::nextHop() const {#nextHop}

Returns the next hop of the given route.

*See also* [setNextHop](networkmanager-iproute.md#setNextHop)()

### void IpRoute::setMetric(quint32 *metric*) {#setMetric}

Defines the `metric` of the given route, lower values have higher priority.

*See also* [metric](networkmanager-iproute.md#metric)()

### void IpRoute::setNextHop(const QHostAddress &*nextHop*) const {#setNextHop}

Defines the next hop of the given route.

*See also* [nextHop](networkmanager-iproute.md#nextHop)()

### NetworkManager::IpRoute &IpRoute::operator=(const NetworkManager::IpRoute &*other*) {#operator-eq}

Makes a copy of the [IpRoute](networkmanager-iproute.md) object `other`.
