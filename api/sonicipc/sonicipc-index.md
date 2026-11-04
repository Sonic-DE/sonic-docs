---
title: "Sonic IPC"
description: "Framed peer-to-peer messages over local sockets."
---

# Sonic IPC

Framed peer-to-peer messages over local sockets.

Sonic IPC is a small inter-process communication library for SonicDE. It is built on Unix domain sockets ([QLocalServer](https://doc.qt.io/qt-6/qlocalserver.html) / [QLocalSocket](https://doc.qt.io/qt-6/qlocalsocket.html)). Components can talk to each other directly, peer to peer, without a message bus, so D-Bus becomes an option rather than a requirement.

- [Sonic::Ipc::Server](sonic-ipc-server.md) listens on a local socket and wraps each client in a [Sonic::Ipc::Connection](sonic-ipc-connection.md).
- [Sonic::Ipc::Client](sonic-ipc-client.md) connects to a server, optionally reconnecting across restarts, or sends one blocking request.
- [Sonic::Ipc::Connection](sonic-ipc-connection.md) sends and receives frames, and tells the uid, gid and pid of the process at the other end.

Each frame carries the application's protocol version and a message type. Damaged, oversized or foreign data is rejected and the connection closed; a peer speaking another protocol version is told so first. Frame type 0xFFFFFFFF is reserved for the library.

```cpp
constexpr quint16 protocolVersion = 1;

auto *server = new Sonic::Ipc::Server(this);
server->listen(Sonic::Ipc::Server::userSocketPath(QStringLiteral("my-service.sock")),
               Sonic::Ipc::Server::Access::User, protocolVersion);
connect(server, &Sonic::Ipc::Server::newConnection, this, [](Sonic::Ipc::Connection *connection) {
    QObject::connect(connection, &Sonic::Ipc::Connection::frameReceived, connection,
                     [connection](quint32 type, const QByteArray &payload) {
                         connection->send(type, payload); // echo
                     });
});
```

## Using the Module {#using-the-module}

### Building with CMake {#building-with-cmake}

Use the `find_package()` command to locate the [SonicIpc](sonicipc-module.md) package and link against its target:

```cpp
find_package(SonicIpc REQUIRED)
target_link_libraries(mytarget PRIVATE Sonic::Ipc)
```

## API Reference {#api-reference}

- [Sonic IPC C++ Classes](sonicipc-module.md)
