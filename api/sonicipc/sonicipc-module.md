---
title: "Sonic IPC C++ Classes"
description: "Framed peer-to-peer messages over local sockets."
---

# Sonic IPC C++ Classes

Framed peer-to-peer messages over local sockets. [More...](#details)

## Namespaces {#namespaces}

- [Sonic::Ipc](sonic-ipc.md): Framed peer-to-peer messages over local sockets.
- [Sonic::Ipc::Crc32](sonic-ipc-crc32.md): The checksum of frame payloads.

## Classes {#classes}

- [Sonic::Ipc::Client](sonic-ipc-client.md): Connects to a Server.
- [Sonic::Ipc::Connection](sonic-ipc-connection.md): One framed connection over a QLocalSocket.
- [Sonic::Ipc::Connection::PeerCredentials](sonic-ipc-connection-peercredentials.md): The process at the other end of a connection.
- [Sonic::Ipc::Frame](sonic-ipc-frame.md): One message: the application's type and its payload.
- [Sonic::Ipc::FrameReader](sonic-ipc-framereader.md): Splits a byte stream into frames.
- [Sonic::Ipc::Server](sonic-ipc-server.md): Listens on a local socket.

## Detailed Description {#details}
