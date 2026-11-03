---
title: "Solid::OpticalDisc Class"
description: "This device interface is available on optical discs."
---

# Solid::OpticalDisc Class

This device interface is available on optical discs. [More...](#details)

- **Header:** `#include <Solid/OpticalDisc>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Solid)`  
  `target_link_libraries(mytarget PRIVATE KF6::Solid)`
- **Inherits:** [Solid::StorageVolume](solid-storagevolume.md)

[List of all members, including inherited members](solid-opticaldisc-members.md)

## Public Types

- [enum OpticalDisc::ContentType](#ContentType-enum)
- [enum OpticalDisc::DiscType](#DiscType-enum)

## Properties

- [\[read-only\] appendable : bool](#appendable-prop)
- [\[read-only\] availableContent : ContentTypes](#availableContent-prop)
- [\[read-only\] blank : bool](#blank-prop)
- [\[read-only\] capacity : qulonglong](#capacity-prop)
- [\[read-only\] discType : DiscType](#discType-prop)
- [\[read-only\] rewritable : bool](#rewritable-prop)

## Public Functions

- [Solid::OpticalDisc::ContentTypes availableContent() const](#availableContent)
- [qulonglong capacity() const](#capacity)
- [Solid::OpticalDisc::DiscType discType() const](#discType)
- [bool isAppendable() const](#isAppendable)
- [bool isBlank() const](#isBlank)
- [bool isRewritable() const](#isRewritable)

## Static Public Members

- [Solid::DeviceInterface::Type deviceInterfaceType()](#deviceInterfaceType)

## Detailed Description {#details}

An optical disc is a volume that can be inserted in CD-R\*,DVD\*,Blu-Ray,HD-DVD drives.

Commonly used in conjunction with [OpticalDrive](solid-opticaldrive.md).

## Member Type Documentation {#member-type-documentation}

### enum OpticalDisc::ContentType {#ContentType-enum}

**flags OpticalDisc::ContentTypes**

This enum type defines the type of content available in an optical disc.

| Constant | Value |   |
| --- | --- | --- |
| `Solid::OpticalDisc::NoContent` | `0x00` |   |
| `Solid::OpticalDisc::Audio` | `0x01` | A disc containing audio |
| `Solid::OpticalDisc::Data` | `0x02` | A disc containing data |
| `Solid::OpticalDisc::VideoCd` | `0x04` | A Video Compact Disc (VCD) |
| `Solid::OpticalDisc::SuperVideoCd` | `0x08` | A Super Video Compact Disc (SVCD) |
| `Solid::OpticalDisc::VideoDvd` | `0x10` | A Video Digital Versatile Disc (DVD-Video) |
| `Solid::OpticalDisc::VideoBluRay` | `0x20` |   |

The `ContentTypes` type is a typedef for `QFlags<ContentType>. `It stores an OR combination of `ContentType` values.

### enum OpticalDisc::DiscType {#DiscType-enum}

This enum type defines the type of optical disc it can be.

| Constant | Value | Description |
| --- | --- | --- |
| `Solid::OpticalDisc::UnknownDiscType` | `-1` | An undetermined disc type |
| `Solid::OpticalDisc::CdRom` | `0` | A Compact Disc Read-Only Memory (CD-ROM) |
| `Solid::OpticalDisc::CdRecordable` | `1` | A Compact Disc Recordable (CD-R) |
| `Solid::OpticalDisc::CdRewritable` | `2` | A Compact Disc ReWritable (CD-RW) |
| `Solid::OpticalDisc::DvdRom` | `3` | A Digital Versatile Disc Read-Only Memory (DVD-ROM) |
| `Solid::OpticalDisc::DvdRam` | `4` | A Digital Versatile Disc Random Access Memory (DVD-RAM) |
| `Solid::OpticalDisc::DvdRecordable` | `5` | A Digital Versatile Disc Recordable (DVD-R) |
| `Solid::OpticalDisc::DvdRewritable` | `6` | A Digital Versatile Disc ReWritable (DVD-RW) |
| `Solid::OpticalDisc::DvdPlusRecordable` | `7` | A Digital Versatile Disc Recordable (DVD+R) |
| `Solid::OpticalDisc::DvdPlusRewritable` | `8` | A Digital Versatile Disc ReWritable (DVD+RW) |
| `Solid::OpticalDisc::DvdPlusRecordableDuallayer` | `9` | A Digital Versatile Disc Recordable Dual-Layer (DVD+R DL) |
| `Solid::OpticalDisc::DvdPlusRewritableDuallayer` | `10` | A Digital Versatile Disc ReWritable Dual-Layer (DVD+RW DL) |
| `Solid::OpticalDisc::BluRayRom` | `11` | A Blu-ray Disc (BD) |
| `Solid::OpticalDisc::BluRayRecordable` | `12` | A Blu-ray Disc Recordable (BD-R) |
| `Solid::OpticalDisc::BluRayRewritable` | `13` | A Blu-ray Disc (BD-RE) |
| `Solid::OpticalDisc::HdDvdRom` | `14` | : A High Density Digital Versatile Disc (HD DVD) |
| `Solid::OpticalDisc::HdDvdRecordable` | `15` | A High Density Digital Versatile Disc Recordable (HD DVD-R) |
| `Solid::OpticalDisc::HdDvdRewritable` | `16` | A High Density Digital Versatile Disc ReWritable (HD DVD-RW) |

## Property Documentation {#property-documentation}

### \[read-only\] appendable : bool {#appendable-prop}

**Access functions:**

- `bool` **[isAppendable](solid-opticaldisc.md#isAppendable)**() const

### \[read-only\] availableContent : ContentTypes {#availableContent-prop}

**Access functions:**

- `Solid::OpticalDisc::ContentTypes` **[availableContent](solid-opticaldisc.md#availableContent)**() const

### \[read-only\] blank : bool {#blank-prop}

**Access functions:**

- `bool` **[isBlank](solid-opticaldisc.md#isBlank)**() const

### \[read-only\] capacity : qulonglong {#capacity-prop}

**Access functions:**

- `qulonglong` **[capacity](solid-opticaldisc.md#capacity)**() const

### \[read-only\] discType : DiscType {#discType-prop}

**Access functions:**

- `Solid::OpticalDisc::DiscType` **[discType](solid-opticaldisc.md#discType)**() const

### \[read-only\] rewritable : bool {#rewritable-prop}

**Access functions:**

- `bool` **[isRewritable](solid-opticaldisc.md#isRewritable)**() const

## Member Function Documentation {#member-function-documentation}

### Solid::OpticalDisc::ContentTypes OpticalDisc::availableContent() const {#availableContent}

Returns the flag set indicating the content types this disc contains (audio, video, data...).

> **Note:** Getter function for property [availableContent](solid-opticaldisc.md#availableContent-prop).

*See also* [Solid::OpticalDisc::ContentType](solid-index.md)

### qulonglong OpticalDisc::capacity() const {#capacity}

Returns the disc capacity in bytes (the maximum size a volume could have on this disc).

> **Note:** Getter function for property [capacity](solid-opticaldisc.md#capacity-prop).

### \[static\] Solid::DeviceInterface::Type OpticalDisc::deviceInterfaceType() {#deviceInterfaceType}

Returns the [Solid::DeviceInterface::Type](solid-deviceinterface.md#Type-enum) of the [OpticalDisc](solid-opticaldisc.md) device interface.

*See also* [Solid::DeviceInterface::Type](solid-index.md)

### Solid::OpticalDisc::DiscType OpticalDisc::discType() const {#discType}

Returns the disc type (cdr, cdrw...).

> **Note:** Getter function for property [discType](solid-opticaldisc.md#discType-prop).

### bool OpticalDisc::isAppendable() const {#isAppendable}

Returns whether it's possible to append additional data to the disc.

> **Note:** Getter function for property [appendable](solid-opticaldisc.md#appendable-prop).

### bool OpticalDisc::isBlank() const {#isBlank}

Returns whether the disc is blank.

> **Note:** Getter function for property [blank](solid-opticaldisc.md#blank-prop).

### bool OpticalDisc::isRewritable() const {#isRewritable}

Indicates if the disc is rewritable (you can write on it several times).

> **Note:** Getter function for property [rewritable](solid-opticaldisc.md#rewritable-prop).
