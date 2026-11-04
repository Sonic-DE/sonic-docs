---
title: "Sonic::Ipc::Connection Class"
description: "One framed connection over a QLocalSocket."
---

# Sonic::Ipc::Connection Class

One framed connection over a [QLocalSocket](https://doc.qt.io/qt-6/qlocalsocket.html). [More...](#details)

- **Header:** `#include <Sonic/Ipc/Connection>`
- **CMake:** `find_package(SonicIpc REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Sonic::Ipc)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](sonic-ipc-connection-members.md)

## Public Functions

- [Connection(QLocalSocket \*socket, quint16 protocolVersion, qint64 maxPayload = defaultMaxPayload, QObject \*parent = nullptr)](#Connection)
- [std::optional\<Sonic::Ipc::Connection::PeerCredentials\> peerCredentials() const](#peerCredentials)
- [quint16 protocolVersion() const](#protocolVersion)
- [bool send(quint32 type, QByteArrayView payload)](#send)
- [bool sendBlocking(quint32 type, QByteArrayView payload, int msecs)](#sendBlocking)
- [QLocalSocket \*socket() const](#socket)
- [std::optional\<Sonic::Ipc::Frame\> waitForFrame(int msecs)](#waitForFrame)

## Signals

- [void disconnected()](#disconnected)
- [void frameReceived(quint32 type, const QByteArray &payload)](#frameReceived)
- [void protocolError(const QString &reason)](#protocolError)
- [void versionRejected(quint16 peerVersion)](#versionRejected)

## Detailed Description {#details}

Frames arrive through [frameReceived](sonic-ipc-connection.md#frameReceived)(); threads without an event loop use [waitForFrame](sonic-ipc-connection.md#waitForFrame)() and [sendBlocking](sonic-ipc-connection.md#sendBlocking)() instead. A protocol error aborts the socket.

## Member Function Documentation {#member-function-documentation}

### Connection::Connection(QLocalSocket \**socket*, quint16 *protocolVersion*, qint64 *maxPayload* = defaultMaxPayload, QObject \**parent* = nullptr) {#Connection}

Takes `socket` and reparents it to this connection, which speaks application protocol `protocolVersion` and rejects payloads larger than `maxPayload` bytes. `parent` is the connection's parent.

### \[signal\] void Connection::disconnected() {#disconnected}

The socket disconnected.

### \[signal\] void Connection::frameReceived(quint32 *type*, const QByteArray &*payload*) {#frameReceived}

A frame of `type` with `payload` arrived.

### std::optional\<Sonic::Ipc::Connection::PeerCredentials\> Connection::peerCredentials() const {#peerCredentials}

The process at the other end; nothing when the socket has no descriptor or the system doesn't tell.

### \[signal\] void Connection::protocolError(const QString &*reason*) {#protocolError}

The peer sent data this side rejects, for the given `reason`; the socket is aborted. A peer with another protocol version is told so first.

### quint16 Connection::protocolVersion() const {#protocolVersion}

The application protocol version this side speaks.

### bool Connection::send(quint32 *type*, QByteArrayView *payload*) {#send}

Writes a frame of `type` with `payload`; false when the socket isn't connected, the write fails, or `type` is the reserved [Frame::VersionRejected](sonic-ipc-frame.md#VersionRejected-var).

### bool Connection::sendBlocking(quint32 *type*, QByteArrayView *payload*, int *msecs*) {#sendBlocking}

Writes a frame of `type` with `payload`, then waits until everything is written or `msecs` pass (-1: no timeout).

### QLocalSocket \*Connection::socket() const {#socket}

The connection's socket.

### \[signal\] void Connection::versionRejected(quint16 *peerVersion*) {#versionRejected}

The peer rejected this side's protocol version; it speaks `peerVersion`.

### std::optional\<Sonic::Ipc::Frame\> Connection::waitForFrame(int *msecs*) {#waitForFrame}

Blocks until a frame arrives or `msecs` pass (-1: no timeout).
