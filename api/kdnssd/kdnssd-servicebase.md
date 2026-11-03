---
title: "KDNSSD::ServiceBase Class"
description: "Describes a service."
---

# KDNSSD::ServiceBase Class

Describes a service. [More...](#details)

- **Header:** `#include <KDNSSD/ServiceBase>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS DNSSD)`  
  `target_link_libraries(mytarget PRIVATE KF6::DNSSD)`
- **Inherits:** [QSharedData](https://doc.qt.io/qt-6/qshareddata.html)
- **Inherited By:** [KDNSSD::PublicService](kdnssd-publicservice.md) and [KDNSSD::RemoteService](kdnssd-remoteservice.md)

[List of all members, including inherited members](kdnssd-servicebase-members.md)

## Public Functions

- [ServiceBase(const QString &name = QString(), const QString &type = QString(), const QString &domain = QString(), const QString &host = QString(), unsigned short port = 0)](#ServiceBase)
- [QString domain() const](#domain)
- [QString hostName() const](#hostName)
- [unsigned short port() const](#port)
- [QString serviceName() const](#serviceName)
- [QMap\<QString, QByteArray\> textData() const](#textData)
- [QString type() const](#type)
- [bool ServiceBase::operator!=(const KDNSSD::ServiceBase &o) const](#operator-not-eq)
- [bool ServiceBase::operator==(const KDNSSD::ServiceBase &o) const](#operator-eq-eq)

## Detailed Description {#details}

This class is used to describe a service. The service can be published by the current application (in which case it is probably a [PublicService](kdnssd-publicservice.md)) or by another application, either on the current machine or a remote machine, in which case it is probably a [RemoteService](kdnssd-remoteservice.md) returned by [ServiceBrowser](kdnssd-servicebrowser.md).

> **Note:** You should not normally need to create a [ServiceBase](kdnssd-servicebase.md) object yourself.

*See also* [PublicService](kdnssd-publicservice.md)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ServiceBase::ServiceBase(const QString &*name* = QString(), const QString &*type* = QString(), const QString &*domain* = QString(), const QString &*host* = QString(), unsigned short *port* = 0) {#ServiceBase}

Creates a [ServiceBase](kdnssd-servicebase.md) object

Note that `name`, `type` and `domain` uniquely identify the service in the DNS-SD system, and `host` and `port` provide the actual location of the service.

For example, [RemoteService](kdnssd-remoteservice.md) populates `host` and `port` based on the `name`, `type` and `domain` attributes using the DNS-SD resolution system.

`name` is the service name

`type` is the service type

`domain` is the DNS-SD domain name for service

`host` is the host name of the service (a fully-qualified domain name)

`port` is the port number of the service

### QString ServiceBase::domain() const {#domain}

Returns the domain that the service belongs to.

It is "local." for link-local services.

### QString ServiceBase::hostName() const {#hostName}

Returns the hostname of the service.

Only valid for local and resolved remote services.

Together with [port](kdnssd-servicebase.md#port)(), this can be used to actually access the service.

*See also* [RemoteService::resolve](kdnssd-remoteservice.md#resolve)(), [RemoteService::resolveAsync](kdnssd-remoteservice.md#resolveAsync)()

### unsigned short ServiceBase::port() const {#port}

Returns the port number of the service.

Only valid for local and resolved remote services.

Together with [hostName](kdnssd-servicebase.md#hostName)(), this can be used to actually access the service.

*See also* [RemoteService::resolve](kdnssd-remoteservice.md#resolve)(), [RemoteService::resolveAsync](kdnssd-remoteservice.md#resolveAsync)()

### QString ServiceBase::serviceName() const {#serviceName}

Returns the name of the service.

### QMap\<QString, QByteArray\> ServiceBase::textData() const {#textData}

Returns additional text data associated with the service.

Only valid for local and resolved remote services.

This is data that provides additional information about the service. For example, it might be used to specify a printer queue on the printer server specified by [hostName](kdnssd-servicebase.md#hostName)() and [port](kdnssd-servicebase.md#port)().

You can check for the data that might be associated with a particular service on the [service types list](http://www.dns-sd.org/ServiceTypes.html). If a `key=value` pair is given, this will appear with the `value` in a [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) indexed by the `key`. If the data is on its own (does not have an `=` in it), it will be used to index an empty [QByteArray](https://doc.qt.io/qt-6/qbytearray.html), and can be checked for with [QMap::contains](https://doc.qt.io/qt-6/qmap.html#contains)().

For example, if you are accessing the \_ipp.\_tcp service, you might do something like:

```cpp
QString printerModel = "unknown";
if (service->textData().contains("ty")) {
    printQueue = QString::fromUtf8(service->textData()["ty"].constData());
}
```

since the TXT data of the IPP service may contain data like "ty=Apple LaserWriter Pro 630".

> **Note:** You actually have to be a bit more clever than this, since the key should usually be case insensitive.

### QString ServiceBase::type() const {#type}

Returns the type of the service.

This is always in the format `_sometype._udp` or `_sometype._tcp`.

See [http://www.dns-sd.org](http://www.dns-sd.org) for [a full list of service types](http://www.dns-sd.org/ServiceTypes.html).

### bool ServiceBase::operator!=(const KDNSSD::ServiceBase &*o*) const {#operator-not-eq}

Compares services based on name, type and domain.

This is enough to for unique identification and omitting port, host and text data allows to compare resolved and unresolved services

`o` is the service to compare this service to

Returns `false` if this service represents the same service (from the point of view of DNS-SD) as `o`, `true` otherwise

### bool ServiceBase::operator==(const KDNSSD::ServiceBase &*o*) const {#operator-eq-eq}

Compares services based on name, type and domain.

This is enough to for unique identification and omitting port, host and text data allows to compare resolved and unresolved services

`o` is the service to compare this service to

Returns `true` if this service represents the same service (from the point of view of DNS-SD) as `o`, `false` otherwise

## Related Non-Members {#related-non-members}

### bool domainIsLocal(const QString &*domain*) {#domainIsLocal}

Check if the `domain` is link-local.

Returns `true` if domain is link-local ('local.'), `false` otherwise
