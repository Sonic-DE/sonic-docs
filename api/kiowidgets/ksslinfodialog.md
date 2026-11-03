---
title: "KSslInfoDialog Class"
description: "KDE SSL Information Dialog."
---

# KSslInfoDialog Class

KDE SSL Information Dialog. [More...](#details)

- **Header:** `#include <KSslInfoDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](ksslinfodialog-members.md)

## Public Functions

- [KSslInfoDialog(QWidget \*parent = nullptr)](#KSslInfoDialog)
- [void setAuxiliaryPartsEncrypted(bool)](#setAuxiliaryPartsEncrypted)
- [void setMainPartEncrypted(bool)](#setMainPartEncrypted)
- [void setSslInfo(const QList\<QSslCertificate\> &certificateChain, const QString &ip, const QString &host, const QString &sslProtocol, const QString &cipher, int usedBits, int bits, const QList\<QList\<QSslError::SslError\>\> &validationErrors)](#setSslInfo)

## Static Public Members

- [QList\<QList\<QSslError::SslError\>\> certificateErrorsFromString(const QString &errorsString)](#certificateErrorsFromString)

## Detailed Description {#details}

This class creates a dialog that can be used to display information about an SSL session.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KSslInfoDialog::KSslInfoDialog(QWidget \**parent* = nullptr) {#KSslInfoDialog}

Construct a KSSL Information Dialog

`parent` the parent widget

### \[static\] QList\<QList\<QSslError::SslError\>\> KSslInfoDialog::certificateErrorsFromString(const QString &*errorsString*) {#certificateErrorsFromString}

Converts certificate errors as provided in the "ssl\_cert\_errors" meta data to a list of QSslError::SslError values per certificate in the certificate chain.

### void KSslInfoDialog::setAuxiliaryPartsEncrypted(*bool*) {#setAuxiliaryPartsEncrypted}

### void KSslInfoDialog::setMainPartEncrypted(*bool*) {#setMainPartEncrypted}

### void KSslInfoDialog::setSslInfo(const QList\<QSslCertificate\> &*certificateChain*, const QString &*ip*, const QString &*host*, const QString &*sslProtocol*, const QString &*cipher*, int *usedBits*, int *bits*, const QList\<QList\<QSslError::SslError\>\> &*validationErrors*) {#setSslInfo}

Set information to display about the SSL connection.

`certificateChain` the certificate chain leading from the certificate authority to the peer.

`ip` the ip of the remote host

`host` the remote hostname

`sslProtocol` the version of SSL in use (SSLv2, SSLv3, TLSv1)

`cipher` the cipher in use

`usedBits` the used bits of the key

`bits` the key size of the cipher in use

`validationErrors` errors validating the certificates, if any
