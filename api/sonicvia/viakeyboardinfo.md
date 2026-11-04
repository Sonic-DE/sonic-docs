---
title: "ViaKeyboardInfo Struct"
description: "A VIA keyboard found by ViaDiscovery."
---

# ViaKeyboardInfo Struct

A VIA keyboard found by [ViaDiscovery](viadiscovery.md). [More...](#details)

- **Header:** `#include <via/viadiscovery.h>`
- **CMake:** `find_package(SonicVia REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE SonicVia::SonicVia)`

[List of all members, including inherited members](viakeyboardinfo-members.md)

## Detailed Description {#details}

## Member Variable Documentation {#member-variable-documentation}

### QString ViaKeyboardInfo::manufacturer {#manufacturer-var}

The manufacturer string.

### QString ViaKeyboardInfo::path {#path-var}

The HID path, for [ViaDevice](viadevice.md).

### quint16 ViaKeyboardInfo::pid {#pid-var}

The USB product ID.

### QString ViaKeyboardInfo::product {#product-var}

The product string.

### quint16 ViaKeyboardInfo::vid {#vid-var}

The USB vendor ID.
