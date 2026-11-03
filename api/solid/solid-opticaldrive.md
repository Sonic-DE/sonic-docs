---
title: "Solid::OpticalDrive Class"
description: "This device interface is available on CD-R,DVD,Blu-Ray,HD-DVD drives."
---

# Solid::OpticalDrive Class

This device interface is available on CD-R\*,DVD\*,Blu-Ray,HD-DVD drives. [More...](#details)

- **Header:** `#include <Solid/OpticalDrive>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Solid)`  
  `target_link_libraries(mytarget PRIVATE KF6::Solid)`
- **Inherits:** [Solid::StorageDrive](solid-storagedrive.md)

[List of all members, including inherited members](solid-opticaldrive-members.md)

## Public Types

- [enum OpticalDrive::MediumType](#MediumType-enum)

## Properties

- [\[read-only\] readSpeed : int](#readSpeed-prop)
- [\[read-only\] supportedMedia : MediumTypes](#supportedMedia-prop)
- [\[read-only\] writeSpeed : int](#writeSpeed-prop)
- [\[read-only\] writeSpeeds : QList\<int\>](#writeSpeeds-prop)

## Public Functions

- [bool eject()](#eject)
- [int readSpeed() const](#readSpeed)
- [Solid::OpticalDrive::MediumTypes supportedMedia() const](#supportedMedia)
- [int writeSpeed() const](#writeSpeed)
- [QList\<int\> writeSpeeds() const](#writeSpeeds)

## Signals

- [void ejectDone(Solid::ErrorType error, QVariant errorData, const QString &udi)](#ejectDone)
- [void ejectPressed(const QString &udi)](#ejectPressed)
- [void ejectRequested(const QString &udi)](#ejectRequested)

## Static Public Members

- [Solid::DeviceInterface::Type deviceInterfaceType()](#deviceInterfaceType)

## Detailed Description {#details}

An [OpticalDrive](solid-opticaldrive.md) is a storage that can handle optical discs.

Commonly used in conjunction with OpticalDisk.

## Member Type Documentation {#member-type-documentation}

### enum OpticalDrive::MediumType {#MediumType-enum}

**flags OpticalDrive::MediumTypes**

This enum type defines the type of medium an optical drive supports.

| Constant | Value |   |
| --- | --- | --- |
| `Solid::OpticalDrive::UnknownMediumType` | `0x00000` |   |
| `Solid::OpticalDrive::Cdr` | `0x00001` | A Recordable Compact Disc (CD-R) |
| `Solid::OpticalDrive::Cdrw` | `0x00002` | A ReWritable Compact Disc (CD-RW) |
| `Solid::OpticalDrive::Dvd` | `0x00004` | A Digital Versatile Disc (DVD) |
| `Solid::OpticalDrive::Dvdr` | `0x00008` | A Recordable Digital Versatile Disc (DVD-R) |
| `Solid::OpticalDrive::Dvdrw` | `0x00010` | A ReWritable Digital Versatile Disc (DVD-RW) |
| `Solid::OpticalDrive::Dvdram` | `0x00020` | A Random Access Memory Digital Versatile Disc (DVD-RAM) |
| `Solid::OpticalDrive::Dvdplusr` | `0x00040` | A Recordable Digital Versatile Disc (DVD+R) |
| `Solid::OpticalDrive::Dvdplusrw` | `0x00080` | A ReWritable Digital Versatile Disc (DVD+RW) |
| `Solid::OpticalDrive::Dvdplusdl` | `0x00100` | A Dual Layer Digital Versatile Disc (DVD+R DL) |
| `Solid::OpticalDrive::Dvdplusdlrw` | `0x00200` | A Dual Layer Digital Versatile Disc (DVD+RW DL) |
| `Solid::OpticalDrive::Bd` | `0x00400` | A Blu-ray Disc (BD) |
| `Solid::OpticalDrive::Bdr` | `0x00800` | A Blu-ray Disc Recordable (BD-R) |
| `Solid::OpticalDrive::Bdre` | `0x01000` | A Blu-ray Disc Recordable and Eraseable (BD-RE) |
| `Solid::OpticalDrive::HdDvd` | `0x02000` | A High Density Digital Versatile Disc (HD DVD) |
| `Solid::OpticalDrive::HdDvdr` | `0x04000` | A High Density Digital Versatile Disc Recordable (HD DVD-R) |
| `Solid::OpticalDrive::HdDvdrw` | `0x08000` | A High Density Digital Versatile Disc ReWritable (HD DVD-RW) |

The `MediumTypes` type is a typedef for `QFlags<MediumType>. `It stores an OR combination of `MediumType` values.

## Property Documentation {#property-documentation}

### \[read-only\] readSpeed : int {#readSpeed-prop}

**Access functions:**

- `int` **[readSpeed](solid-opticaldrive.md#readSpeed)**() const

### \[read-only\] supportedMedia : MediumTypes {#supportedMedia-prop}

**Access functions:**

- `Solid::OpticalDrive::MediumTypes` **[supportedMedia](solid-opticaldrive.md#supportedMedia)**() const

### \[read-only\] writeSpeed : int {#writeSpeed-prop}

**Access functions:**

- `int` **[writeSpeed](solid-opticaldrive.md#writeSpeed)**() const

### \[read-only\] writeSpeeds : QList\<int\> {#writeSpeeds-prop}

**Access functions:**

- `QList`\<`int`\> **[writeSpeeds](solid-opticaldrive.md#writeSpeeds)**() const

## Member Function Documentation {#member-function-documentation}

### \[static\] Solid::DeviceInterface::Type OpticalDrive::deviceInterfaceType() {#deviceInterfaceType}

Returns the [Solid::DeviceInterface::Type](solid-deviceinterface.md#Type-enum) of the [OpticalDrive](solid-opticaldrive.md) device interface.

*See also* [Solid::DeviceInterface::Type](solid-index.md)

### bool OpticalDrive::eject() {#eject}

Ejects any disc that could be contained in this drive. If this drive is empty but has a tray it'll be opened.

Returns the status of the eject operation.

### \[signal\] void OpticalDrive::ejectDone(Solid::ErrorType *error*, QVariant *errorData*, const QString &*udi*) {#ejectDone}

This signal is emitted when the attempted eject process on the drive with the given `udi` is completed.

The signal might be spontaneous, i.e. it can be triggered by another process.

Returns an `error` followed by additional `errorData` information, if any.

### \[signal\] void OpticalDrive::ejectPressed(const QString &*udi*) {#ejectPressed}

This signal is emitted when the eject button is pressed on the drive with the given `udi`.

Please note that some (broken) drives don't report this event.

### \[signal\] void OpticalDrive::ejectRequested(const QString &*udi*) {#ejectRequested}

This signal is emitted when eject on the drive with the given `udi` is requested.

The signal might be spontaneous, i.e. it can be triggered by another process.

### int OpticalDrive::readSpeed() const {#readSpeed}

Returns the maximum read speed of this drive in kilobytes per second.

> **Note:** Getter function for property [readSpeed](solid-opticaldrive.md#readSpeed-prop).

### Solid::OpticalDrive::MediumTypes OpticalDrive::supportedMedia() const {#supportedMedia}

Returns the flag set indicating the medium types this drive supports.

> **Note:** Getter function for property [supportedMedia](solid-opticaldrive.md#supportedMedia-prop).

### int OpticalDrive::writeSpeed() const {#writeSpeed}

Returns the maximum write speed of this drive in kilobytes per second.

> **Note:** Getter function for property [writeSpeed](solid-opticaldrive.md#writeSpeed-prop).

### QList\<int\> OpticalDrive::writeSpeeds() const {#writeSpeeds}

Returns the list of supported write speeds of this drive in kilobytes per second.

> **Note:** Getter function for property [writeSpeeds](solid-opticaldrive.md#writeSpeeds-prop).
