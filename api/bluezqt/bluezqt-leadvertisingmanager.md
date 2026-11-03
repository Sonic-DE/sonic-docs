---
title: "BluezQt::LEAdvertisingManager Class"
description: "Bluetooth LE advertising manager."
---

# BluezQt::LEAdvertisingManager Class

Bluetooth LE advertising manager. [More...](#details)

- **Header:** `#include <BluezQt/LEAdvertisingManager>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-leadvertisingmanager-members.md)

## Public Functions

- [BluezQt::PendingCall \*registerAdvertisement(BluezQt::LEAdvertisement \*advertisement)](#registerAdvertisement)
- [BluezQt::PendingCall \*unregisterAdvertisement(BluezQt::LEAdvertisement \*advertisement)](#unregisterAdvertisement)

## Detailed Description {#details}

The Advertising Manager allows external applications to register Advertisement Data which should be broadcast to devices. Advertisement Data elements must follow the API for LE Advertisement Data.

*See also* [LEAdvertisement](bluezqt-leadvertisement.md)

## Member Function Documentation {#member-function-documentation}

### BluezQt::PendingCall \*LEAdvertisingManager::registerAdvertisement(BluezQt::LEAdvertisement \**advertisement*) {#registerAdvertisement}

Registers an `advertisement` object to be sent over the LE Advertising channel.

The service must be exported under interface LEAdvertisement1.

InvalidArguments error indicates invalid or conflicting properties.

InvalidLength error indicates that provided data results in too long data packet.

The properties of this object are parsed on register, any changes are ignored.

If the same object is registered twice it will result in an AlreadyExists error.

NotPermitted error indicates that the maximum number of advertisements is reached.

Possible errors:

- [PendingCall::InvalidArguments](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::AlreadyExists](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::InvalidLength](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::NotPermitted](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### BluezQt::PendingCall \*LEAdvertisingManager::unregisterAdvertisement(BluezQt::LEAdvertisement \**advertisement*) {#unregisterAdvertisement}

Unregisters `advertisement`.

This unregisters an advertisement that has been previously registered. The object path must match the same value that has been used on registration.

Possible errors:

- [PendingCall::InvalidArguments](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::DoesNotExist](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.
