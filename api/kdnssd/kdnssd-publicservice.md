---
title: "KDNSSD::PublicService Class"
description: "Represents a service to be published."
---

# KDNSSD::PublicService Class

Represents a service to be published. [More...](#details)

- **Header:** `#include <KDNSSD/PublicService>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS DNSSD)`  
  `target_link_libraries(mytarget PRIVATE KF6::DNSSD)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html) and [KDNSSD::ServiceBase](kdnssd-servicebase.md)

[List of all members, including inherited members](kdnssd-publicservice-members.md)

## Public Functions

- [PublicService(const QString &name = QString(), const QString &type = QString(), unsigned int port = 0, const QString &domain = QString(), const QStringList &subtypes = QStringList())](#PublicService)
- [bool isPublished() const](#isPublished)
- [bool publish()](#publish)
- [void publishAsync()](#publishAsync)
- [void setDomain(const QString &domain)](#setDomain)
- [void setPort(unsigned short port)](#setPort)
- [void setServiceName(const QString &serviceName)](#setServiceName)
- [void setSubTypes(const QStringList &subtypes)](#setSubTypes)
- [void setTextData(const QMap\<QString, QByteArray\> &textData)](#setTextData)
- [void setType(const QString &type)](#setType)
- [void stop()](#stop)
- [QStringList subtypes() const](#subtypes)

## Signals

- [void published(bool successful)](#published)

## Detailed Description {#details}

This class allows you to publish the existence of a network service provided by your application.

If you are providing a web server and want to advertise it on the local network, you might do

```cpp
KDNSSD::PublicService *service = new KDNSSD::PublicService("My files", "_http._tcp", 80);
bool isOK = service->publish();
```

In this example [publish](kdnssd-publicservice.md#publish)() is synchronous: it will not return until publishing is complete. This is usually not too long but it can freeze an application's GUI for a moment. To publish asynchronously instead, do:

```cpp
KDNSSD::PublicService *service = new KDNSSD::PublicService("My files", "_http._tcp", 80);
connect(service, SIGNAL(published(bool)), this, SLOT(wasPublished(bool)));
service->publishAsync();
```

## Member Function Documentation {#member-function-documentation}

### \[explicit\] PublicService::PublicService(const QString &*name* = QString(), const QString &*type* = QString(), unsigned int *port* = 0, const QString &*domain* = QString(), const QStringList &*subtypes* = QStringList()) {#PublicService}

Creates a service description that can be published.

If no `name` is given, the computer name is used instead. If there is already a service with the same name, type and domain a number will be appended to the name to make it unique.

If no `domain` is specified, the service is published on the link-local domain (.local).

The subtypes can be used to specify server attributes, such as "\_anon" for anonymous FTP servers, or can specify a specific protocol (such as a web service interface) on top of a generic protocol like SOAP.

There is [a comprehensive list](http://www.dns-sd.org/ServiceTypes.html) of possible types available, but you are largely on your own for subtypes.

`name` is a service name to use instead of the computer name

`type` is the service type, in the form `_sometype._udp` or `_sometype._tcp`

`port` is the port number, or 0 to "reserve" the service name

`domain` is the domain to publish the service on (see [DomainBrowser](kdnssd-domainbrowser.md))

`subtypes` is an optional list of subtypes, each with a leading underscore

*See also* [ServiceBrowser::ServiceBrowser](kdnssd-servicebrowser.md#ServiceBrowser)()

### bool PublicService::isPublished() const {#isPublished}

Whether the service is currently published.

Returns `true` if the service is being published to the domain, `false` otherwise

### bool PublicService::publish() {#publish}

Publish the service synchronously.

The method will not return (and hence the application interface will freeze, since KDElibs code should be executed in the main thread) until either the service is published or publishing fails.

[published](kdnssd-publicservice.md#published)() is emitted before this method returns.

Returns `true` if the service was successfully published, `false` otherwise

### void PublicService::publishAsync() {#publishAsync}

Publish the service asynchronously

Returns immediately and emits [published](kdnssd-publicservice.md#published)() when completed.

> **Note:** [published](kdnssd-publicservice.md#published)() may be emitted before this method returns when an error is detected immediately.

### \[signal\] void PublicService::published(bool *successful*) {#published}

Emitted when publishing is complete.

`successful` is true of the service was successfully published

It will also emitted when an already-published service is republished after a property of the service (such as the name or port) is changed.

### void PublicService::setDomain(const QString &*domain*) {#setDomain}

Sets the domain where the service is published.

"local." means link-local, ie: the IP subnet on the LAN containing this computer.

If service is already published, it will be removed from the current domain and published on `domain` instead.

`domain` is the new domain to publish the service on

### void PublicService::setPort(unsigned short *port*) {#setPort}

Sets the port the service is published on.

If the service is already published, it will be re-announced with the new port.

`port` is the port of the service, or 0 to simply "reserve" the name

### void PublicService::setServiceName(const QString &*serviceName*) {#setServiceName}

Sets the name of the service.

If the service is already published, it will be re-announced with the new name.

`serviceName` the new name of the service

### void PublicService::setSubTypes(const QStringList &*subtypes*) {#setSubTypes}

Sets the subtypes of the service.

If the service is already published, it will be re-announced with the new subtypes.

The existing list of substypes is replaced, so an empty list will cause all existing subtypes to be removed.

`subtypes` is the new list of subtypes

### void PublicService::setTextData(const QMap\<QString, QByteArray\> &*textData*) {#setTextData}

Sets new text properties.

If the service is already published, it will be re-announced with the new data.

`textData` is the new text properties for the service

*See also* [ServiceBase::textData](kdnssd-servicebase.md#textData)()

### void PublicService::setType(const QString &*type*) {#setType}

Sets the service type.

If the service is already published, it will be re-announced with the new type.

`type` is the new type of the service

See [PublicService](kdnssd-publicservice.md#PublicService)() for details on the format of `type`

### void PublicService::stop() {#stop}

Stops publishing or aborts an incomplete publish request.

Useful when you want to disable the service for some time.

> **Note:** If you stop providing a service (without exiting the application), you should stop publishing it.

### QStringList PublicService::subtypes() const {#subtypes}

Returns the subtypes of this service.

*See also* [setSubTypes](kdnssd-publicservice.md#setSubTypes)()
