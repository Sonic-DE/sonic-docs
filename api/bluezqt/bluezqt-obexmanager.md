---
title: "BluezQt::ObexManager Class"
description: "OBEX manager."
---

# BluezQt::ObexManager Class

OBEX manager. [More...](#details)

- **Header:** `#include <BluezQt/ObexManager>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS BluezQt)`  
  `target_link_libraries(mytarget PRIVATE KF6::BluezQt)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](bluezqt-obexmanager-members.md)

## Properties

- [\[read-only\] initialized : bool](#initialized-prop)
- [\[read-only\] operational : bool](#operational-prop)
- [\[read-only\] sessions : QList\<ObexSessionPtr\>](#sessions-prop)

## Public Functions

- [ObexManager(QObject \*parent = nullptr)](#ObexManager)
- [BluezQt::InitObexManagerJob \*init()](#init)
- [bool isInitialized() const](#isInitialized)
- [bool isOperational() const](#isOperational)
- [BluezQt::ObexSessionPtr sessionForPath(const QDBusObjectPath &path) const](#sessionForPath)
- [QList\<BluezQt::ObexSessionPtr\> sessions() const](#sessions)

## Public Slots

- [BluezQt::PendingCall \*createSession(const QString &destination, const QVariantMap &args)](#createSession)
- [BluezQt::PendingCall \*registerAgent(BluezQt::ObexAgent \*agent)](#registerAgent)
- [BluezQt::PendingCall \*removeSession(const QDBusObjectPath &session)](#removeSession)
- [BluezQt::PendingCall \*unregisterAgent(BluezQt::ObexAgent \*agent)](#unregisterAgent)

## Signals

- [void operationalChanged(bool operational)](#operationalChanged)
- [void sessionAdded(BluezQt::ObexSessionPtr session)](#sessionAdded)
- [void sessionRemoved(BluezQt::ObexSessionPtr session)](#sessionRemoved)

## Static Public Members

- [BluezQt::PendingCall \*startService()](#startService)

## Detailed Description {#details}

The entry point to communicate with session BlueZ obex daemon.

You must call [init](bluezqt-obexmanager.md#init)() before other functions can be used.

> **Note:** If manager is not operational, all methods that returns a [PendingCall](bluezqt-pendingcall.md) will fail with [PendingCall::InternalError](bluezqt-pendingcall.md#Error-enum).

## Property Documentation {#property-documentation}

### \[read-only\] initialized : bool {#initialized-prop}

**Access functions:**

- `bool` **[isInitialized](bluezqt-obexmanager.md#isInitialized)**() const

### \[read-only\] operational : bool {#operational-prop}

**Access functions:**

- `bool` **[isOperational](bluezqt-obexmanager.md#isOperational)**() const

**Notifier signal:**

- `void` **[operationalChanged](bluezqt-obexmanager.md#operationalChanged)**(`bool` *operational*)

### \[read-only\] sessions : QList\<ObexSessionPtr\> {#sessions-prop}

**Access functions:**

- `QList`\<`BluezQt::ObexSessionPtr`\> **[sessions](bluezqt-obexmanager.md#sessions)**() const

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ObexManager::ObexManager(QObject \**parent* = nullptr) {#ObexManager}

Creates a new [ObexManager](bluezqt-obexmanager.md) object as a child of `parent`.

### \[slot\] BluezQt::PendingCall \*ObexManager::createSession(const QString &*destination*, const QVariantMap &*args*) {#createSession}

Creates a new OBEX session with the address of the target device `destination` and the given session parameters `args`.

The `args` parameter is a dictionary to hold optional or type-specific parameters.

Typical parameters:

- [QString](https://doc.qt.io/qt-6/qstring.html) target - type of session to be created
- [QString](https://doc.qt.io/qt-6/qstring.html) source - device address to be used

Supported targets:

- ftp - [ObexFileTransfer](bluezqt-obexfiletransfer.md)
- map
- opp - [ObexObjectPush](bluezqt-obexobjectpush.md)
- pbap
- sync

Possible errors:

- [PendingCall::InvalidArguments](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::Failed](bluezqt-pendingcall.md#Error-enum)

Returns QDBusObjectPath pending call.

### BluezQt::InitObexManagerJob \*ObexManager::init() {#init}

Creates a new init manager job.

### bool ObexManager::isInitialized() const {#isInitialized}

Returns whether the manager is initialized.

> **Note:** Getter function for property [initialized](bluezqt-obexmanager.md#initialized-prop).

### bool ObexManager::isOperational() const {#isOperational}

Returns whether the manager is operational.

The manager is operational when initialization was successful and the BlueZ session daemon is running.

> **Note:** Getter function for property [operational](bluezqt-obexmanager.md#operational-prop).

### \[signal\] void ObexManager::operationalChanged(bool *operational*) {#operationalChanged}

Indicates that the `operational` state has changed.

> **Note:** Notifier signal for property [operational](bluezqt-obexmanager.md#operational-prop).

### \[slot\] BluezQt::PendingCall \*ObexManager::registerAgent(BluezQt::ObexAgent \**agent*) {#registerAgent}

Registers an `agent`.

This agent will be used to authorize an incoming object push requests.

Possible errors:

- [PendingCall::AlreadyExists](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### \[slot\] BluezQt::PendingCall \*ObexManager::removeSession(const QDBusObjectPath &*session*) {#removeSession}

Removes an existing OBEX `session`.

Possible errors:

- [PendingCall::InvalidArguments](bluezqt-pendingcall.md#Error-enum)
- [PendingCall::NotAuthorized](bluezqt-pendingcall.md#Error-enum)

Returns void pending call.

### \[signal\] void ObexManager::sessionAdded(BluezQt::ObexSessionPtr *session*) {#sessionAdded}

Indicates that the `session` was added.

### BluezQt::ObexSessionPtr ObexManager::sessionForPath(const QDBusObjectPath &*path*) const {#sessionForPath}

Returns a session for the specified `path`.

The `path` does not need to be equal to the [ObexSession](bluezqt-obexsession.md) path, startsWith test is performed in the search. That means you can use this method to get [ObexSession](bluezqt-obexsession.md) from path returned by [createSession](bluezqt-obexmanager.md#createSession)().

### \[signal\] void ObexManager::sessionRemoved(BluezQt::ObexSessionPtr *session*) {#sessionRemoved}

Indicates that the `session` was removed.

### QList\<BluezQt::ObexSessionPtr\> ObexManager::sessions() const {#sessions}

Returns a list of all sessions.

> **Note:** Getter function for property [sessions](bluezqt-obexmanager.md#sessions-prop).

### \[static\] BluezQt::PendingCall \*ObexManager::startService() {#startService}

Attempts to start org.bluez.obex service by D-Bus activation.

Possible return values are 1 if the service was started, 2 if the service is already running, or error if the service could not be started.

Returns quint32 pending call.

### \[slot\] BluezQt::PendingCall \*ObexManager::unregisterAgent(BluezQt::ObexAgent \**agent*) {#unregisterAgent}

Unregisters an `agent`.

Possible errors:

- [PendingCall::DoesNotExist](bluezqt-pendingcall.md#Error-enum)

Returns void pending call
