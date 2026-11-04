---
title: "ViaProtocol Class"
description: "The VIA lighting commands for one device."
---

# ViaProtocol Class

The VIA lighting commands for one device. [More...](#details)

- **Header:** `#include <via/viaprotocol.h>`
- **CMake:** `find_package(SonicVia REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE SonicVia::SonicVia)`

[List of all members, including inherited members](viaprotocol-members.md)

## Public Functions

- [ViaProtocol(ViaDevice &device, quint16 protocolVersion = kProtocolV3)](#ViaProtocol)
- [bool applyColor(const QColor &color)](#applyColor)
- [bool getEffect(LightingChannel channel, quint8 &outEffect)](#getEffect)
- [bool getLightingValue(LightingChannel channel, RgbValueId valueId, QByteArray &outValue)](#getLightingValue)
- [bool hasLightingSupport()](#hasLightingSupport)
- [quint16 protocolVersion() const](#protocolVersion)
- [bool saveSettings()](#saveSettings)
- [bool setBrightness(LightingChannel channel, quint8 brightness)](#setBrightness)
- [bool setColor(LightingChannel channel, quint8 hue, quint8 saturation)](#setColor)
- [bool setLightingValue(LightingChannel channel, RgbValueId valueId, const QByteArray &value)](#setLightingValue)

## Static Public Members

- [ViaHsv hsvFromColor(const QColor &color)](#hsvFromColor)
- [quint16 queryProtocolVersion(ViaDevice &device)](#queryProtocolVersion)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ViaProtocol::ViaProtocol(ViaDevice &*device*, quint16 *protocolVersion* = kProtocolV3) {#ViaProtocol}

Talks to `device`. `protocolVersion` selects the command encoding (V3 \>= [kProtocolV3](viacommand.md#kProtocolV3-var) vs legacy). Defaults to V3. Use [queryProtocolVersion](viaprotocol.md#queryProtocolVersion)(device) to obtain the device's actual version before constructing.

### bool ViaProtocol::applyColor(const QColor &*color*) {#applyColor}

Sets the device's lighting to `color`: try RGB Matrix (effect \> 0), fall back to RGB Light, otherwise return false. Returns false in stub mode.

### bool ViaProtocol::getEffect(LightingChannel *channel*, quint8 &*outEffect*) {#getEffect}

Reads the lighting effect on `channel` into `outEffect`.

### bool ViaProtocol::getLightingValue(LightingChannel *channel*, RgbValueId *valueId*, QByteArray &*outValue*) {#getLightingValue}

Reads `valueId` on `channel` into `outValue`, encoded as for [setLightingValue](viaprotocol.md#setLightingValue)(); false when the device doesn't support it or the response doesn't match.

### bool ViaProtocol::hasLightingSupport() {#hasLightingSupport}

Whether this device has lighting: true when the RGB Matrix channel responds (device returns a value, not 0xFF) OR the RGB Light channel responds, REGARDLESS of the effect value. This is intentionally more lenient than [applyColor](viaprotocol.md#applyColor)(), which requires effect \> 0. Returns false in stub mode.

### \[static\] ViaHsv ViaProtocol::hsvFromColor(const QColor &*color*) {#hsvFromColor}

Converts `color` to the VIA single-byte HSV. Returns a zeroed [ViaHsv](viahsv.md) for an invalid color.

### quint16 ViaProtocol::protocolVersion() const {#protocolVersion}

The protocol version that selects the command encoding.

### \[static\] quint16 ViaProtocol::queryProtocolVersion(ViaDevice &*device*) {#queryProtocolVersion}

Queries [GetProtocolVersion](viacommand.md#ViaCommandId-enum) on `device` and returns the big-endian u16 at response\[1\],\[2\] (verified: utils::shift\_to\_16\_bit(buffer\[1\], buffer\[2\])). Returns 0 on failure (the caller should then skip the device). Independent of the instance protocol version.

### bool ViaProtocol::saveSettings() {#saveSettings}

Saves the lighting settings on the device.

### bool ViaProtocol::setBrightness(LightingChannel *channel*, quint8 *brightness*) {#setBrightness}

Sets the brightness on `channel` to `brightness`.

### bool ViaProtocol::setColor(LightingChannel *channel*, quint8 *hue*, quint8 *saturation*) {#setColor}

Sets the color on `channel` to `hue` and `saturation`.

### bool ViaProtocol::setLightingValue(LightingChannel *channel*, RgbValueId *valueId*, const QByteArray &*value*) {#setLightingValue}

Sets `valueId` on `channel`. `value` is the raw value bytes (e.g. \[hue, sat\] for Color, \[brightness\] for Brightness). Encoding is protocol-version-aware: V3 uses \[channel, valueId(1-4), value\]; legacy (\< 11) uses rgblight-only \[valueId(0x80-0x83), value\] and rejects non-rgblight channels without HID. On success the device echoed the command; on unsupported (0xFF) or mismatch this returns false.
