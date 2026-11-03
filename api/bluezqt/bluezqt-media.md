---
title: "BluezQt::Media Class"
description: "Bluetooth Media."
---

# BluezQt::Media Class

Bluetooth Media. [More...](#details)

- **Header:** `#include <BluezQt/Media>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-media-members.md)

## Public Functions

- [BluezQt::PendingCall \*registerEndpoint(BluezQt::MediaEndpoint \*endpoint)](#registerEndpoint)
- [BluezQt::PendingCall \*unregisterEndpoint(BluezQt::MediaEndpoint \*endpoint)](#unregisterEndpoint)

## Detailed Description {#details}

This allows media endpoints to be established in accordance with the capabilities of a specific media service profile.

For example, an A2DP media endpoint could be created allowing data from a remote device to be streamed to/from the sender.

Each media endpoint is associated with a service object instance that implements the required behaviours of the endpoint. The service object must be created at a given path before it is registered.

*See also* [MediaEndpoint](bluezqt-mediaendpoint.md)

## Member Function Documentation {#member-function-documentation}

### BluezQt::PendingCall \*Media::registerEndpoint(BluezQt::MediaEndpoint \**endpoint*) {#registerEndpoint}

Registers an `endpoint`.

Register a local end point to sender, the sender can register as many end points as it likes.

> **Note:** If the sender disconnects the end points are automatically unregistered.

Possible errors:

- [PendingCall::InvalidArguments](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::NotSupported](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### BluezQt::PendingCall \*Media::unregisterEndpoint(BluezQt::MediaEndpoint \**endpoint*) {#unregisterEndpoint}

Unregisters an `endpoint`.

Returns void pending call.
