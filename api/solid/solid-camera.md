---
title: "Solid::Camera Class"
description: "This device interface is available on digital camera devices."
---

# Solid::Camera Class

This device interface is available on digital camera devices. [More...](#details)

- **Header:** `#include <Solid/Camera>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Solid)`  
  `target_link_libraries(mytarget PRIVATE KF6::Solid)`
- **Inherits:** [Solid::DeviceInterface](solid-deviceinterface.md)

[List of all members, including inherited members](solid-camera-members.md)

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

A digital camera is a device used to transform images into data. Nowadays most digital cameras are multifunctional and able to take photographs, video or sound. On the system side they are a particular type of device holding data, the access method can be different from the typical storage device, hence why it's a separate device interface.

## Property Documentation {#property-documentation}

### \[read-only\] supportedDrivers : QStringList {#supportedDrivers-prop}

**Access functions:**

- `QStringList` **[supportedDrivers](solid-camera.md#supportedDrivers)**(`QString` *protocol* = QString()) const

### \[read-only\] supportedProtocols : QStringList {#supportedProtocols-prop}

**Access functions:**

- `QStringList` **[supportedProtocols](solid-camera.md#supportedProtocols)**() const

## Member Function Documentation {#member-function-documentation}

### \[static\] Solid::DeviceInterface::Type Camera::deviceInterfaceType() {#deviceInterfaceType}

Returns the [Solid::DeviceInterface::Type](solid-deviceinterface.md#Type-enum) of the Camera device interface.

*See also* [Solid::DeviceInterface::Type](solid-index.md)

### QVariant Camera::driverHandle(const QString &*driver*) const {#driverHandle}

Returns a `driver` specific string allowing to access the device.

For example for the "gphoto" driver it will return a list of the form '("usb", vendor\_id, product\_id)'.

### QStringList Camera::supportedDrivers(QString *protocol* = QString()) const {#supportedDrivers}

Returns known installed device drivers that claim to handle this device using the requested `protocol`.

If `protocol` is omitted, returns a list of all drivers supporting the device.

> **Note:** Getter function for property [supportedDrivers](solid-camera.md#supportedDrivers-prop).

### QStringList Camera::supportedProtocols() const {#supportedProtocols}

Returns known protocols this device supports.

This list may be dependent on installed device driver libraries.

> **Note:** Getter function for property [supportedProtocols](solid-camera.md#supportedProtocols-prop).
