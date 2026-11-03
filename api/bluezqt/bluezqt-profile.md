---
title: "BluezQt::Profile Class"
description: "Bluetooth profile."
---

# BluezQt::Profile Class

Bluetooth profile. [More...](#details)

- **Header:** `#include <BluezQt/Profile>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-profile-members.md)

## Public Types

- [enum Profile::LocalRole](#LocalRole-enum)

## Properties

- [\[read-only\] uuid : QString](#uuid-prop)

## Public Functions

- [Profile(QObject \*parent = nullptr)](#Profile)
- [QSharedPointer\<QLocalSocket\> createSocket(const QDBusUnixFileDescriptor &fd)](#createSocket)
- [void newConnection(BluezQt::DevicePtr device, const QDBusUnixFileDescriptor &fd, const QVariantMap &properties, const BluezQt::Request\<\> &request)](#newConnection)
- [QDBusObjectPath objectPath() const](#objectPath)
- [void release()](#release)
- [void requestDisconnection(BluezQt::DevicePtr device, const BluezQt::Request\<\> &request)](#requestDisconnection)
- [void setAutoConnect(bool autoConnect)](#setAutoConnect)
- [void setChannel(quint16 channel)](#setChannel)
- [void setFeatures(quint16 features)](#setFeatures)
- [void setLocalRole(BluezQt::Profile::LocalRole role)](#setLocalRole)
- [void setName(const QString &name)](#setName)
- [void setPsm(quint16 psm)](#setPsm)
- [void setRequireAuthentication(bool require)](#setRequireAuthentication)
- [void setRequireAuthorization(bool require)](#setRequireAuthorization)
- [void setService(const QString &service)](#setService)
- [void setServiceRecord(const QString &serviceRecord)](#setServiceRecord)
- [void setVersion(quint16 version)](#setVersion)
- [QString uuid() const](#uuid)

## Detailed Description {#details}

This class represents a Bluetooth profile.

It is only needed to reimplement pure virtual functions. You don't need to set any additional properties.

But you may need to specify at least channel number or PSM in case it couldn't be determined from UUID. It is also a good idea to provide name for the profile.

Setting the channel number with [setChannel](bluezqt-profile.md#setChannel)() will make the profile use RFCOMM, while setting the PSM with [setPsm](bluezqt-profile.md#setPsm)() will make the profile use L2CAP.

> **Note:** The return value of requests will be sent asynchronously with Request class. It is also possible to cancel/reject all requests.

## Member Type Documentation {#member-type-documentation}

### enum Profile::LocalRole {#LocalRole-enum}

Local role to identify sides in asymmetric profiles.

| Constant | Value | Description |
| --- | --- | --- |
| `BluezQt::Profile::ClientRole` | `0` | Indicates that this is a client. |
| `BluezQt::Profile::ServerRole` | `1` | Indicates that this is a server. |

## Property Documentation {#property-documentation}

### \[read-only\] uuid : QString {#uuid-prop}

**Access functions:**

- virtual `QString` **[uuid](bluezqt-profile.md#uuid)**() const = 0

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Profile::Profile(QObject \**parent* = nullptr) {#Profile}

Creates a new Profile object as a child of `parent`.

### QSharedPointer\<QLocalSocket\> Profile::createSocket(const QDBusUnixFileDescriptor &*fd*) {#createSocket}

Creates a socket from the given file descriptor `fd`.

*See also* [newConnection](bluezqt-profile.md#newConnection)()

### \[virtual\] void Profile::newConnection(BluezQt::DevicePtr *device*, const QDBusUnixFileDescriptor &*fd*, const QVariantMap &*properties*, const BluezQt::Request\<\> &*request*) {#newConnection}

Requests the new connection.

Common properties:

- quint16 Version - Profile version
- quint16 Features - Profile features

To create socket from fd, you can use:

```cpp
QSharedPointer<QLocalSocket> socket = createSocket(fd);
if (!socket->isValid()) {
    delete socket;
    request.cancel();
    return;
}
```

`device` The device that requested the connection.

`fd` The socket file descriptor.

`properties` Additional properties.

`request` The request to be used for sending a reply.

### \[pure virtual\] QDBusObjectPath Profile::objectPath() const {#objectPath}

Returns the D-Bus object path of the profile.

The path where the profile will be registered.

> **Note:** You must provide valid object path!

### \[virtual\] void Profile::release() {#release}

Indicates that the profile was unregistered.

This method gets called when the Bluetooth daemon unregisters the profile.

A profile can use it to do cleanup tasks. There is no need to unregister the profile, because when this method gets called it has already been unregistered.

### \[virtual\] void Profile::requestDisconnection(BluezQt::DevicePtr *device*, const BluezQt::Request\<\> &*request*) {#requestDisconnection}

Requests the disconnection of the profile.

This method gets called when a profile gets disconnected.

`device` The device to be disconnected.

`request` The request to be used for sending a reply.

### void Profile::setAutoConnect(bool *autoConnect*) {#setAutoConnect}

Sets whether the profile will `autoConnect`.

In case of a client UUID this will force connection of the RFCOMM or L2CAP channels when a remote device is connected.

### void Profile::setChannel(quint16 *channel*) {#setChannel}

Sets the RFCOMM `channel` number.

Available channel number range is 0-31.

Setting channel number to 0 will automatically choose the correct channel number for profile UUID.

### void Profile::setFeatures(quint16 *features*) {#setFeatures}

Sets the profile `features`.

### void Profile::setLocalRole(BluezQt::Profile::LocalRole *role*) {#setLocalRole}

Sets the local `role` to identify the side.

For asymmetric profiles that do not have UUIDs available to uniquely identify each side this parameter allows specifying the precise local role.

### void Profile::setName(const QString &*name*) {#setName}

Sets the human readable `name` of the profile.

### void Profile::setPsm(quint16 *psm*) {#setPsm}

Sets the L2CAP `psm` port number.

PSM (Protocol Service Multiplexer) is a port number in L2CAP.

Setting PSM to 0 will automatically choose the correct PSM for the profile UUID.

### void Profile::setRequireAuthentication(bool *require*) {#setRequireAuthentication}

Sets whether the pairing is required to connect with parameter `require`.

### void Profile::setRequireAuthorization(bool *require*) {#setRequireAuthorization}

Sets whether the authorization is required to connect with parameter `require`.

### void Profile::setService(const QString &*service*) {#setService}

Sets the primary `service` class UUID (if different from profile UUID).

### void Profile::setServiceRecord(const QString &*serviceRecord*) {#setServiceRecord}

Sets an SDP `serviceRecord`.

This allows to provide a manual SDP record, otherwise it will be generated automatically.

### void Profile::setVersion(quint16 *version*) {#setVersion}

Sets the profile `version`.

### \[pure virtual\] QString Profile::uuid() const {#uuid}

Returns the UUID of the profile.

> **Note:** Getter function for property [uuid](bluezqt-profile.md#uuid-prop).
