---
title: "BluezQt::ObexObjectPush Class"
description: "OBEX object push."
---

# BluezQt::ObexObjectPush Class

OBEX object push. [More...](#details)

- **Header:** `#include <BluezQt/ObexObjectPush>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-obexobjectpush-members.md)

## Public Functions

- [ObexObjectPush(const QDBusObjectPath &path, QObject \*parent = nullptr)](#ObexObjectPush)
- [BluezQt::PendingCall \*exchangeBusinessCards(const QString &clientFileName, const QString &targetFileName)](#exchangeBusinessCards)
- [QDBusObjectPath objectPath() const](#objectPath)
- [BluezQt::PendingCall \*pullBusinessCard(const QString &targetFileName)](#pullBusinessCard)
- [BluezQt::PendingCall \*sendFile(const QString &fileName)](#sendFile)

## Detailed Description {#details}

This class represents an OBEX object push interface.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ObexObjectPush::ObexObjectPush(const QDBusObjectPath &*path*, QObject \**parent* = nullptr) {#ObexObjectPush}

Creates a new [ObexObjectPush](bluezqt-obexobjectpush.md) object with the given session `path` as a child of `parent`.

This class will be typically used with a `path` from result of [ObexManager::createSession](bluezqt-obexmanager.md#createSession)().

### BluezQt::PendingCall \*ObexObjectPush::exchangeBusinessCards(const QString &*clientFileName*, const QString &*targetFileName*) {#exchangeBusinessCards}

Exchanges the business cards `clientFileName` and `targetFileName` on the remote device.

This method pushes the local business card to the remote device and then retrieve the remote business card and store it in a local file.

If an empty `targetFileName` is given, a name will be automatically calculated for the temporary file.

The returned [ObexTransfer](bluezqt-obextransfer.md) can be used to track progress of transfer.

Possible errors:

- [PendingCall::InvalidArguments](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns [ObexTransfer](bluezqt-obextransfer.md) \* pending call.

### QDBusObjectPath ObexObjectPush::objectPath() const {#objectPath}

Returns the D-Bus object path of the object push session.

### BluezQt::PendingCall \*ObexObjectPush::pullBusinessCard(const QString &*targetFileName*) {#pullBusinessCard}

Pulls the business card from targetFileName within a remote device.

If an empty `targetFileName` is given, a name will be automatically calculated for the temporary file.

The returned [ObexTransfer](bluezqt-obextransfer.md) can be used to track progress of transfer.

Possible errors:

- [PendingCall::InvalidArguments](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns [ObexTransfer](bluezqt-obextransfer.md) \* pending call.

### BluezQt::PendingCall \*ObexObjectPush::sendFile(const QString &*fileName*) {#sendFile}

Sends one local file `fileName` to the remote device.

The returned [ObexTransfer](bluezqt-obextransfer.md) can be used to track progress of transfer.

Possible errors:

- [PendingCall::InvalidArguments](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns [ObexTransfer](bluezqt-obextransfer.md) \* pending call.
