---
title: "BluezQt::ObexFileTransfer Class"
description: "OBEX file transfer."
---

# BluezQt::ObexFileTransfer Class

OBEX file transfer. [More...](#details)

- **Header:** `#include <BluezQt/ObexFileTransfer>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-obexfiletransfer-members.md)

## Public Functions

- [ObexFileTransfer(const QDBusObjectPath &path, QObject \*parent = nullptr)](#ObexFileTransfer)
- [BluezQt::PendingCall \*changeFolder(const QString &folder)](#changeFolder)
- [BluezQt::PendingCall \*copyFile(const QString &sourceFileName, const QString &targetFileName)](#copyFile)
- [BluezQt::PendingCall \*createFolder(const QString &folder)](#createFolder)
- [BluezQt::PendingCall \*deleteFile(const QString &fileName)](#deleteFile)
- [BluezQt::PendingCall \*getFile(const QString &targetFileName, const QString &sourceFileName)](#getFile)
- [BluezQt::PendingCall \*listFolder()](#listFolder)
- [BluezQt::PendingCall \*moveFile(const QString &sourceFileName, const QString &targetFileName)](#moveFile)
- [QDBusObjectPath objectPath() const](#objectPath)
- [BluezQt::PendingCall \*putFile(const QString &sourceFileName, const QString &targetFileName)](#putFile)

## Detailed Description {#details}

This class represents an OBEX file transfer interface.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ObexFileTransfer::ObexFileTransfer(const QDBusObjectPath &*path*, QObject \**parent* = nullptr) {#ObexFileTransfer}

Creates a new [ObexFileTransfer](bluezqt-obexfiletransfer.md) object at the given session `path` as a child of `parent`.

This class will be typically used with a `path` from result of [ObexManager::createSession](bluezqt-obexmanager.md#createSession)().

### BluezQt::PendingCall \*ObexFileTransfer::changeFolder(const QString &*folder*) {#changeFolder}

Changes the current `folder`.

Possible errors:

- [PendingCall::InvalidArguments](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### BluezQt::PendingCall \*ObexFileTransfer::copyFile(const QString &*sourceFileName*, const QString &*targetFileName*) {#copyFile}

Copies a file at `sourceFileName` to `targetFileName`, both within the remote device.

Possible errors:

- [PendingCall::InvalidArguments](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### BluezQt::PendingCall \*ObexFileTransfer::createFolder(const QString &*folder*) {#createFolder}

Creates a new `folder`.

Possible errors:

- [PendingCall::InvalidArguments](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### BluezQt::PendingCall \*ObexFileTransfer::deleteFile(const QString &*fileName*) {#deleteFile}

Deletes a file/folder at `fileName` within the remote device.

Possible errors:

- [PendingCall::InvalidArguments](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### BluezQt::PendingCall \*ObexFileTransfer::getFile(const QString &*targetFileName*, const QString &*sourceFileName*) {#getFile}

Gets the file at full path `sourceFileName` from the remote device and saves it to `targetFileName`.

If an empty `targetFileName` is given, a name will be automatically calculated for the temporary file.

Possible errors:

- [PendingCall::InvalidArguments](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns [ObexTransferPtr](bluezqt.md#ObexTransferPtr-typedef) pending call.

### BluezQt::PendingCall \*ObexFileTransfer::listFolder() {#listFolder}

Lists a current folder.

Possible errors:

- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns [QList](https://doc.qt.io/qt-6/qlist.html)\<[ObexFileTransferEntry](bluezqt-obexfiletransferentry.md)\> pending call.

### BluezQt::PendingCall \*ObexFileTransfer::moveFile(const QString &*sourceFileName*, const QString &*targetFileName*) {#moveFile}

Moves a file `sourceFileName` to `targetFileName`, both within the remote device.

Possible errors:

- [PendingCall::InvalidArguments](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### QDBusObjectPath ObexFileTransfer::objectPath() const {#objectPath}

Returns the D-Bus object path of the file transfer session.

### BluezQt::PendingCall \*ObexFileTransfer::putFile(const QString &*sourceFileName*, const QString &*targetFileName*) {#putFile}

Puts the file at full path `sourceFileName` to the remote device in `targetFileName`.

If an empty `targetFileName` is given, a name will be automatically calculated for the temporary file.

Possible errors:

- [PendingCall::InvalidArguments](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns [ObexTransferPtr](bluezqt.md#ObexTransferPtr-typedef) pending call.
