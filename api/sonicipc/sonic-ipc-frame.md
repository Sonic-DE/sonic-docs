---
title: "Sonic::Ipc::Frame Struct"
description: "One message: the application's type and its payload."
---

# Sonic::Ipc::Frame Struct

One message: the application's type and its payload. [More...](#details)

- **Header:** `#include <Sonic/Ipc/Frame>`
- **CMake:** `find_package(SonicIpc REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Sonic::Ipc)`

[List of all members, including inherited members](sonic-ipc-frame-members.md)

## Detailed Description {#details}

## Member Variable Documentation {#member-variable-documentation}

### const quint32 Frame::VersionRejected {#VersionRejected-var}

Reserved for the library: tells a peer its protocol version was rejected. The payload is the sender's quint16 version.

### QByteArray Frame::payload {#payload-var}

The message's bytes.

### quint32 Frame::type {#type-var}

The application's message type.
