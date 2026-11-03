---
title: "Solid::StorageDrive Class"
description: "This device interface is available on storage devices."
---

# Solid::StorageDrive Class

This device interface is available on storage devices. [More...](#details)

- **Header:** `#include <Solid/StorageDrive>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Solid)`  
  `target_link_libraries(mytarget PRIVATE KF6::Solid)`
- **Inherits:** [Solid::DeviceInterface](solid-deviceinterface.md)
- **Inherited By:** [Solid::OpticalDrive](solid-opticaldrive.md)

[List of all members, including inherited members](solid-storagedrive-members.md)

## Public Types

- [enum StorageDrive::Bus](#Bus-enum)
- [enum StorageDrive::DriveType](#DriveType-enum)

## Properties

- [\[read-only\] bus : Bus](#bus-prop)
- [\[read-only\] driveType : DriveType](#driveType-prop)
- [\[read-only\] hotpluggable : bool](#hotpluggable-prop)
- [\[read-only\] inUse : bool](#inUse-prop)
- [\[read-only\] removable : bool](#removable-prop)
- [\[read-only\] size : qulonglong](#size-prop)
- [\[read-only\] timeDetected : const QDateTime](#timeDetected-prop)
- [\[read-only\] timeMediaDetected : QDateTime](#timeMediaDetected-prop)

## Public Functions

- [Solid::StorageDrive::Bus bus() const](#bus)
- [Solid::StorageDrive::DriveType driveType() const](#driveType)
- [bool isHotpluggable() const](#isHotpluggable)
- [bool isInUse() const](#isInUse)
- [bool isRemovable() const](#isRemovable)
- [qulonglong size() const](#size)
- [QDateTime timeDetected() const](#timeDetected) (since 6.0)
- [QDateTime timeMediaDetected() const](#timeMediaDetected) (since 6.0)

## Static Public Members

- [Solid::DeviceInterface::Type deviceInterfaceType()](#deviceInterfaceType)

## Detailed Description {#details}

A storage is anything that can contain a set of volumes (card reader, hard disk, cdrom drive...). It's a particular kind of block device.

A [StorageDrive](solid-storagedrive.md) is commonly used in conjunction with [StorageVolume](solid-storagevolume.md) and [StorageAccess](solid-storageaccess.md).

| [StorageDrive](solid-storagedrive.md) | [StorageVolume](solid-storagevolume.md) | [StorageAccess](solid-storageaccess.md) |
| --- | --- | --- |
| drives | partition tables / filesystems | mount points / partitions |

It can be used to fetch a parent device of a [StorageVolume](solid-storagevolume.md) that is a [StorageDrive](solid-storagedrive.md) in order to check its properties, for example:

```cpp
const Solid::Device& dev = m_device;
if (dev.is<Solid::StorageVolume>() && dev.parent().is<Solid::StorageDrive>()) {
    auto parent = dev.parent().as<Solid::StorageDrive>();
    if (parent->isRemovable() || parent->isHotpluggable()) {
        usable = false;
    }

    const Solid::StorageVolume* volume = dev.as<Solid::StorageVolume>();
    if (volume->isIgnored() || volume->usage() != Solid::StorageVolume::FileSystem) {
        usable = false;
    }
}
```

## Member Type Documentation {#member-type-documentation}

### enum StorageDrive::Bus {#Bus-enum}

This enum type defines the type of bus a storage device is attached to.

| Constant | Value | Description |
| --- | --- | --- |
| `Solid::StorageDrive::Ide` | `0` | An Integrated Drive Electronics (IDE) bus, also known as ATA |
| `Solid::StorageDrive::Usb` | `1` | An Universal Serial Bus (USB) |
| `Solid::StorageDrive::Ieee1394` | `2` | An Ieee1394 bus, also known as Firewire |
| `Solid::StorageDrive::Scsi` | `3` | A Small Computer System Interface bus |
| `Solid::StorageDrive::Sata` | `4` | A Serial Advanced Technology Attachment (SATA) bus |
| `Solid::StorageDrive::Platform` | `5` | A legacy bus that is part of the underlying platform |

### enum StorageDrive::DriveType {#DriveType-enum}

This enum type defines the type of drive a storage device can be.

| Constant | Value | Description |
| --- | --- | --- |
| `Solid::StorageDrive::HardDisk` | `0` | A hard disk |
| `Solid::StorageDrive::CdromDrive` | `1` | An optical drive |
| `Solid::StorageDrive::Floppy` | `2` | A floppy disk drive |
| `Solid::StorageDrive::Tape` | `3` | A tape drive |
| `Solid::StorageDrive::CompactFlash` | `4` | A Compact Flash card reader |
| `Solid::StorageDrive::MemoryStick` | `5` | A Memory Stick card reader |
| `Solid::StorageDrive::SmartMedia` | `6` | A Smart Media card reader |
| `Solid::StorageDrive::SdMmc` | `7` | A SecureDigital/MultiMediaCard card reader |
| `Solid::StorageDrive::Xd` | `8` | A xD card reader |

## Property Documentation {#property-documentation}

### \[read-only\] bus : Bus {#bus-prop}

**Access functions:**

- `Solid::StorageDrive::Bus` **[bus](solid-storagedrive.md#bus)**() const

### \[read-only\] driveType : DriveType {#driveType-prop}

**Access functions:**

- `Solid::StorageDrive::DriveType` **[driveType](solid-storagedrive.md#driveType)**() const

### \[read-only\] hotpluggable : bool {#hotpluggable-prop}

**Access functions:**

- `bool` **[isHotpluggable](solid-storagedrive.md#isHotpluggable)**() const

### \[read-only\] inUse : bool {#inUse-prop}

**Access functions:**

- `bool` **[isInUse](solid-storagedrive.md#isInUse)**() const

### \[read-only\] removable : bool {#removable-prop}

**Access functions:**

- `bool` **[isRemovable](solid-storagedrive.md#isRemovable)**() const

### \[read-only\] size : qulonglong {#size-prop}

**Access functions:**

- `qulonglong` **[size](solid-storagedrive.md#size)**() const

### \[read-only\] timeDetected : const QDateTime {#timeDetected-prop}

**Access functions:**

- `QDateTime` **[timeDetected](solid-storagedrive.md#timeDetected)**() const

### \[read-only\] timeMediaDetected : QDateTime {#timeMediaDetected-prop}

**Access functions:**

- `QDateTime` **[timeDetected](solid-storagedrive.md#timeDetected)**() const

## Member Function Documentation {#member-function-documentation}

### Solid::StorageDrive::Bus StorageDrive::bus() const {#bus}

Returns the bus type of the physical interface this storage device is connected to.

> **Note:** Getter function for property [bus](solid-storagedrive.md#bus-prop).

*See also* [Solid::StorageDrive::Bus](solid-index.md)

### \[static\] Solid::DeviceInterface::Type StorageDrive::deviceInterfaceType() {#deviceInterfaceType}

Returns the [Solid::DeviceInterface::Type](solid-deviceinterface.md#Type-enum) of the [StorageDrive](solid-storagedrive.md) device interface.

*See also* [Solid::DeviceInterface::Type](solid-index.md)

### Solid::StorageDrive::DriveType StorageDrive::driveType() const {#driveType}

Returns the type of this storage drive.

> **Note:** Getter function for property [driveType](solid-storagedrive.md#driveType-prop).

*See also* [Solid::StorageDrive::DriveType](solid-index.md)

### bool StorageDrive::isHotpluggable() const {#isHotpluggable}

Returns whether this storage device can be plugged or unplugged while the computer is running (that is, it supports hotplugging).

> **Note:** Getter function for property [hotpluggable](solid-storagedrive.md#hotpluggable-prop).

### bool StorageDrive::isInUse() const {#isInUse}

Returns whether the storage device is currently in use, that is, if at least one child storage access is mounted.

> **Note:** Getter function for property [inUse](solid-storagedrive.md#inUse-prop).

### bool StorageDrive::isRemovable() const {#isRemovable}

Returns whether the media contained by this drive can be removed.

For example, a memory card can be removed from the drive by the user, while partitions can't be removed from hard disks.

> **Note:** Getter function for property [removable](solid-storagedrive.md#removable-prop).

### qulonglong StorageDrive::size() const {#size}

Returns this drive's size in bytes.

> **Note:** Getter function for property [size](solid-storagedrive.md#size-prop).

### \[since 6.0\] QDateTime StorageDrive::timeDetected() const {#timeDetected}

Returns the time when the drive was detected.

Typically this means the time a drive was plugged in, or the computer rebooted.

An invalid datetime may be returned if the underlying information is not available.

> **Note:** Getter function for properties [timeDetected](solid-storagedrive.md#timeDetected-prop) and [timeMediaDetected](solid-storagedrive.md#timeMediaDetected-prop).

This function was introduced in Qt 6.0.

### \[since 6.0\] QDateTime StorageDrive::timeMediaDetected() const {#timeMediaDetected}

Returns the time when media in the drive was detected.

Typically this means the time a card was inserted into a reader, or the computer rebooted.

An invalid datetime may be returned if the underlying information is not available.

This function was introduced in Qt 6.0.
