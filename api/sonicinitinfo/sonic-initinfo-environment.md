---
title: "Sonic::InitInfo::Environment Struct"
description: "Where to look; the defaults describe the live system."
---

# Sonic::InitInfo::Environment Struct

Where to look; the defaults describe the live system. [More...](#details)

- **Header:** `#include <Sonic/InitInfo/InitInfo>`
- **CMake:** `find_package(SonicInitInfo REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Sonic::InitInfo)`

[List of all members, including inherited members](sonic-initinfo-environment-members.md)

## Detailed Description {#details}

Tests point these at a fake tree.

## Member Variable Documentation {#member-variable-documentation}

### QString Environment::fsRoot {#fsRoot-var}

Prefix for /etc, /sbin and /run.

### QString Environment::procRoot {#procRoot-var}

The proc file system.

### bool Environment::useDBus {#useDBus-var}

Whether [seatManager](sonic-initinfo.md#seatManager)() may also ask the system bus, when the library is built with Qt D-Bus.
