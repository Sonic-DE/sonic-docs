---
title: "KSslCertificateRule Class"
description: "Network transparent access to files and data."
---

# KSslCertificateRule Class

Network transparent access to files and data. [More...](#details)

- **Header:** `#include <KSslCertificateManager>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`

[List of all members, including inherited members](ksslcertificaterule-members.md)

## Public Functions

- [KSslCertificateRule(const QSslCertificate &cert = QSslCertificate(), const QString &hostName = QString())](#KSslCertificateRule)
- [QSslCertificate certificate() const](#certificate)
- [QDateTime expiryDateTime() const](#expiryDateTime)
- [QList\<QSslError\> filterErrors(const QList\<QSslError\> &errors) const](#filterErrors)
- [QString hostName() const](#hostName)
- [bool isErrorIgnored(QSslError::SslError error) const](#isErrorIgnored)
- [bool isRejected() const](#isRejected)
- [void setExpiryDateTime(const QDateTime &dateTime)](#setExpiryDateTime)
- [void setIgnoredErrors(const QList\<QSslError::SslError\> &errors)](#setIgnoredErrors)
- [void setIgnoredErrors(const QList\<QSslError\> &errors)](#setIgnoredErrors-1)
- [void setRejected(bool rejected)](#setRejected)

## Detailed Description {#details}

Certificate rule.

## Member Function Documentation {#member-function-documentation}

### KSslCertificateRule::KSslCertificateRule(const QSslCertificate &*cert* = QSslCertificate(), const QString &*hostName* = QString()) {#KSslCertificateRule}

### QSslCertificate KSslCertificateRule::certificate() const {#certificate}

### QDateTime KSslCertificateRule::expiryDateTime() const {#expiryDateTime}

*See also* [setExpiryDateTime](ksslcertificaterule.md#setExpiryDateTime)()

### QList\<QSslError\> KSslCertificateRule::filterErrors(const QList\<QSslError\> &*errors*) const {#filterErrors}

Filter out errors that are already ignored.

### QString KSslCertificateRule::hostName() const {#hostName}

### bool KSslCertificateRule::isErrorIgnored(QSslError::SslError *error*) const {#isErrorIgnored}

Returns whether `error` is ignored for this certificate.

### bool KSslCertificateRule::isRejected() const {#isRejected}

### void KSslCertificateRule::setExpiryDateTime(const QDateTime &*dateTime*) {#setExpiryDateTime}

*See also* [expiryDateTime](ksslcertificaterule.md#expiryDateTime)()

### void KSslCertificateRule::setIgnoredErrors(const QList\<QSslError::SslError\> &*errors*) {#setIgnoredErrors}

Set the ignored errors for this certificate.

### void KSslCertificateRule::setIgnoredErrors(const QList\<QSslError\> &*errors*) {#setIgnoredErrors-1}

Set the ignored errors for this certificate.

### void KSslCertificateRule::setRejected(bool *rejected*) {#setRejected}

*See also* [isRejected](ksslcertificaterule.md#isRejected)()
