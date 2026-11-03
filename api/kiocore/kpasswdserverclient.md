---
title: "KPasswdServerClient Class"
description: "Interface class for kpasswdserver."
---

# KPasswdServerClient Class

Interface class for kpasswdserver. [More...](#details)

- **Header:** `#include <KPasswdServerClient>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`

[List of all members, including inherited members](kpasswdserverclient-members.md)

## Public Functions

- [KPasswdServerClient()](#KPasswdServerClient)
- [void addAuthInfo(const KIO::AuthInfo &info, qlonglong windowId)](#addAuthInfo)
- [bool checkAuthInfo(KIO::AuthInfo \*info, qlonglong windowId, qlonglong usertime)](#checkAuthInfo)
- [int queryAuthInfo(KIO::AuthInfo \*info, const QString &errorMsg, qlonglong windowId, qlonglong usertime)](#queryAuthInfo)
- [void removeAuthInfo(const QString &host, const QString &protocol, const QString &user)](#removeAuthInfo)

## Detailed Description {#details}

KIO workers should not use this directly but via the WorkerBase API.

## Member Function Documentation {#member-function-documentation}

### KPasswdServerClient::KPasswdServerClient() {#KPasswdServerClient}

Creates a client instance for kpasswdserver. The instance should be kept for the lifetime of the process, not created for each request.

### void KPasswdServerClient::addAuthInfo(const KIO::AuthInfo &*info*, qlonglong *windowId*) {#addAuthInfo}

Manually add authentication information to kpasswdserver's cache.

`info` information to add

`windowId` used as parent window for dialogs, comes from QWidget::winId() on the toplevel widget

### bool KPasswdServerClient::checkAuthInfo(KIO::AuthInfo \**info*, qlonglong *windowId*, qlonglong *usertime*) {#checkAuthInfo}

Check if kpasswdserver has cached authentication information regarding an AuthInfo object.

`info` information to check cache for

`windowId` used as parent for dialogs, comes from QWidget::winId() on the toplevel widget

`usertime` the X11 user time from the calling application, so that any dialog (e.g. wallet password) respects focus-prevention rules. Use KUserTimestamp::userTimestamp in the GUI application from which the request originates.

Returns `true` if kpasswdserver provided cached information, false if not

Info will contain the results of the check. To see if information was retrieved, check info.isModified().

### int KPasswdServerClient::queryAuthInfo(KIO::AuthInfo \**info*, const QString &*errorMsg*, qlonglong *windowId*, qlonglong *usertime*) {#queryAuthInfo}

Let kpasswdserver ask the user for authentication information.

`info` information to query the user for

`errorMsg` error message that will be displayed to the user

`windowId` used as parent for dialogs, comes from QWidget::winId() on the toplevel widget

`usertime` the X11 user time from the calling application, so that the dialog (e.g. wallet password) respects focus-prevention rules. Use KUserTimestamp::userTimestamp in the GUI application from which the request originates.

Returns a KIO error code: [KJob::NoError](../kcoreaddons/kjob.md#anonymous-kjob-h-307-enum) (0) on success, otherwise ERR\_USER\_CANCELED if the user canceled, or ERR\_PASSWD\_SERVER if we couldn't communicate with kpasswdserver.

If [NoError](https://doc.qt.io/qt-6/qdtls.html#QDtlsError-enum) is returned, then `info` will contain the authentication information that was retrieved.

### void KPasswdServerClient::removeAuthInfo(const QString &*host*, const QString &*protocol*, const QString &*user*) {#removeAuthInfo}

Manually remove authentication information from kpasswdserver's cache.

`host` hostname of the information to remove

`protocol` protocol to remove information for

`user` username to remove information for
