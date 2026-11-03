---
title: "KDNSSD::ServiceTypeBrowser Class"
description: "Browses the service types being published on a domain."
---

# KDNSSD::ServiceTypeBrowser Class

Browses the service types being published on a domain. [More...](#details)

- **Header:** `#include <KDNSSD/ServiceTypeBrowser>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS DNSSD)`  
  `target_link_libraries(mytarget PRIVATE KF6::DNSSD)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kdnssd-servicetypebrowser-members.md)

## Public Functions

- [ServiceTypeBrowser(const QString &domain = QString(), QObject \*parent = nullptr)](#ServiceTypeBrowser)
- [QStringList serviceTypes() const](#serviceTypes)
- [void startBrowse()](#startBrowse)

## Signals

- [void finished()](#finished)
- [void serviceTypeAdded(const QString &type)](#serviceTypeAdded)
- [void serviceTypeRemoved(const QString &type)](#serviceTypeRemoved)

## Detailed Description {#details}

This class is mostly useful for generic utilities for browsing all the published service types on a local network. Applications that wish to find out about available services of a particular type (such as web servers) should use [ServiceBrowser](kdnssd-servicebrowser.md).

[ServiceTypeBrowser](kdnssd-servicetypebrowser.md) provides a list of all the service types published by at least one service on a given domain.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ServiceTypeBrowser::ServiceTypeBrowser(const QString &*domain* = QString(), QObject \**parent* = nullptr) {#ServiceTypeBrowser}

Creates a [ServiceTypeBrowser](kdnssd-servicetypebrowser.md) for a domain.

The link-local domain (the LAN subnet for this computer) will be used if no `domain` is given. [DomainBrowser](kdnssd-domainbrowser.md) can be used to get a list of browsing domains.

Note that WAN domains may not support service type browsing.

`domain` is a browsing domain to search

`parent` is the parent object (see [QObject](https://doc.qt.io/qt-6/qobject.html) documentation)

*See also* [startBrowse](kdnssd-servicetypebrowser.md#startBrowse)(), [ServiceBrowser::isAvailable](kdnssd-servicebrowser.md#isAvailable)()

### \[signal\] void ServiceTypeBrowser::finished() {#finished}

Emitted when the list of published service types has settled.

> **Note:** This signal is emitted once after [startBrowse](kdnssd-servicetypebrowser.md#startBrowse)() is called when the types of all the services that are currently published have been reported (even if no services are available or the DNS-SD service is not available). It is emitted again when a new batch of service types become available or disappear.

For example, if a new host is connected to network and announces services of several new types, they will be reported by several [serviceTypeAdded](kdnssd-servicetypebrowser.md#serviceTypeAdded)() signals and the whole batch will be concluded by finished().

This signal can be used by applications that just want to get a list of the currently available service types (similar to a directory listing) and do not care about adding or removing service types that appear or disappear later.

*See also* [serviceTypeAdded](kdnssd-servicetypebrowser.md#serviceTypeAdded)(), [serviceTypeRemoved](kdnssd-servicetypebrowser.md#serviceTypeRemoved)()

### \[signal\] void ServiceTypeBrowser::serviceTypeAdded(const QString &*type*) {#serviceTypeAdded}

A new type of service has been found.

`type` is the service type

*See also* serviceTypeAdded(), [finished](kdnssd-servicetypebrowser.md#finished)()

### \[signal\] void ServiceTypeBrowser::serviceTypeRemoved(const QString &*type*) {#serviceTypeRemoved}

Emitted when there are no more services of this type.

> **Warning:** This signal is not reliable: it is possible that it will not be emitted even after last service of this type disappeared

`type` is the service type

*See also* [serviceTypeAdded](kdnssd-servicetypebrowser.md#serviceTypeAdded)(), [finished](kdnssd-servicetypebrowser.md#finished)()

### QStringList ServiceTypeBrowser::serviceTypes() const {#serviceTypes}

All the service types currently being published.

Returns a list of service types, in the form `_type._tcp` or `_type._udp`

### void ServiceTypeBrowser::startBrowse() {#startBrowse}

Starts browsing for published services.

> **Note:** Only the first call to this function will have any effect.

Browsing stops when the [ServiceTypeBrowser](kdnssd-servicetypebrowser.md) object is destroyed.

> **Warning:** The [serviceTypeAdded](kdnssd-servicetypebrowser.md#serviceTypeAdded)() signal may be emitted before this function returns.

*See also* [serviceTypeAdded](kdnssd-servicetypebrowser.md#serviceTypeAdded)(), [serviceTypeRemoved](kdnssd-servicetypebrowser.md#serviceTypeRemoved)(), [finished](kdnssd-servicetypebrowser.md#finished)()
