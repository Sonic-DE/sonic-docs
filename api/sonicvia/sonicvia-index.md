---
title: "Sonic VIA"
description: "Lighting control for QMK keyboards over the VIA protocol."
---

# Sonic VIA

Lighting control for QMK keyboards over the VIA protocol.

Sonic VIA implements the QMK [VIA](https://www.caniusevia.com/) HID keyboard protocol for RGB lighting control.

- [ViaDiscovery](viadiscovery.md) lists VIA keyboards (HID usage page 0xff60) without opening them.
- [ViaDevice](viadevice.md) gives blocking access to one keyboard.
- [ViaProtocol](viaprotocol.md) sends the lighting commands, encoded for the device's protocol version (VIA V3, 11 and later, or legacy).
- [ViaCommand](viacommand.md) builds single VIA commands.

Without hidapi at build time, the library is a stub: discovery finds no keyboards and devices don't open.

## Using the Module {#using-the-module}

### Building with CMake {#building-with-cmake}

Use the `find_package()` command to locate the [SonicVia](sonicvia-module.md) package and link against its target:

```cpp
find_package(SonicVia REQUIRED)
target_link_libraries(mytarget PRIVATE SonicVia::SonicVia)
```

## API Reference {#api-reference}

- [Sonic VIA C++ Classes](sonicvia-module.md)
