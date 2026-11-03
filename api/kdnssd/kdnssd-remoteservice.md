---
title: "KDNSSD::RemoteService Class"
description: "Describes a service published over DNS-SD, typically on a remote machine."
---

# KDNSSD::RemoteService Class

Describes a service published over DNS-SD, typically on a remote machine. [More...](#details)

- **Header:** `#include <KDNSSD/RemoteService>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS DNSSD)`  
  `target_link_libraries(mytarget PRIVATE KF6::DNSSD)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html) and [KDNSSD::ServiceBase](kdnssd-servicebase.md)

[List of all members, including inherited members](kdnssd-remoteservice-members.md)

## Public Functions

- [RemoteService(const QString &name, const QString &type, const QString &domain)](#RemoteService)
- [bool isResolved() const](#isResolved)
- [bool resolve()](#resolve)
- [void resolveAsync()](#resolveAsync)

## Signals

- [void resolved(bool successful)](#resolved)

## Detailed Description {#details}

This class allows delayed or asynchronous resolution of services. As the name suggests, the service is normally on a remote machine, but the service could just as easily be published on the local machine.

[RemoteService](kdnssd-remoteservice.md) instances are normally provided by [ServiceBrowser](kdnssd-servicebrowser.md), but can be used to resolve any service if you know the name, type and domain for it.

*See also* [ServiceBrowser](kdnssd-servicebrowser.md)

## Member Function Documentation {#member-function-documentation}

### RemoteService::RemoteService(const QString &*name*, const QString &*type*, const QString &*domain*) {#RemoteService}

Creates an unresolved [RemoteService](kdnssd-remoteservice.md) representing the service with the given name, type and domain.

`name` is the name of the service

`type` is the type of the service (see [ServiceBrowser::ServiceBrowser](kdnssd-servicebrowser.md#ServiceBrowser)())

`domain` is the domain of the service

*See also* [ServiceBrowser::isAvailable](kdnssd-servicebrowser.md#isAvailable)()

### bool RemoteService::isResolved() const {#isResolved}

Whether the service has been successfully resolved.

Returns `true` if [hostName](kdnssd-servicebase.md#hostName)() and [port](kdnssd-servicebase.md#port)() will return valid values, `false` otherwise

### bool RemoteService::resolve() {#resolve}

Resolves the host name and port of service synchronously.

The host name is not resolved into an IP address - use KResolver for that.

> **Note:** [resolved](kdnssd-remoteservice.md#resolved)() is emitted before this function is returned.

resolve() will not cause [RemoteService](kdnssd-remoteservice.md) to monitor for changes in the hostname or port of the service.

Returns `true` if successful, `false` on failure

*See also* [resolveAsync](kdnssd-remoteservice.md#resolveAsync)(), [hostName](kdnssd-servicebase.md#hostName)(), [port](kdnssd-servicebase.md#port)()

### void RemoteService::resolveAsync() {#resolveAsync}

Resolves the host name and port of service asynchronously.

> **Note:** The host name is not resolved into an IP address - use KResolver for that.

The [resolved](kdnssd-remoteservice.md#resolved)() signal will be emitted when the resolution is complete, or when it fails.

> **Note:** [resolved](kdnssd-remoteservice.md#resolved)() may be emitted before this function returns in case of immediate failure.

[RemoteService](kdnssd-remoteservice.md) will keep monitoring the service for changes in hostname and port, and re-emit [resolved](kdnssd-remoteservice.md#resolved)() when either changes.

*See also* [resolve](kdnssd-remoteservice.md#resolve)(), [hostName](kdnssd-servicebase.md#hostName)(), [port](kdnssd-servicebase.md#port)()

### \[signal\] void RemoteService::resolved(bool *successful*) {#resolved}

Emitted when resolving is complete

If operating in asynchronous mode this signal can be emitted several times (when the hostName or port of the service changes).

`successful` is `true` if the hostName and port were successfully resolved, `false` otherwise
