---
title: "Solid Namespace"
description: "Hardware Abstraction Framework."
---

# Solid Namespace

Hardware Abstraction Framework. [More...](#details)

- **Header:** `#include <Solid/SolidNamespace>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Solid)`  
  `target_link_libraries(mytarget PRIVATE KF6::Solid)`

## Detailed Description {#details}

## Classes {#classes}

### class [Battery](solid-battery.md)

This device interface is available on batteries.

### class [Block](solid-block.md)

This device interface is available on block devices.

### class [Camera](solid-camera.md)

This device interface is available on digital camera devices.

### class [Device](solid-device.md)

Allows applications to deal with devices available in the underlying system.

### class [DeviceInterface](solid-deviceinterface.md)

Base class of all device interfaces.

### class [DeviceNotifier](solid-devicenotifier.md)

This class allow to query the underlying system for information about the hardware available.

### class [GenericInterface](solid-genericinterface.md)

Generic interface to deal with a device.

### class [NetworkShare](solid-networkshare.md)

This device interface is available for network share volumes.

### class [OpticalDisc](solid-opticaldisc.md)

This device interface is available on optical discs.

### class [OpticalDrive](solid-opticaldrive.md)

This device interface is available on CD-R\*,DVD\*,Blu-Ray,HD-DVD drives.

### class [PortableMediaPlayer](solid-portablemediaplayer.md)

This class implements Portable Media Player device interface and represents a portable media player attached to the system.

### class [Predicate](solid-predicate.md)

This class implements predicates for devices.

### class [Processor](solid-processor.md)

This device interface is available on processors.

### class [StorageAccess](solid-storageaccess.md)

This device interface is available on volume devices to access them (i.e. mount or unmount them).

### class [StorageDrive](solid-storagedrive.md)

This device interface is available on storage devices.

### class [StorageVolume](solid-storagevolume.md)

This device interface is available on volume devices.

## Type Documentation {#type-documentation}

### enum Solid::ErrorType {#ErrorType-enum}

| Constant |   |
| --- | --- |
| `Solid::NoError` | `0` |
| `Solid::UnauthorizedOperation` | `1` |
| `Solid::DeviceBusy` | `2` |
| `Solid::OperationFailed` | `3` |
| `Solid::UserCanceled` | `4` |
| `Solid::InvalidOption` | `5` |
| `Solid::MissingDriver` | `6` |
