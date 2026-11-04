---
title: "Sonic::Ipc::Connection::PeerCredentials Struct"
description: "The process at the other end of a connection."
---

# Sonic::Ipc::Connection::PeerCredentials Struct

The process at the other end of a connection. [More...](#details)

- **Header:** `#include <Sonic/Ipc/Connection>`
- **CMake:** `find_package(SonicIpc REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Sonic::Ipc)`

[List of all members, including inherited members](sonic-ipc-connection-peercredentials-members.md)

## Detailed Description {#details}

## Member Variable Documentation {#member-variable-documentation}

### qint64 PeerCredentials::gid {#gid-var}

The peer's group ID.

### qint64 PeerCredentials::pid {#pid-var}

The peer's process ID; -1 where the platform doesn't report it (BSD).

### qint64 PeerCredentials::uid {#uid-var}

The peer's user ID.
