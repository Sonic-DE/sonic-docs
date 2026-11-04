---
title: "Sonic::Ipc::Client Class"
description: "Connects to a Server."
---

# Sonic::Ipc::Client Class

Connects to a Server. [More...](#details)

- **Header:** `#include <Sonic/Ipc/Client>`
- **CMake:** `find_package(SonicIpc REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Sonic::Ipc)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](sonic-ipc-client-members.md)

## Public Functions

- [Client(quint16 protocolVersion, qint64 maxPayload = defaultMaxPayload, QObject \*parent = nullptr)](#Client)
- [void connectToServer(const QString &nameOrPath)](#connectToServer)
- [Sonic::Ipc::Connection \*connection() const](#connection)
- [void disconnectFromServer()](#disconnectFromServer)
- [void setReconnectInterval(int msecs)](#setReconnectInterval)

## Signals

- [void connected(Sonic::Ipc::Connection \*connection)](#connected)
- [void connectionFailed(const QString &reason)](#connectionFailed)
- [void versionRejected(quint16 serverVersion)](#versionRejected)

## Static Public Members

- [std::optional\<Sonic::Ipc::Frame\> request(const QString &nameOrPath, quint32 type, QByteArrayView payload, quint16 protocolVersion, int timeoutMs, QString \*error, qint64 maxPayload = defaultMaxPayload)](#request)

## Detailed Description {#details}

Long-lived subscribers can turn on automatic reconnection; it stops for good once the server rejects this side's protocol version.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Client::Client(quint16 *protocolVersion*, qint64 *maxPayload* = defaultMaxPayload, QObject \**parent* = nullptr) {#Client}

Creates a client that speaks application protocol `protocolVersion` and rejects payloads larger than `maxPayload` bytes, with the given `parent`.

### void Client::connectToServer(const QString &*nameOrPath*) {#connectToServer}

Connects to the server at `nameOrPath`, as [QLocalSocket::connectToServer](https://doc.qt.io/qt-6/qlocalsocket.html#connectToServer)() takes it; [connected](sonic-ipc-client.md#connected)() or [connectionFailed](sonic-ipc-client.md#connectionFailed)() follows.

### \[signal\] void Client::connected(Sonic::Ipc::Connection \**connection*) {#connected}

The client connected; `connection` belongs to the client.

### Sonic::Ipc::Connection \*Client::connection() const {#connection}

The current connection; null while not connected.

### \[signal\] void Client::connectionFailed(const QString &*reason*) {#connectionFailed}

Connecting failed, for the given `reason`.

### void Client::disconnectFromServer() {#disconnectFromServer}

Stops reconnecting and closes the connection.

### \[static\] std::optional\<Sonic::Ipc::Frame\> Client::request(const QString &*nameOrPath*, quint32 *type*, QByteArrayView *payload*, quint16 *protocolVersion*, int *timeoutMs*, QString \**error*, qint64 *maxPayload* = defaultMaxPayload) {#request}

Blocking request for threads without an event loop: connects to `nameOrPath`, sends one frame of `type` with `payload` in protocol `protocolVersion` and waits for one reply, all within `timeoutMs` (-1: no timeout). Replies larger than `maxPayload` bytes are rejected. The socket is created on the calling thread.

On failure it returns nothing and sets `error`, when it isn't null.

### void Client::setReconnectInterval(int *msecs*) {#setReconnectInterval}

Reconnects `msecs` after a failed connect or a disconnect; 0, the default, turns it off.

### \[signal\] void Client::versionRejected(quint16 *serverVersion*) {#versionRejected}

The server rejected this side's protocol version; it speaks `serverVersion`. The client stops reconnecting.
