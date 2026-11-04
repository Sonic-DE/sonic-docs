---
title: "ViaHsv Struct"
description: "Result of converting a QColor to VIA's single-byte HSV components."
---

# ViaHsv Struct

Result of converting a [QColor](https://doc.qt.io/qt-6/qcolor.html) to VIA's single-byte HSV components. [More...](#details)

- **Header:** `#include <via/viaprotocol.h>`
- **CMake:** `find_package(SonicVia REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE SonicVia::SonicVia)`

[List of all members, including inherited members](viahsv-members.md)

## Detailed Description {#details}

## Member Variable Documentation {#member-variable-documentation}

### quint8 ViaHsv::brightness {#brightness-var}

The brightness, 0-255.

### quint8 ViaHsv::hue {#hue-var}

The hue, 0-255.

### quint8 ViaHsv::saturation {#saturation-var}

The saturation, 0-255.
