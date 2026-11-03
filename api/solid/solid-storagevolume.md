---
title: "Solid::StorageVolume Class"
description: "This device interface is available on volume devices."
---

# Solid::StorageVolume Class

This device interface is available on volume devices. [More...](#details)

- **Header:** `#include <Solid/StorageVolume>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Solid)`  
  `target_link_libraries(mytarget PRIVATE KF6::Solid)`
- **Inherits:** [Solid::DeviceInterface](solid-deviceinterface.md)
- **Inherited By:** [Solid::OpticalDisc](solid-opticaldisc.md)

[List of all members, including inherited members](solid-storagevolume-members.md)

## Public Types

- [enum StorageVolume::UsageType](#UsageType-enum)

## Properties

- [\[read-only\] fsType : QString](#fsType-prop)
- [\[read-only\] ignored : bool](#ignored-prop)
- [\[read-only\] label : QString](#label-prop)
- [\[read-only\] size : qulonglong](#size-prop)
- [\[read-only\] usage : UsageType](#usage-prop)
- [\[read-only\] uuid : QString](#uuid-prop)

## Public Functions

- [Solid::Device encryptedContainer() const](#encryptedContainer)
- [QString fsType() const](#fsType)
- [bool isIgnored() const](#isIgnored)
- [QString label() const](#label)
- [qulonglong size() const](#size)
- [Solid::StorageVolume::UsageType usage() const](#usage)
- [QString uuid() const](#uuid)

## Static Public Members

- [Solid::DeviceInterface::Type deviceInterfaceType()](#deviceInterfaceType)

## Detailed Description {#details}

A volume is anything that can contain data (partition, optical disc, memory card). It's a particular kind of block device.

A [StorageVolume](solid-storagevolume.md) is commonly used in conjunction with [StorageDrive](solid-storagedrive.md) and [StorageAccess](solid-storageaccess.md).

| [StorageDrive](solid-storagedrive.md) | [StorageVolume](solid-storagevolume.md) | [StorageAccess](solid-storageaccess.md) |
| --- | --- | --- |
| drives | partition tables / filesystems | mount points / partitions |

```cpp
QList<Solid::Device> devices = Solid::Device::listFromType(Solid::DeviceInterface::StorageVolume, QString());
for (auto device : devices) {
    auto volume = device.as<const Solid::StorageVolume>();
    if (volume) {
        // ...
    }
}
```

## Member Type Documentation {#member-type-documentation}

### enum StorageVolume::UsageType {#UsageType-enum}

This enum type defines how a volume is used.

| Constant | Value | Description |
| --- | --- | --- |
| `Solid::StorageVolume::FileSystem` | `2` | A mountable filesystem volume |
| `Solid::StorageVolume::PartitionTable` | `3` | A volume containing a partition table |
| `Solid::StorageVolume::Raid` | `4` | A volume member of a raid set (not mountable) |
| `Solid::StorageVolume::Other` | `0` | A not mountable volume (like a swap partition) |
| `Solid::StorageVolume::Unused` | `1` | An unused or free volume |
| `Solid::StorageVolume::Encrypted` | `5` |   |

## Property Documentation {#property-documentation}

### \[read-only\] fsType : QString {#fsType-prop}

**Access functions:**

- `QString` **[fsType](solid-storagevolume.md#fsType)**() const

### \[read-only\] ignored : bool {#ignored-prop}

**Access functions:**

- `bool` **[isIgnored](solid-storagevolume.md#isIgnored)**() const

### \[read-only\] label : QString {#label-prop}

**Access functions:**

- `QString` **[label](solid-storagevolume.md#label)**() const

### \[read-only\] size : qulonglong {#size-prop}

**Access functions:**

- `qulonglong` **[size](solid-storagevolume.md#size)**() const

### \[read-only\] usage : UsageType {#usage-prop}

**Access functions:**

- `Solid::StorageVolume::UsageType` **[usage](solid-storagevolume.md#usage)**() const

### \[read-only\] uuid : QString {#uuid-prop}

**Access functions:**

- `QString` **[uuid](solid-storagevolume.md#uuid)**() const

## Member Function Documentation {#member-function-documentation}

### \[static\] Solid::DeviceInterface::Type StorageVolume::deviceInterfaceType() {#deviceInterfaceType}

Returns the [Solid::DeviceInterface::Type](solid-deviceinterface.md#Type-enum) of the [StorageVolume](solid-storagevolume.md) device interface.

*See also* [Solid::DeviceInterface::Type](solid-index.md)

### Solid::Device StorageVolume::encryptedContainer() const {#encryptedContainer}

Returns the encrypted volume containing the current volume if applicable, an invalid device otherwise.

### QString StorageVolume::fsType() const {#fsType}

Returns the filesystem type of this volume, QString() otherwise.

FIXME: It's a platform dependent string, maybe we should switch to an enum?

> **Note:** Getter function for property [fsType](solid-storagevolume.md#fsType-prop).

### bool StorageVolume::isIgnored() const {#isIgnored}

Returns whether this volume should be ignored by applications.

If it should be ignored, it generally means that it should be invisible to the user. It's useful for firmware partitions or OS reinstall partitions on some systems.

> **Note:** Getter function for property [ignored](solid-storagevolume.md#ignored-prop).

### QString StorageVolume::label() const {#label}

Returns the volume label if available, QString() otherwise.

> **Note:** Getter function for property [label](solid-storagevolume.md#label-prop).

### qulonglong StorageVolume::size() const {#size}

Returns this volume size in bytes.

> **Note:** Getter function for property [size](solid-storagevolume.md#size-prop).

### Solid::StorageVolume::UsageType StorageVolume::usage() const {#usage}

Returns the usage type for this volume (for example filesystem).

> **Note:** Getter function for property [usage](solid-storagevolume.md#usage-prop).

*See also* [Solid::StorageVolume::UsageType](solid-index.md)

### QString StorageVolume::uuid() const {#uuid}

Returns this volume Universal Unique IDentifier (UUID), QString() otherwise.

You can generally assume that this identifier is unique with reasonable confidence. Except if the volume UUID has been forged to intentionally provoke a collision, the probability of having two volumes with the same UUID is low.

> **Note:** Getter function for property [uuid](solid-storagevolume.md#uuid-prop).
