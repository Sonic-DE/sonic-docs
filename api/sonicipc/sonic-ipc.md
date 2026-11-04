---
title: "Sonic::Ipc Namespace"
description: "Framed peer-to-peer messages over local sockets."
---

# Sonic::Ipc Namespace

Framed peer-to-peer messages over local sockets. [More...](#details)

- **Header:** `#include <Sonic/Ipc/Frame>`
- **CMake:** `find_package(SonicIpc REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Sonic::Ipc)`

## Detailed Description {#details}

The Sonic IPC frame. Big-endian header of 20 bytes, then the payload:

| Type | Field |
| --- | --- |
| quint32 | magic 0x534F4E43 |
| quint16 | frame format 1 |
| quint16 | application protocol |
| quint32 | type |
| quint32 | payload length |
| quint32 | CRC-32 of the payload |

## Namespaces {#namespaces}

### namespace Ipc::Crc32

## Classes {#classes}

### class [Client](sonic-ipc-client.md)

Connects to a Server.

### class [Connection](sonic-ipc-connection.md)

One framed connection over a [QLocalSocket](https://doc.qt.io/qt-6/qlocalsocket.html).

### struct [Ipc::Frame](sonic-ipc-frame.md)

### class [FrameReader](sonic-ipc-framereader.md)

Splits a byte stream into frames.

### class [Server](sonic-ipc-server.md)

Listens on a local socket.

## Variable Documentation {#variable-documentation}

### const qint64 Ipc::defaultMaxPayload {#defaultMaxPayload-var}

The largest payload accepted unless a caller sets another limit: 16 MiB.

### const quint16 Ipc::frameFormatVersion {#frameFormatVersion-var}

The frame format this library writes and reads.

### const qsizetype Ipc::frameHeaderSize {#frameHeaderSize-var}

The header's size in bytes.

### const quint32 Ipc::frameMagic {#frameMagic-var}

The first four bytes of every frame, "SONC".

## Function Documentation {#function-documentation}

### QByteArray Ipc::encodeFrame(quint32 *type*, QByteArrayView *payload*, quint16 *protocolVersion*) {#encodeFrame}

The frame bytes for `payload` of `type` in application protocol `protocolVersion`; empty, with a warning, for the reserved [Frame::VersionRejected](sonic-ipc-frame.md#VersionRejected-var) type.
