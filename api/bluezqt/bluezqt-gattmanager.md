---
title: "BluezQt::GattManager Class"
description: "Bluetooth GattManager."
---

# BluezQt::GattManager Class

Bluetooth [GattManager](bluezqt-gattmanager.md). [More...](#details)

- **Header:** `#include <BluezQt/GattManager>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-gattmanager-members.md)

## Public Functions

- [BluezQt::PendingCall \*registerApplication(BluezQt::GattApplication \*application)](#registerApplication)
- [BluezQt::PendingCall \*unregisterApplication(BluezQt::GattApplication \*application)](#unregisterApplication)

## Detailed Description {#details}

GATT Manager allows external applications to register GATT services and profiles.

Registering a profile allows applications to subscribe to \*remote\* services. These must implement the GattProfile1 interface defined above.

Registering a service allows applications to publish a \*local\* GATT service, which then becomes available to remote devices. A GATT service is represented by a D-Bus object hierarchy where the root node corresponds to a service and the child nodes represent characteristics and descriptors that belong to that service. Each node must implement one of GattService1, GattCharacteristic1, or GattDescriptor1 interfaces described above, based on the attribute it represents. Each node must also implement the standard D-Bus Properties interface to expose their properties. These objects collectively represent a GATT service definition.

*See also* [GattApplication](bluezqt-gattapplication.md)

## Member Function Documentation {#member-function-documentation}

### BluezQt::PendingCall \*GattManager::registerApplication(BluezQt::GattApplication \**application*) {#registerApplication}

Registers a local GATT services hierarchy as described above (GATT Server) and/or GATT profiles (GATT Client) for a given `application`.

The application object path together with the D-Bus system bus connection ID define the identification of the application registering a GATT based service or profile.

Possible errors:

- org.bluez.Error.InvalidArguments
- org.bluez.Error.AlreadyExists

Returns void pending call.

### BluezQt::PendingCall \*GattManager::unregisterApplication(BluezQt::GattApplication \**application*) {#unregisterApplication}

Unregisters the services that have been previously registered for the given `application`.

The object path parameter must match the same value that has been used upon registration.

Possible errors:

- org.bluez.Error.InvalidArguments
- org.bluez.Error.DoesNotExist

Returns void pending call.
