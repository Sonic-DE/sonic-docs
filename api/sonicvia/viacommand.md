---
title: "ViaCommand Class"
description: "One VIA command and its payload."
---

# ViaCommand Class

One VIA command and its payload. [More...](#details)

- **Header:** `#include <via/viacommand.h>`
- **CMake:** `find_package(SonicVia REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE SonicVia::SonicVia)`

[List of all members, including inherited members](viacommand-members.md)

## Public Functions

- [ViaCommand(ViaCommandId commandId, const QByteArray &payload = QByteArray())](#ViaCommand)
- [ViaCommandId commandId() const](#commandId)
- [QByteArray payload() const](#payload)
- [QByteArray toReport() const](#toReport)

## Static Public Members

- [ViaCommand customGetValue(LightingChannel channel, RgbValueId valueId)](#customGetValue)
- [ViaCommand customSave()](#customSave)
- [ViaCommand customSetValue(LightingChannel channel, RgbValueId valueId, const QByteArray &value)](#customSetValue)
- [ViaCommand getProtocolVersion()](#getProtocolVersion)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] ViaCommand::ViaCommand(ViaCommandId *commandId*, const QByteArray &*payload* = QByteArray()) {#ViaCommand}

Creates the command `commandId` with `payload`, truncated to 31 bytes.

### ViaCommandId ViaCommand::commandId() const {#commandId}

The command's ID.

### \[static\] ViaCommand ViaCommand::customGetValue(LightingChannel *channel*, RgbValueId *valueId*) {#customGetValue}

Reads `valueId` on `channel`. Payload: \[channel, valueId\].

> **Note:** This encodes the V3 scheme (protocol 11 and later) only; see [customSetValue](viacommand.md#customSetValue)().

### \[static\] ViaCommand ViaCommand::customSave() {#customSave}

Saves the lighting settings on the device.

### \[static\] ViaCommand ViaCommand::customSetValue(LightingChannel *channel*, RgbValueId *valueId*, const QByteArray &*value*) {#customSetValue}

Sets `valueId` on `channel` to the bytes `value`. Payload: \[channel, valueId, value...\].

> **Note:** This encodes the V3 scheme (protocol 11 and later) only. [ViaProtocol](viaprotocol.md) constructs the legacy payload (\[valueId(0x80-0x83), value...\]) directly; don't use this for legacy devices.

### \[static\] ViaCommand ViaCommand::getProtocolVersion() {#getProtocolVersion}

The command that asks for the device's VIA protocol version.

### QByteArray ViaCommand::payload() const {#payload}

The command's payload.

### QByteArray ViaCommand::toReport() const {#toReport}

Returns the 33-byte HID report: \[0x00, [commandId](viacommand.md#commandId), payload, zero-padded to 33\].

## Related Non-Members {#related-non-members}

### enum LightingChannel {#LightingChannel-enum}

The keyboard's lighting system.

| Constant | Value | Description |
| --- | --- | --- |
| `ViaCommand::LightingChannel::QmkRgblight` | `0x02` | QMK RGB Light. |
| `ViaCommand::LightingChannel::QmkRgbMatrix` | `0x03` | QMK RGB Matrix. |

### enum RgbValueId {#RgbValueId-enum}

A lighting value.

| Constant | Value | Description |
| --- | --- | --- |
| `ViaCommand::RgbValueId::Brightness` | `0x01` | The brightness. |
| `ViaCommand::RgbValueId::Effect` | `0x02` | The lighting effect. |
| `ViaCommand::RgbValueId::EffectSpeed` | `0x03` | The effect's speed. |
| `ViaCommand::RgbValueId::Color` | `0x04` | The color, as hue and saturation. |

### enum ViaCommandId {#ViaCommandId-enum}

The VIA command IDs this library sends.

| Constant | Value | Description |
| --- | --- | --- |
| `ViaCommand::ViaCommandId::GetProtocolVersion` | `0x01` | Asks for the device's VIA protocol version. |
| `ViaCommand::ViaCommandId::CustomSetValue` | `0x07` | Sets a lighting value. |
| `ViaCommand::ViaCommandId::CustomGetValue` | `0x08` | Reads a lighting value. |
| `ViaCommand::ViaCommandId::CustomSave` | `0x09` | Saves the lighting settings on the device. |

### const quint16 kProtocolV3 {#kProtocolV3-var}

VIA protocol version 11, where the lighting command encoding changes. Devices reporting less use the legacy scheme: single-byte value IDs 0x80-0x83, no channel byte, RGB Light only. From 11 on, commands carry the channel and value IDs 1-4, and RGB Matrix is available.

### const quint16 kProtocolAlpha {#kProtocolAlpha-var}

VIA protocol version 7, "alpha".

### const quint16 kProtocolBeta {#kProtocolBeta-var}

VIA protocol version 8, "beta".

### const quint16 kProtocolGamma {#kProtocolGamma-var}

VIA protocol version 9, "gamma", which many keyboards report.

### const int kViaReportSize {#kViaReportSize-var}

Size of a VIA HID report (leading 0x00 report id + command id + 31 data bytes).
