---
title: "SignOn::AccessRequest Class"
description: "A client's request to access an identity."
---

# SignOn::AccessRequest Class

A client's request to access an identity. [More...](#details)

- **Header:** `#include <SignOn/AbstractAccessControlManager>`

[List of all members, including inherited members](signon-accessrequest-members.md)

## Public Functions

- [AccessRequest()](#AccessRequest)
- [AccessRequest(const SignOn::AccessRequest &other)](#AccessRequest-1)
- [quint32 identity() const](#identity)
- [const QDBusConnection &peerConnection() const](#peerConnection)
- [const QDBusMessage &peerMessage() const](#peerMessage)
- [void setIdentity(quint32 id)](#setIdentity)
- [void setPeer(const QDBusConnection &connection, const QDBusMessage &message)](#setPeer)

## Detailed Description {#details}

*See also* [AbstractAccessControlManager::handleRequest](signon-abstractaccesscontrolmanager.md#handleRequest)()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] AccessRequest::AccessRequest() {#AccessRequest}

Creates an empty request.

### AccessRequest::AccessRequest(const SignOn::AccessRequest &*other*) {#AccessRequest-1}

Copy constructor, copying `other`.

### quint32 AccessRequest::identity() const {#identity}

The SignOn::Identity resource being accessed.

*See also* [setIdentity](signon-accessrequest.md#setIdentity)()

### const QDBusConnection &AccessRequest::peerConnection() const {#peerConnection}

The connection over which the request was sent.

### const QDBusMessage &AccessRequest::peerMessage() const {#peerMessage}

The request message sent over DBUS by the client.

### void AccessRequest::setIdentity(quint32 *id*) {#setIdentity}

Specifies the SignOn::Identity resource `id` being accessed.

*See also* [identity](signon-accessrequest.md#identity)()

### void AccessRequest::setPeer(const QDBusConnection &*connection*, const QDBusMessage &*message*) {#setPeer}

Identifies the client requesting the access: `connection` is the connection over which the message was sent, and `message` the request message sent over DBUS by the process.
