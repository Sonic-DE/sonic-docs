---
title: "SignOn::AbstractAccessControlManager Class"
description: "Helps filtering incoming Signon Daemon requests, based on security privileges of the client processes."
---

# SignOn::AbstractAccessControlManager Class

Helps filtering incoming Signon Daemon requests, based on security privileges of the client processes. [More...](#details)

- **Header:** `#include <SignOn/AbstractAccessControlManager>`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](signon-abstractaccesscontrolmanager-members.md)

## Public Functions

- [AbstractAccessControlManager(QObject \*parent = 0)](#AbstractAccessControlManager)
- [~AbstractAccessControlManager()](#dtor.AbstractAccessControlManager)
- [QString appIdOfPeer(const QDBusConnection &peerConnection, const QDBusMessage &peerMessage)](#appIdOfPeer)
- [SignOn::AccessReply \*handleRequest(const SignOn::AccessRequest &request)](#handleRequest)
- [bool isPeerAllowedToAccess(const QDBusConnection &peerConnection, const QDBusMessage &peerMessage, const QString &securityContext)](#isPeerAllowedToAccess)
- [QString keychainWidgetAppId()](#keychainWidgetAppId)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] AbstractAccessControlManager::AbstractAccessControlManager(QObject \**parent* = 0) {#AbstractAccessControlManager}

Constructs a [AbstractAccessControlManager](signon-abstractaccesscontrolmanager.md) object with the given `parent`.

### \[virtual noexcept\] AbstractAccessControlManager::~AbstractAccessControlManager() {#dtor.AbstractAccessControlManager}

Destructor.

### \[virtual\] QString AbstractAccessControlManager::appIdOfPeer(const QDBusConnection &*peerConnection*, const QDBusMessage &*peerMessage*) {#appIdOfPeer}

Looks up for the application identifier of a specific client process. `peerConnection` is the connection over which the message was sent, and `peerMessage` the request message sent over DBUS by the process.

Returns the application identifier of the process, or an empty string if none found.

### \[virtual\] SignOn::AccessReply \*AbstractAccessControlManager::handleRequest(const SignOn::AccessRequest &*request*) {#handleRequest}

Asynchronously handle an access request from a client; `request` describes the requested access.

Returns an [AccessReply](signon-accessreply.md) object which can be used to obtain the asynchronous reply.

### \[virtual\] bool AbstractAccessControlManager::isPeerAllowedToAccess(const QDBusConnection &*peerConnection*, const QDBusMessage &*peerMessage*, const QString &*securityContext*) {#isPeerAllowedToAccess}

Checks if a client process is allowed to access objects with a certain security context. The access type to be checked depends on the concrete implementation of this function.

`peerConnection` is the connection over which the message was sent, `peerMessage` the request message sent over DBUS by the process, and `securityContext` the security context to be checked against.

Returns true, if the peer is allowed, false otherwise.

### \[virtual\] QString AbstractAccessControlManager::keychainWidgetAppId() {#keychainWidgetAppId}

Returns the application identifier of the keychain widget
