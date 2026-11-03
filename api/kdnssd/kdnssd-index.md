---
title: "KDNSSD"
description: "Interface to system-level multicast DNS service discovery.."
---

# KDNSSD

Interface to system-level multicast DNS service discovery..

Network service discovery using Zeroconf

## Introduction {#introduction}

KDNSSD is a library for handling the DNS-based Service Discovery Protocol (DNS-SD), the layer of [Zeroconf](http://www.zeroconf.org) that allows network services, such as printers, to be discovered without any user intervention or centralized infrastructure.

##  {#more-information}

If you are writing an application that wants to discover services on the network, use [KDNSSD::ServiceBrowser](kdnssd-servicebrowser.md). You can also find available service types using ServiceTypeBrowser.

If you want to announce the availability of a service provided by your application, use [KDNSSD::PublicService](kdnssd-publicservice.md).

[KDNSSD::DomainBrowser](kdnssd-domainbrowser.md) allows you to find domains (other than the local one) recommended for browsing or publishing to.

Note that KDNSSD::ServiceBrowser::isAvailable() provides information about the availability of the services provided by this library generally, not just for browsing services.

## More information {#more-information-2}

More information about DNS-SD can be found in the online documentation for Apple's implementation of Zeroconf, [Bonjour](https://developer.apple.com/bonjour/).

## Using the Module {#using-the-module}

Using a Qt module's C++ API requires linking against the module library, either directly or through other dependencies. Several build tools have dedicated support for this, including CMake and [qmake](https://doc.qt.io/qt-6/resources.html#qmake).

### Building with CMake {#building-with-cmake}

Use the `find_package()` command to locate the needed module component in the `Qt6` package:

```cpp
find_package(Qt6 REQUIRED COMPONENTS KF6)
target_link_libraries(mytarget PRIVATE Qt6::KF6)
```

For more details, see the Build with CMake overview.

## API Reference {#api-reference}

- [KDNSSD C++ Classes](kdnssd-module.md)
