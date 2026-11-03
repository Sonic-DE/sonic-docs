---
title: "Solid::DeviceInterface Class"
description: "Base class of all device interfaces."
---

# Solid::DeviceInterface Class

Base class of all device interfaces. [More...](#details)

- **Header:** `#include <Solid/DeviceInterface>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Solid)`  
  `target_link_libraries(mytarget PRIVATE KF6::Solid)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)
- **Inherited By:** [Solid::Battery](solid-battery.md), [Solid::Block](solid-block.md), [Solid::Camera](solid-camera.md), [Solid::GenericInterface](solid-genericinterface.md), [Solid::NetworkShare](solid-networkshare.md), [Solid::PortableMediaPlayer](solid-portablemediaplayer.md), [Solid::Processor](solid-processor.md), [Solid::StorageAccess](solid-storageaccess.md), [Solid::StorageDrive](solid-storagedrive.md), and [Solid::StorageVolume](solid-storagevolume.md)

[List of all members, including inherited members](solid-deviceinterface-members.md)

## Public Types

- [enum DeviceInterface::Type](#Type-enum)

## Public Functions

- [bool isValid() const](#isValid)

## Static Public Members

- [Solid::DeviceInterface::Type stringToType(const QString &type)](#stringToType)
- [QString typeDescription(Solid::DeviceInterface::Type type)](#typeDescription)
- [QString typeToString(Solid::DeviceInterface::Type type)](#typeToString)

## Detailed Description {#details}

A device interface describes what a device can do. A device generally has a set of device interfaces.

## Member Type Documentation {#member-type-documentation}

### enum DeviceInterface::Type {#Type-enum}

This enum type defines the type of device interface that a Device can have.

| Constant | Value | Description |
| --- | --- | --- |
| `Solid::DeviceInterface::Unknown` | `0` | An undetermined device interface |
| `Solid::DeviceInterface::GenericInterface` | `1` |   |
| `Solid::DeviceInterface::Processor` | `2` | A processor |
| `Solid::DeviceInterface::Block` | `3` | A block device |
| `Solid::DeviceInterface::StorageAccess` | `4` | A mechanism to access data on a storage device |
| `Solid::DeviceInterface::StorageDrive` | `5` | A storage drive |
| `Solid::DeviceInterface::OpticalDrive` | `6` | An optical drive (CD-ROM, DVD, ...) |
| `Solid::DeviceInterface::StorageVolume` | `7` | A volume |
| `Solid::DeviceInterface::OpticalDisc` | `8` | An optical disc |
| `Solid::DeviceInterface::Camera` | `9` | A digital camera |
| `Solid::DeviceInterface::PortableMediaPlayer` | `10` | A portable media player |
| `Solid::DeviceInterface::Battery` | `12` |   |
| `Solid::DeviceInterface::NetworkShare` | `14` | A network share interface |

## Member Function Documentation {#member-function-documentation}

### bool DeviceInterface::isValid() const {#isValid}

Returns if this device interface is valid (available in the system).

### \[static\] Solid::DeviceInterface::Type DeviceInterface::stringToType(const QString &*type*) {#stringToType}

Returns the device interface type for the given class name.

### \[static\] QString DeviceInterface::typeDescription(Solid::DeviceInterface::Type *type*) {#typeDescription}

Returns a pretty name for the device interface type for use in an application.

### \[static\] QString DeviceInterface::typeToString(Solid::DeviceInterface::Type *type*) {#typeToString}

Returns the class name of the device interface type.
