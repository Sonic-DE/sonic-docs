---
title: "KSslCertificateManager Class"
description: "Network transparent access to files and data."
---

# KSslCertificateManager Class

Network transparent access to files and data. [More...](#details)

- **Header:** `#include <KSslCertificateManager>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`

[List of all members, including inherited members](ksslcertificatemanager-members.md)

## Public Functions

- [QList\<QSslCertificate\> caCertificates() const](#caCertificates)
- [void clearRule(const KSslCertificateRule &rule)](#clearRule)
- [void clearRule(const QSslCertificate &cert, const QString &hostName)](#clearRule-1)
- [KSslCertificateRule rule(const QSslCertificate &cert, const QString &hostName) const](#rule)
- [void setRule(const KSslCertificateRule &rule)](#setRule)

## Static Public Members

- [QList\<QSslError\> nonIgnorableErrors(const QList\<QSslError\> &errors)](#nonIgnorableErrors)
- [KSslCertificateManager \*self()](#self)

## Detailed Description {#details}

Certificate manager.

## Member Function Documentation {#member-function-documentation}

### QList\<QSslCertificate\> KSslCertificateManager::caCertificates() const {#caCertificates}

### void KSslCertificateManager::clearRule(const KSslCertificateRule &*rule*) {#clearRule}

### void KSslCertificateManager::clearRule(const QSslCertificate &*cert*, const QString &*hostName*) {#clearRule-1}

### \[static\] QList\<QSslError\> KSslCertificateManager::nonIgnorableErrors(const QList\<QSslError\> &*errors*) {#nonIgnorableErrors}

Returns the subset of `errors` that cannot be ignored, ie. that is considered fatal.

### KSslCertificateRule KSslCertificateManager::rule(const QSslCertificate &*cert*, const QString &*hostName*) const {#rule}

*See also* [setRule](ksslcertificatemanager.md#setRule)()

### \[static\] KSslCertificateManager \*KSslCertificateManager::self() {#self}

### void KSslCertificateManager::setRule(const KSslCertificateRule &*rule*) {#setRule}

*See also* [rule](ksslcertificatemanager.md#rule)()
