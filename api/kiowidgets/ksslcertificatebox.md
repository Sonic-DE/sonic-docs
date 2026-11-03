---
title: "KSslCertificateBox Class"
description: "productname."
---

# KSslCertificateBox Class

productname. [More...](#details)

- **Header:** `#include <KSslCertificateBox>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](ksslcertificatebox-members.md)

## Public Types

- [enum KSslCertificateBox::CertificateParty](#CertificateParty-enum)

## Public Functions

- [void clear()](#clear)
- [void setCertificate(const QSslCertificate &cert, KSslCertificateBox::CertificateParty party)](#setCertificate)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum KSslCertificateBox::CertificateParty {#CertificateParty-enum}

| Constant |   |
| --- | --- |
| `KSslCertificateBox::Subject` | `0` |
| `KSslCertificateBox::Issuer` | `1` |

## Member Function Documentation {#member-function-documentation}

### void KSslCertificateBox::clear() {#clear}

### void KSslCertificateBox::setCertificate(const QSslCertificate &*cert*, KSslCertificateBox::CertificateParty *party*) {#setCertificate}
