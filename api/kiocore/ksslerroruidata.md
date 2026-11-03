---
title: "KSslErrorUiData Class"
description: "Network transparent access to files and data."
---

# KSslErrorUiData Class

Network transparent access to files and data. [More...](#details)

- **Header:** `#include <KSslErrorUiData>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`

[List of all members, including inherited members](ksslerroruidata-members.md)

## Public Functions

- [KSslErrorUiData()](#KSslErrorUiData)
- [KSslErrorUiData(const QSslSocket \*socket)](#KSslErrorUiData-1)
- [KSslErrorUiData(const QNetworkReply \*reply, const QList\<QSslError\> &sslErrors)](#KSslErrorUiData-2)

## Detailed Description {#details}

This class can hold all the necessary data from a [QSslSocket](https://doc.qt.io/qt-6/qsslsocket.html) or [QNetworkReply](https://doc.qt.io/qt-6/qnetworkreply.html) to ask the user to continue connecting in the face of SSL errors. It can be used to carry the data for the UI over time or over thread boundaries.

*See also* [KIO::SslUi::askIgnoreSslErrors](../kiowidgets/kio-sslui.md#askIgnoreSslErrors)()

## Member Function Documentation {#member-function-documentation}

### KSslErrorUiData::KSslErrorUiData() {#KSslErrorUiData}

Default construct an instance with no useful data.

### KSslErrorUiData::KSslErrorUiData(const QSslSocket \**socket*) {#KSslErrorUiData-1}

Create an instance and initialize it with SSL error data from `socket`.

### KSslErrorUiData::KSslErrorUiData(const QNetworkReply \**reply*, const QList\<QSslError\> &*sslErrors*) {#KSslErrorUiData-2}

Create an instance and initialize it with SSL error data from `reply`.
