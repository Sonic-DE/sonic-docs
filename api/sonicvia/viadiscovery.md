---
title: "ViaDiscovery Class"
description: "Finds VIA keyboards."
---

# ViaDiscovery Class

Finds VIA keyboards. [More...](#details)

- **Header:** `#include <via/viadiscovery.h>`
- **CMake:** `find_package(SonicVia REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE SonicVia::SonicVia)`

[List of all members, including inherited members](viadiscovery-members.md)

## Static Public Members

- [QVector\<ViaKeyboardInfo\> discoverViaKeyboards()](#discoverViaKeyboards)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[static\] QVector\<ViaKeyboardInfo\> ViaDiscovery::discoverViaKeyboards() {#discoverViaKeyboards}

Lists all VIA keyboards (usage page 0xff60). Pure enumeration: does NOT probe-open. Empty when built as a stub or when no VIA device is present. Access is checked by the caller via [ViaDevice::open](viadevice.md#open)().
