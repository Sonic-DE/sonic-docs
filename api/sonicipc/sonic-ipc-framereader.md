---
title: "Sonic::Ipc::FrameReader Class"
description: "Splits a byte stream into frames."
---

# Sonic::Ipc::FrameReader Class

Splits a byte stream into frames. [More...](#details)

- **Header:** `#include <Sonic/Ipc/FrameReader>`
- **CMake:** `find_package(SonicIpc REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Sonic::Ipc)`

[List of all members, including inherited members](sonic-ipc-framereader-members.md)

## Public Types

- [enum FrameReader::Error](#Error-enum)

## Public Functions

- [FrameReader(quint16 expectedProtocol, qint64 maxPayload = defaultMaxPayload)](#FrameReader)
- [Sonic::Ipc::FrameReader::Error error() const](#error)
- [QString errorString() const](#errorString)
- [void feed(QByteArrayView data)](#feed)
- [std::optional\<Sonic::Ipc::Frame\> next()](#next)
- [quint16 peerProtocolVersion() const](#peerProtocolVersion)

## Detailed Description {#details}

The payload length is checked as soon as the header is complete, before any payload is buffered. After an error the reader stays in error; the caller closes the connection.

## Member Type Documentation {#member-type-documentation}

### enum FrameReader::Error {#Error-enum}

What the reader rejected.

| Constant | Value | Description |
| --- | --- | --- |
| `Sonic::Ipc::FrameReader::Error::None` | `0` | No error. |
| `Sonic::Ipc::FrameReader::Error::BadMagic` | `1` | The data doesn't start with [frameMagic](sonic-ipc.md#frameMagic-var): not a Sonic IPC peer. |
| `Sonic::Ipc::FrameReader::Error::BadFormatVersion` | `2` | An unsupported frame format. |
| `Sonic::Ipc::FrameReader::Error::ProtocolMismatch` | `3` | The peer speaks another application protocol version. |
| `Sonic::Ipc::FrameReader::Error::TooLarge` | `4` | The payload is larger than the limit. |
| `Sonic::Ipc::FrameReader::Error::BadChecksum` | `5` | The payload doesn't match its CRC-32. |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] FrameReader::FrameReader(quint16 *expectedProtocol*, qint64 *maxPayload* = defaultMaxPayload) {#FrameReader}

Creates a reader for application protocol `expectedProtocol` that rejects payloads larger than `maxPayload` bytes.

### Sonic::Ipc::FrameReader::Error FrameReader::error() const {#error}

What the reader rejected, or [Error::None](sonic-ipc-framereader.md#Error-enum).

### QString FrameReader::errorString() const {#errorString}

A description of [error](sonic-ipc-framereader.md#error)().

### void FrameReader::feed(QByteArrayView *data*) {#feed}

Appends `data` received from the stream.

### std::optional\<Sonic::Ipc::Frame\> FrameReader::next() {#next}

The next complete frame; nothing while a frame is incomplete or after an error.

### quint16 FrameReader::peerProtocolVersion() const {#peerProtocolVersion}

The protocol version in the last header read; names the peer's version after [ProtocolMismatch](sonic-ipc-framereader.md#Error-enum).
