---
title: "Solid::Block Class"
description: "This device interface is available on block devices."
---

# Solid::Block Class

This device interface is available on block devices. [More...](#details)

- **Header:** `#include <Solid/Block>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Solid)`  
  `target_link_libraries(mytarget PRIVATE KF6::Solid)`
- **Inherits:** [Solid::DeviceInterface](solid-deviceinterface.md)

[List of all members, including inherited members](solid-block-members.md)

## Properties

- [\[read-only\] device : QString](#device-prop)
- [\[read-only\] isSystem : bool](#isSystem-prop)
- [\[read-only\] major : int](#major-prop)
- [\[read-only\] minor : int](#minor-prop)

## Public Functions

- [QString device() const](#device)
- [int deviceMajor() const](#deviceMajor)
- [int deviceMinor() const](#deviceMinor)
- [bool isSystem() const](#isSystem) (since 6.15)

## Static Public Members

- [Solid::DeviceInterface::Type deviceInterfaceType()](#deviceInterfaceType)

## Detailed Description {#details}

A block device is an addressable device such as drive or partition. It is possible to interact with such a device using a special file in the system.

## Property Documentation {#property-documentation}

### \[read-only\] device : QString {#device-prop}

**Access functions:**

- `QString` **[device](solid-block.md#device)**() const

### \[read-only\] isSystem : bool {#isSystem-prop}

**Access functions:**

- `bool` **[isSystem](solid-block.md#isSystem)**() const

### \[read-only\] major : int {#major-prop}

**Access functions:**

- `int` **[deviceMajor](solid-block.md#deviceMajor)**() const

### \[read-only\] minor : int {#minor-prop}

**Access functions:**

- `int` **[deviceMinor](solid-block.md#deviceMinor)**() const

## Member Function Documentation {#member-function-documentation}

### QString Block::device() const {#device}

Returns the absolute path of the special file to interact with the device.

> **Note:** Getter function for property [device](solid-block.md#device-prop).

### \[static\] Solid::DeviceInterface::Type Block::deviceInterfaceType() {#deviceInterfaceType}

Returns the [Solid::DeviceInterface::Type](solid-deviceinterface.md#Type-enum) of the Block device interface.

*See also* [Solid::DeviceInterface::Type](solid-index.md)

### int Block::deviceMajor() const {#deviceMajor}

Returns the major number of the node file to interact with the device.

> **Note:** Getter function for property [major](solid-block.md#major-prop).

### int Block::deviceMinor() const {#deviceMinor}

Returns the minor number of the node file to interact with the device.

> **Note:** Getter function for property [minor](solid-block.md#minor-prop).

### \[since 6.15\] bool Block::isSystem() const {#isSystem}

Returns whether this block is considered a system block, that is, it requires additional permissions to access (mount/umount).

It defaults to false if the backend does not support it.

> **Note:** Getter function for property [isSystem](solid-block.md#isSystem-prop).

This function was introduced in Qt 6.15.
