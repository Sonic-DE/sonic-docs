---
title: "Solid::PortableMediaPlayer Class"
description: "This class implements Portable Media Player device interface and represents a portable media player attached to the system."
---

# Solid::PortableMediaPlayer Class

This class implements Portable Media Player device interface and represents a portable media player attached to the system. [More...](#details)

- **Header:** `#include <Solid/PortableMediaPlayer>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Solid)`  
  `target_link_libraries(mytarget PRIVATE KF6::Solid)`
- **Inherits:** [Solid::DeviceInterface](solid-deviceinterface.md)

[List of all members, including inherited members](solid-portablemediaplayer-members.md)

## Properties

- [\[read-only\] supportedDrivers : QStringList](#supportedDrivers-prop)
- [\[read-only\] supportedProtocols : QStringList](#supportedProtocols-prop)

## Public Functions

- [QVariant driverHandle(const QString &driver) const](#driverHandle)
- [QStringList supportedDrivers(QString protocol = QString()) const](#supportedDrivers)
- [QStringList supportedProtocols() const](#supportedProtocols)

## Static Public Members

- [Solid::DeviceInterface::Type deviceInterfaceType()](#deviceInterfaceType)

## Detailed Description {#details}

A portable media player is a portable device able to play multimedia files.

Some of them have recording capabilities.

## Property Documentation {#property-documentation}

### \[read-only\] supportedDrivers : QStringList {#supportedDrivers-prop}

**Access functions:**

- `QStringList` **[supportedDrivers](solid-portablemediaplayer.md#supportedDrivers)**(`QString` *protocol* = QString()) const

### \[read-only\] supportedProtocols : QStringList {#supportedProtocols-prop}

**Access functions:**

- `QStringList` **[supportedProtocols](solid-portablemediaplayer.md#supportedProtocols)**() const

## Member Function Documentation {#member-function-documentation}

### \[static\] Solid::DeviceInterface::Type PortableMediaPlayer::deviceInterfaceType() {#deviceInterfaceType}

Returns the [Solid::DeviceInterface::Type](solid-deviceinterface.md#Type-enum) of the [PortableMediaPlayer](solid-portablemediaplayer.md) device interface.

*See also* [Solid::DeviceInterface::Type](solid-index.md)

### QVariant PortableMediaPlayer::driverHandle(const QString &*driver*) const {#driverHandle}

Returns a `driver` specific string allowing to access the device.

For example for the "mtp" driver it will return the serial number of the device.

### QStringList PortableMediaPlayer::supportedDrivers(QString *protocol* = QString()) const {#supportedDrivers}

Returns known installed device drivers that claim to handle this device using the requested `protocol`.

If `protocol` is omitted, returns a list of all drivers supporting the device.

> **Note:** Getter function for property [supportedDrivers](solid-portablemediaplayer.md#supportedDrivers-prop).

### QStringList PortableMediaPlayer::supportedProtocols() const {#supportedProtocols}

Returns known protocols this device supports.

This list may be dependent on installed device driver libraries.

> **Note:** Getter function for property [supportedProtocols](solid-portablemediaplayer.md#supportedProtocols-prop).
