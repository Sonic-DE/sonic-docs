---
title: "KDNSSD Namespace"
description: "Interfaces to system mDNS service discovery."
---

# KDNSSD Namespace

Interfaces to system mDNS service discovery. [More...](#details)

- **Header:** `#include <KDNSSD>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS DNSSD)`  
  `target_link_libraries(mytarget PRIVATE KF6::DNSSD)`

## Detailed Description {#details}

## Classes {#classes}

### class [DomainBrowser](kdnssd-domainbrowser.md)

Browses recommended domains for browsing or publishing to.

### class [DomainModel](kdnssd-domainmodel.md)

Model for list of Zeroconf domains.

### class [PublicService](kdnssd-publicservice.md)

Represents a service to be published.

### class [RemoteService](kdnssd-remoteservice.md)

Describes a service published over DNS-SD, typically on a remote machine.

### class [ServiceBase](kdnssd-servicebase.md)

Describes a service.

### class [ServiceBrowser](kdnssd-servicebrowser.md)

Browses for network services advertised over DNS-SD.

### class [ServiceModel](kdnssd-servicemodel.md)

Model for list of Zeroconf services.

### class [ServiceTypeBrowser](kdnssd-servicetypebrowser.md)

Browses the service types being published on a domain.

## Function Documentation {#function-documentation}

### bool domainIsLocal(const QString &*domain*) {#domainIsLocal}

Check if the `domain` is link-local.

Returns `true` if domain is link-local ('local.'), `false` otherwise
