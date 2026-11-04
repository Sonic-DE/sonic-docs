---
title: "Sonic::Ipc::Server Class"
description: "Listens on a local socket."
---

# Sonic::Ipc::Server Class

Listens on a local socket. [More...](#details)

- **Header:** `#include <Sonic/Ipc/Server>`
- **CMake:** `find_package(SonicIpc REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Sonic::Ipc)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](sonic-ipc-server-members.md)

## Public Types

- [enum Server::Access](#Access-enum)

## Public Functions

- [Server(QObject \*parent = nullptr)](#Server)
- [void broadcast(quint32 type, QByteArrayView payload)](#broadcast)
- [void close()](#close)
- [QList\<Sonic::Ipc::Connection \*\> connections() const](#connections)
- [QString errorString() const](#errorString)
- [QString fullServerName() const](#fullServerName)
- [bool listen(const QString &nameOrPath, Sonic::Ipc::Server::Access access, quint16 protocolVersion, qint64 maxPayload = defaultMaxPayload)](#listen)

## Signals

- [void newConnection(Sonic::Ipc::Connection \*connection)](#newConnection)

## Static Public Members

- [QString userSocketPath(const QString &fileName)](#userSocketPath)

## Detailed Description {#details}

Wraps each client in a Connection, parented to this server and deleted when it disconnects.

## Member Type Documentation {#member-type-documentation}

### enum Server::Access {#Access-enum}

Who may connect to the socket.

| Constant | Value | Description |
| --- | --- | --- |
| `Sonic::Ipc::Server::Access::User` | `0` | Owner only ([QLocalServer::UserAccessOption](https://doc.qt.io/qt-6/qlocalserver.html#SocketOption-enum)). |
| `Sonic::Ipc::Server::Access::Group` | `1` | Owner and group. |
| `Sonic::Ipc::Server::Access::World` | `2` | Everyone. |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Server::Server(QObject \**parent* = nullptr) {#Server}

Creates a server that isn't listening yet, with the given `parent`.

### void Server::broadcast(quint32 *type*, QByteArrayView *payload*) {#broadcast}

Sends a frame of `type` with `payload` to every connection.

### void Server::close() {#close}

Closes every connection and stops listening.

### QList\<Sonic::Ipc::Connection \*\> Server::connections() const {#connections}

The connected clients.

### QString Server::errorString() const {#errorString}

Why [listen](sonic-ipc-server.md#listen)() failed.

### QString Server::fullServerName() const {#fullServerName}

The socket's file path; callers that hand the socket to another uid chown this after [listen](sonic-ipc-server.md#listen)().

### bool Server::listen(const QString &*nameOrPath*, Sonic::Ipc::Server::Access *access*, quint16 *protocolVersion*, qint64 *maxPayload* = defaultMaxPayload) {#listen}

Passes `nameOrPath` to [QLocalServer::listen](https://doc.qt.io/qt-6/qlocalserver.html#listen)() unchanged. Fails while another server answers on it, so a live server is never replaced; a stale socket file is removed and listened on.

`access` says who may connect. Connections speak application protocol `protocolVersion` and reject payloads larger than `maxPayload` bytes.

### \[signal\] void Server::newConnection(Sonic::Ipc::Connection \**connection*) {#newConnection}

A client connected; `connection` belongs to the server.

### \[static\] QString Server::userSocketPath(const QString &*fileName*) {#userSocketPath}

\<RuntimeLocation\>/`fileName`, or /tmp/sonic-\<uid\>/`fileName` when Qt has no runtime location. The /tmp directory is created with mode 0700 and refused (empty result) if it is a symlink, not a directory, owned by another user, or open to group or others.
