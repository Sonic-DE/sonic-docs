---
title: "Solid::StorageAccess Class"
description: "This device interface is available on volume devices to access them (i.e. mount or unmount them)."
---

# Solid::StorageAccess Class

This device interface is available on volume devices to access them (i.e. mount or unmount them). [More...](#details)

- **Header:** `#include <Solid/StorageAccess>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Solid)`  
  `target_link_libraries(mytarget PRIVATE KF6::Solid)`
- **Inherits:** [Solid::DeviceInterface](solid-deviceinterface.md)

[List of all members, including inherited members](solid-storageaccess-members.md)

## Properties

- [\[read-only\] accessible : bool](#accessible-prop)
- [\[read-only\] encrypted : bool](#encrypted-prop)
- [\[read-only\] filePath : QString](#filePath-prop)
- [\[read-only\] ignored : bool](#ignored-prop)

## Public Functions

- [bool canCheck() const](#canCheck)
- [bool canRepair() const](#canRepair)
- [bool check()](#check)
- [QString filePath() const](#filePath)
- [bool isAccessible() const](#isAccessible)
- [bool isEncrypted() const](#isEncrypted)
- [bool isIgnored() const](#isIgnored)
- [bool repair()](#repair)
- [bool setup()](#setup)
- [bool teardown()](#teardown)

## Signals

- [void accessibilityChanged(bool accessible, const QString &udi)](#accessibilityChanged)
- [void checkDone(Solid::ErrorType error, QVariant errorData, const QString &udi)](#checkDone) (since 6.11)
- [void checkRequested(const QString &udi)](#checkRequested) (since 6.11)
- [void repairDone(Solid::ErrorType error, QVariant errorData, const QString &udi)](#repairDone)
- [void repairRequested(const QString &udi)](#repairRequested)
- [void setupDone(Solid::ErrorType error, QVariant errorData, const QString &udi)](#setupDone)
- [void setupRequested(const QString &udi)](#setupRequested)
- [void teardownDone(Solid::ErrorType error, QVariant errorData, const QString &udi)](#teardownDone)
- [void teardownRequested(const QString &udi)](#teardownRequested)

## Static Public Members

- [Solid::DeviceInterface::Type deviceInterfaceType()](#deviceInterfaceType)

## Detailed Description {#details}

A volume is anything that can contain data (partition, optical disc, memory card). It's a particular kind of block device.

A [StorageAccess](solid-storageaccess.md) is commonly used in conjunction with [StorageDrive](solid-storagedrive.md) and [StorageVolume](solid-storagevolume.md).

| [StorageDrive](solid-storagedrive.md) | [StorageVolume](solid-storagevolume.md) | [StorageAccess](solid-storageaccess.md) |
| --- | --- | --- |
| drives | partition tables / filesystems | mount points / partitions |

```cpp
const List<Solid::Device> devices = Solid::Device::listFromType(Solid::DeviceInterface::StorageVolume, QString());
for (auto device : devices) {
    auto access = device.as<const Solid::StorageAccess>();
    if (access) {
        // ...
    }
}
```

## Property Documentation {#property-documentation}

### \[read-only\] accessible : bool {#accessible-prop}

**Access functions:**

- `bool` **[isAccessible](solid-storageaccess.md#isAccessible)**() const

### \[read-only\] encrypted : bool {#encrypted-prop}

**Access functions:**

- `bool` **[isEncrypted](solid-storageaccess.md#isEncrypted)**() const

### \[read-only\] filePath : QString {#filePath-prop}

**Access functions:**

- `QString` **[filePath](solid-storageaccess.md#filePath)**() const

### \[read-only\] ignored : bool {#ignored-prop}

**Access functions:**

- `bool` **[isIgnored](solid-storageaccess.md#isIgnored)**() const

## Member Function Documentation {#member-function-documentation}

### \[signal\] void StorageAccess::accessibilityChanged(bool *accessible*, const QString &*udi*) {#accessibilityChanged}

This signal is emitted when the accessiblity of this device has changed.

### bool StorageAccess::canCheck() const {#canCheck}

Indicates if this volume can check for filesystem errors.

### bool StorageAccess::canRepair() const {#canRepair}

Returns whether the filesystem of this volume supports repair attempts.

It does not indicate if such an attempt will succeed.

### bool StorageAccess::check() {#check}

Checks the filesystem for consistency avoiding any modifications or repairs.

Returns whether the filesystem is undamaged. Mounted or unsupported filesystems will result in an error.

### \[signal, since 6.11\] void StorageAccess::checkDone(Solid::ErrorType *error*, QVariant *errorData*, const QString &*udi*) {#checkDone}

This signal is emitted when the attempted check of the device with the given `udi` is completed.

Returns an `error` followed by additional `errorData` information, if any.

The signal might be spontaneous i.e. it can be triggered by another process.

This function was introduced in Qt 6.11.

### \[signal, since 6.11\] void StorageAccess::checkRequested(const QString &*udi*) {#checkRequested}

This signal is emitted when a check of the device with the given `udi` is requested.

The signal might be spontaneous i.e. it can be triggered by another process.

This function was introduced in Qt 6.11.

### \[static\] Solid::DeviceInterface::Type StorageAccess::deviceInterfaceType() {#deviceInterfaceType}

Returns the [Solid::DeviceInterface::Type](solid-deviceinterface.md#Type-enum) of the [StorageAccess](solid-storageaccess.md) device interface.

*See also* [Solid::DeviceInterface::Type](solid-index.md)

### QString StorageAccess::filePath() const {#filePath}

Returns the absolute path to the mount point if the volume is mounted, QString() otherwise.

> **Note:** Getter function for property [filePath](solid-storageaccess.md#filePath-prop).

### bool StorageAccess::isAccessible() const {#isAccessible}

Returns if this volume is mounted.

> **Note:** Getter function for property [accessible](solid-storageaccess.md#accessible-prop).

### bool StorageAccess::isEncrypted() const {#isEncrypted}

Returns if the source of the storage is encrypted.

> **Note:** Getter function for property [encrypted](solid-storageaccess.md#encrypted-prop).

### bool StorageAccess::isIgnored() const {#isIgnored}

Returns whether this volume should be ignored by applications.

If it should be ignored, it generally means that it should be invisible to the user. It's useful for firmware partitions or OS reinstall partitions on some systems.

> **Note:** Getter function for property [ignored](solid-storageaccess.md#ignored-prop).

### bool StorageAccess::repair() {#repair}

Tries to repair the filesystem.

Mounted or unsupported filesystems will result in an error.

Returns whether the filesystem could be successfully repaired.

### \[signal\] void StorageAccess::repairDone(Solid::ErrorType *error*, QVariant *errorData*, const QString &*udi*) {#repairDone}

This signal is emitted when the attempted repair of the device with the given `udi` is completed.

Returns an `error` followed by additional `errorData` information, if any.

The signal might be spontaneous i.e. it can be triggered by another process.

### \[signal\] void StorageAccess::repairRequested(const QString &*udi*) {#repairRequested}

This signal is emitted when a repair of the device with the given `udi` is requested.

The signal might be spontaneous i.e. it can be triggered by another process.

### bool StorageAccess::setup() {#setup}

Mounts the volume.

Returns false if the operation is not supported, true if the operation is attempted.

### \[signal\] void StorageAccess::setupDone(Solid::ErrorType *error*, QVariant *errorData*, const QString &*udi*) {#setupDone}

This signal is emitted when the attempted setting up of the device with the given `udi` is completed.

Returns an `error` followed by additional `errorData` information, if any.

The signal might be spontaneous i.e. it can be triggered by another process.

### \[signal\] void StorageAccess::setupRequested(const QString &*udi*) {#setupRequested}

\* This signal is emitted when a setup of the device with the given `udi` is requested.

\* The signal might be spontaneous i.e. it can be triggered by another process.

### bool StorageAccess::teardown() {#teardown}

Unmounts the volume.

Returns `false` if the operation is not supported, `true` if the operation is attempted.

### \[signal\] void StorageAccess::teardownDone(Solid::ErrorType *error*, QVariant *errorData*, const QString &*udi*) {#teardownDone}

This signal is emitted when the attempted tearing down of the device with the given `udi` is completed.

Returns an `error` followed by additional `errorData` information, if any.

The signal might be spontaneous i.e. it can be triggered by another process.

### \[signal\] void StorageAccess::teardownRequested(const QString &*udi*) {#teardownRequested}

This signal is emitted when a teardown of the device with the given `udi` is requested.

The signal might be spontaneous i.e. it can be triggered by another process.
