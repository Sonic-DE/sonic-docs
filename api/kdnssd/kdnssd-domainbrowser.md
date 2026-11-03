---
title: "KDNSSD::DomainBrowser Class"
description: "Browses recommended domains for browsing or publishing to."
---

# KDNSSD::DomainBrowser Class

Browses recommended domains for browsing or publishing to. [More...](#details)

- **Header:** `#include <KDNSSD/DomainBrowser>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS DNSSD)`  
  `target_link_libraries(mytarget PRIVATE KF6::DNSSD)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kdnssd-domainbrowser-members.md)

## Public Types

- [enum DomainBrowser::DomainType](#DomainType-enum)

## Public Functions

- [DomainBrowser(KDNSSD::DomainBrowser::DomainType type, QObject \*parent = nullptr)](#DomainBrowser)
- [QStringList domains() const](#domains)
- [bool isRunning() const](#isRunning)
- [void startBrowse()](#startBrowse)

## Signals

- [void domainAdded(const QString &domain)](#domainAdded)
- [void domainRemoved(const QString &domain)](#domainRemoved)

## Detailed Description {#details}

Usage of this class is very simple. If you are interested in browsing for services, simple do:

```cpp
KDNSSD::DomainBrowser *browser =
    new KDNSSD::DomainBrowser(KDNSSD::DomainBrowser::Browsing, this);
connect(browser, SIGNAL(domainAdded(QString)),
        this, SLOT(browsingDomainAdded(QString));
connect(browser, SIGNAL(domainRemoved(QString)),
        this, SLOT(browsingDomainRemove(QString));
browser->startBrowse();
```

If you are interested in domains where you can register services, usage is identical except that you should pass [KDNSSD::DomainBrowser::Publishing](kdnssd-domainbrowser.md#DomainType-enum) to the constructor.

## Member Type Documentation {#member-type-documentation}

### enum DomainBrowser::DomainType {#DomainType-enum}

A type of domain recommendation.

| Constant | Value | Description |
| --- | --- | --- |
| `KDNSSD::DomainBrowser::Browsing` | `0` | Domains recommended for browsing for services on (using [ServiceBrowser](kdnssd-servicebrowser.md)). |
| `KDNSSD::DomainBrowser::Publishing` | `1` | Domains recommended for publishing to (using [PublicService](kdnssd-publicservice.md)). |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] DomainBrowser::DomainBrowser(KDNSSD::DomainBrowser::DomainType *type*, QObject \**parent* = nullptr) {#DomainBrowser}

Standard constructor

The global DNS-SD configuration (for example, the global Avahi configuration for the Avahi backend) will be used.

`type` is the type of domain to search for

`parent` is the parent object (see [QObject](https://doc.qt.io/qt-6/qobject.html) documentation)

*See also* [startBrowse](kdnssd-domainbrowser.md#startBrowse)(), [ServiceBrowser::isAvailable](kdnssd-servicebrowser.md#isAvailable)()

### \[signal\] void DomainBrowser::domainAdded(const QString &*domain*) {#domainAdded}

A new domain has been discovered.

If the requested [DomainType](kdnssd-domainbrowser.md#DomainType-enum) is Browsing, this will also be emitted for the domains specified in the global configuration.

`domain` is the name of the domain

*See also* [domainRemoved](kdnssd-domainbrowser.md#domainRemoved)()

### \[signal\] void DomainBrowser::domainRemoved(const QString &*domain*) {#domainRemoved}

A domain has disappeared from the browsed list.

Emitted when domain has been removed from browsing list or the publishing list (depending on which list was requested in the constructor).

`domain` is the name of the domain

*See also* [domainAdded](kdnssd-domainbrowser.md#domainAdded)()

### QStringList DomainBrowser::domains() const {#domains}

The current known list of domains of the requested [DomainType](kdnssd-domainbrowser.md#DomainType-enum).

Returns a list of currently known domain names

### bool DomainBrowser::isRunning() const {#isRunning}

Whether the browsing has been started.

Returns `true` if [startBrowse](kdnssd-domainbrowser.md#startBrowse)() has been called, `false` otherwise

### void DomainBrowser::startBrowse() {#startBrowse}

Starts browsing.

> **Note:** Only the first call to this function will have any effect.

Browsing stops when the [DomainBrowser](kdnssd-domainbrowser.md) object is destroyed.

> **Warning:** The [domainAdded](kdnssd-domainbrowser.md#domainAdded)() signal may be emitted before this function returns.

*See also* [domainAdded](kdnssd-domainbrowser.md#domainAdded)(), [domainRemoved](kdnssd-domainbrowser.md#domainRemoved)()
