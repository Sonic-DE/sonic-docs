---
title: "List of All Members for Sonic::Ipc::Connection"
description: "Every member of Sonic::Ipc::Connection, including inherited members."
parent: "sonicipc/sonic-ipc-connection"
---

# List of All Members for Sonic::Ipc::Connection

This is the complete list of members for [Sonic::Ipc::Connection](sonic-ipc-connection.md), including inherited members.

- [Connection(QLocalSocket \*, quint16, qint64, QObject \*)](sonic-ipc-connection.md#Connection)
- [disconnected()](sonic-ipc-connection.md#disconnected)
- [frameReceived(quint32, const QByteArray &)](sonic-ipc-connection.md#frameReceived)
- [peerCredentials() const : std::optional\<Sonic::Ipc::Connection::PeerCredentials\>](sonic-ipc-connection.md#peerCredentials)
- [protocolError(const QString &)](sonic-ipc-connection.md#protocolError)
- [protocolVersion() const : quint16](sonic-ipc-connection.md#protocolVersion)
- [send(quint32, QByteArrayView) : bool](sonic-ipc-connection.md#send)
- [sendBlocking(quint32, QByteArrayView, int) : bool](sonic-ipc-connection.md#sendBlocking)
- [socket() const : QLocalSocket \*](sonic-ipc-connection.md#socket)
- [versionRejected(quint16)](sonic-ipc-connection.md#versionRejected)
- [waitForFrame(int) : std::optional\<Sonic::Ipc::Frame\>](sonic-ipc-connection.md#waitForFrame)

Sonic::Ipc::Connection also inherits the members of [QObject](https://doc.qt.io/qt-6/qobject-members.html).
