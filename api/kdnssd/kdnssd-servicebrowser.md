---
title: "KDNSSD::ServiceBrowser Class"
description: "Browses for network services advertised over DNS-SD."
---

# KDNSSD::ServiceBrowser Class

Browses for network services advertised over DNS-SD. [More...](#details)

- **Header:** `#include <KDNSSD/ServiceBrowser>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS DNSSD)`  
  `target_link_libraries(mytarget PRIVATE KF6::DNSSD)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kdnssd-servicebrowser-members.md)

## Public Types

- [enum ServiceBrowser::State](#State-enum)

## Public Functions

- [ServiceBrowser(const QString &type, bool autoResolve = false, const QString &domain = QString(), const QString &subtype = QString())](#ServiceBrowser)
- [bool isAutoResolving() const](#isAutoResolving)
- [QList\<RemoteService::Ptr\> services() const](#services)
- [void startBrowse()](#startBrowse)

## Signals

- [void finished()](#finished)
- [void serviceAdded(KDNSSD::RemoteService::Ptr service)](#serviceAdded)
- [void serviceRemoved(KDNSSD::RemoteService::Ptr service)](#serviceRemoved)

## Static Public Members

- [QString getLocalHostName()](#getLocalHostName)
- [KDNSSD::ServiceBrowser::State isAvailable()](#isAvailable)
- [QHostAddress resolveHostName(const QString &hostname)](#resolveHostName)

## Detailed Description {#details}

This is the central class in the KDNSSD library for applications that want to discover services on network.

Suppose that you need list of web servers running. Then you might do something like:

```cpp
KDNSSD::ServiceBrowser *browser = new KDNSSD::ServiceBrowser(QStringLiteral("_http._tcp"));
connect(browser, &KDNSSD::ServiceBrowser::serviceAdded,
        this, [](KDNSSD::RemoteService::Ptr service) {
        });
connect(browser, &KDNSSD::ServiceBrowser::serviceRemoved,
        this, [](KDNSSD::RemoteService::Ptr service) {
        });
browser->startBrowse();
```

In above example addService() will be called for every web server already running and for every web service that subsequently appears on the network and delService() will be called when a server previously advertised is stopped.

Because no domain was passed to constructor, the default domain will be searched. To find other domains to browse for services on, use [DomainBrowser](kdnssd-domainbrowser.md).

## Member Type Documentation {#member-type-documentation}

### enum ServiceBrowser::State {#State-enum}

Availability of DNS-SD services.

| Constant | Value | Description |
| --- | --- | --- |
| `KDNSSD::ServiceBrowser::Working` | `0` | The DNS-SD services are available. |
| `KDNSSD::ServiceBrowser::Stopped` | `1` | Not available because mDnsd or Avahi daemon is not running. |
| `KDNSSD::ServiceBrowser::Unsupported` | `2` | Not available because KDE was compiled without DNS-SD support. |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ServiceBrowser::ServiceBrowser(const QString &*type*, bool *autoResolve* = false, const QString &*domain* = QString(), const QString &*subtype* = QString()) {#ServiceBrowser}

Creates a [ServiceBrowser](kdnssd-servicebrowser.md) for a particular service type.

[DomainBrowser](kdnssd-domainbrowser.md) can be used to find other domains to browse on. If no domain is given, the default domain is used.

The service type is the high-level protocol type, followed by a dot, followed by the transport protocol type (`_tcp` or `_udp`). The [DNS-SD website](http://www.dns-sd.org) maintains [a full list](http://www.dns-sd.org/ServiceTypes.html) of service types.

The `subtype` parameter allows you to do more fine-grained filtering on the services you are interested in. So you might request only FTP servers that allow anonymous access by passing `"_ftp._tcp"` as the `type` and `"_anon"` as the `subtype`. Subtypes are particularly important for types like `_soap` and `_upnp`, which are far too generic for most applications. In these cases, the subtype can be used to specify the particular SOAP or UPnP protocol they want.

> **Warning:** Enabling `autoResolve` will increase network usage by resolving all services, so this feature should be used only when necessary.

`type` is the service type to browse for (example: "\_http.\_tcp")

`autoResolve` if true, discovered services will be resolved before being reported with the [serviceAdded](kdnssd-servicebrowser.md#serviceAdded)() signal

`domain` is the domain to search on instead of the default one

`subtype` if not an empty string, only browse for a specific subtype

*See also* [startBrowse](kdnssd-servicebrowser.md#startBrowse)(), [isAvailable](kdnssd-servicebrowser.md#isAvailable)()

### \[signal\] void ServiceBrowser::finished() {#finished}

Emitted when the list of published services has settled.

> **Note:** This signal is emitted once after [startBrowse](kdnssd-servicebrowser.md#startBrowse)() is called when all the services of the requested type that are currently published have been reported (even if none are available or the DNS-SD service is not available). It is emitted again when a new batch of services become available or disappear.

For example, if a new host is connected to network and announces some services watched for by this [ServiceBrowser](kdnssd-servicebrowser.md), they will be reported by one or more [serviceAdded](kdnssd-servicebrowser.md#serviceAdded)() signals and the whole batch will be concluded by finished().

This signal can be used by applications that just want to get a list of the currently available services (similar to a directory listing) and do not care about adding or removing services that appear or disappear later.

> **Warning:** There is no guarantee any [RemoteService](kdnssd-remoteservice.md) pointers received by [serviceAdded](kdnssd-servicebrowser.md#serviceAdded)() will be valid by the time this signal is emitted, so you should either do all your work involving them in the slot receiving the [serviceAdded](kdnssd-servicebrowser.md#serviceAdded)() signal, or you should listen to [serviceRemoved](kdnssd-servicebrowser.md#serviceRemoved)() as well.

*See also* [serviceAdded](kdnssd-servicebrowser.md#serviceAdded)(), [serviceRemoved](kdnssd-servicebrowser.md#serviceRemoved)()

### \[static\] QString ServiceBrowser::getLocalHostName() {#getLocalHostName}

The mDNS hostname of the local machine.

Usually this will return the same as QHostInfo::localHostName(), but it may be changed to something different in the Avahi configuration file (if using the Avahi backend).

Returns the hostname, or an empty string on failure

### bool ServiceBrowser::isAutoResolving() const {#isAutoResolving}

Whether discovered services are resolved before being reported.

Returns the value of the autoResolve parameter passed to the constructor.

### \[static\] KDNSSD::ServiceBrowser::State ServiceBrowser::isAvailable() {#isAvailable}

Checks availability of DNS-SD services.

> **Note:** Although this method is part of [ServiceBrowser](kdnssd-servicebrowser.md), none of the classes in this library will be able to perform their intended function if this method does not return [Working](kdnssd-servicebrowser.md#State-enum).

If this method does not return [Working](kdnssd-servicebrowser.md#State-enum), it is still safe to call any of the methods in this library. However, no services will be found or published and no domains will be found.

If you use this function to report an error to the user, below is a suggestion on how to word the errors when publishing a service. The first line of each error message can also be used for reporting errors when browsing for services.

```cpp
switch(KDNSSD::ServiceBrowser::isAvailable()) {
case KDNSSD::ServiceBrowser::Working:
    return "";
case KDNSSD::ServiceBrowser::Stopped:
    return i18n("<p>The Zeroconf daemon is not running. See the Service"
                " Discovery Handbook for more information.<br/>"
                "Other users will not see the services provided by this
                " system when browsing the network via zeroconf, but "
                " normal access will still work.</p>");
case KDNSSD::ServiceBrowser::Unsupported:
    return i18n("<p>Zeroconf support is not available in this version of KDE."
                " See the Service Discovery Handbook for more information.<br/>"
                "Other users will not see the services provided by this
                " application when browsing the network via zeroconf, but "
                " normal access will still work.</p>");
default:
    return i18n("<p>Unknown error with Zeroconf.<br/>"
                "Other users will not see the services provided by this
                " application when browsing the network via zeroconf, but "
                " normal access will still work.</p>");
}
```

Returns the mDNS-SD service state.

### \[static\] QHostAddress ServiceBrowser::resolveHostName(const QString &*hostname*) {#resolveHostName}

Resolves an mDNS hostname into an IP address.

> **Note:** This function is very rarely useful, since a properly configured system is able to resolve an mDNS-based host name using the system resolver (ie: you can just pass the mDNS hostname to KIO or other library).

`hostname` the hostname to be resolved

Returns a QHostAddress containing the IP address, or QHostAddress() if resolution failed

### \[signal\] void ServiceBrowser::serviceAdded(KDNSSD::RemoteService::Ptr *service*) {#serviceAdded}

Emitted when new service is discovered.

If [isAutoResolving](kdnssd-servicebrowser.md#isAutoResolving)() returns `true`, this will not be emitted until the service has been resolved.

`service` is a [RemoteService](kdnssd-remoteservice.md) object describing the service

*See also* [serviceRemoved](kdnssd-servicebrowser.md#serviceRemoved)(), [finished](kdnssd-servicebrowser.md#finished)()

### \[signal\] void ServiceBrowser::serviceRemoved(KDNSSD::RemoteService::Ptr *service*) {#serviceRemoved}

Emitted when a service is no longer published over DNS-SD.

The [RemoteService](kdnssd-remoteservice.md) object is removed from the [services](kdnssd-servicebrowser.md#services)() list and deleted immediately after this signal returns.

> **Warning:** Do **not** use a delayed connection with this signal.

`service` a [RemoteService](kdnssd-remoteservice.md) object describing the service

*See also* [serviceAdded](kdnssd-servicebrowser.md#serviceAdded)(), [finished](kdnssd-servicebrowser.md#finished)()

### QList\<RemoteService::Ptr\> ServiceBrowser::services() const {#services}

The currently known services of the specified type.

Returns a list of [RemoteService](kdnssd-remoteservice.md) pointers

*See also* [serviceAdded](kdnssd-servicebrowser.md#serviceAdded)(), [serviceRemoved](kdnssd-servicebrowser.md#serviceRemoved)()

### \[virtual\] void ServiceBrowser::startBrowse() {#startBrowse}

Starts browsing for services.

> **Note:** Only the first call to this function will have any effect.

Browsing stops when the [ServiceBrowser](kdnssd-servicebrowser.md) object is destroyed.

> **Warning:** The [serviceAdded](kdnssd-servicebrowser.md#serviceAdded)() signal may be emitted before this function returns.

*See also* [serviceAdded](kdnssd-servicebrowser.md#serviceAdded)(), [serviceRemoved](kdnssd-servicebrowser.md#serviceRemoved)(), [finished](kdnssd-servicebrowser.md#finished)()
