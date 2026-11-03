---
title: "Solid::Device Class"
description: "Allows applications to deal with devices available in the underlying system."
---

# Solid::Device Class

Allows applications to deal with devices available in the underlying system. [More...](#details)

- **Header:** `#include <Solid/Device>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Solid)`  
  `target_link_libraries(mytarget PRIVATE KF6::Solid)`

[List of all members, including inherited members](solid-device-members.md)

## Public Functions

- [Device(const QString &udi = QString())](#Device)
- [template \<typename DevIface\> DevIface \*as()](#as)
- [template \<typename DevIface\> const DevIface \*as() const](#as-1)
- [Solid::DeviceInterface \*asDeviceInterface(const Solid::DeviceInterface::Type &type)](#asDeviceInterface)
- [const Solid::DeviceInterface \*asDeviceInterface(const Solid::DeviceInterface::Type &type) const](#asDeviceInterface-1)
- [QString description() const](#description)
- [QString displayName() const](#displayName)
- [QStringList emblems() const](#emblems)
- [QString icon() const](#icon)
- [template \<typename DevIface\> bool is() const](#is)
- [bool isDeviceInterface(const Solid::DeviceInterface::Type &type) const](#isDeviceInterface)
- [bool isValid() const](#isValid)
- [Solid::Device parent() const](#parent)
- [QString parentUdi() const](#parentUdi)
- [QString product() const](#product)
- [QString udi() const](#udi)
- [QString vendor() const](#vendor)

## Static Public Members

- [QList\<Solid::Device\> allDevices()](#allDevices)
- [QList\<Solid::Device\> listFromQuery(const Solid::Predicate &predicate, const QString &parentUdi = QString())](#listFromQuery)
- [QList\<Solid::Device\> listFromQuery(const QString &predicate, const QString &parentUdi = QString())](#listFromQuery-1)
- [QList\<Solid::Device\> listFromType(const Solid::DeviceInterface::Type &type, const QString &parentUdi = QString())](#listFromType)
- [Solid::Device storageAccessFromPath(const QString &path)](#storageAccessFromPath)

## Detailed Description {#details}

Device stores a reference to device data provided by the backend.

Device objects are designed to be used by value. Copying these objects is quite cheap, so using pointers is generally not needed.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Device::Device(const QString &*udi* = QString()) {#Device}

Constructs a device for a given Universal Device Identifier `udi`.

### \[static\] QList\<Solid::Device\> Device::allDevices() {#allDevices}

Returns all devices available in the underlying system.

### template \<typename DevIface\> DevIface \*Device::as() {#as}

Returns a specialized interface to interact with the device corresponding to a given device interface, or nullptr if it doesn't exist.

```cpp
const Solid::Processor* processor = device.as<Solid::Processor>();
```

### template \<typename DevIface\> const DevIface \*Device::as() const {#as-1}

Returns a specialized interface to interact with the device corresponding to a given device interface, or nullptr if it doesn't exist.

```cpp
const Solid::Processor* processor = device.as<const Solid::Processor>();
```

### Solid::DeviceInterface \*Device::asDeviceInterface(const Solid::DeviceInterface::Type &*type*) {#asDeviceInterface}

Returns a specialized interface to interact with the device corresponding to a particular device interface `type`, or nullptr if it doesn't exist.

```cpp
const Solid::Battery* battery =
    qobject_cast<const Solid::Battery>(device.asDeviceInterface(Solid::DeviceInterface::Battery));
```

### const Solid::DeviceInterface \*Device::asDeviceInterface(const Solid::DeviceInterface::Type &*type*) const {#asDeviceInterface-1}

Returns a specialized interface to interact with the device corresponding to a particular device interface `type`, or nullptr if it doesn't exist.

### QString Device::description() const {#description}

Returns the description of this device.

### QString Device::displayName() const {#displayName}

Returns the display name to use for this device.

Same as description when not defined.

### QStringList Device::emblems() const {#emblems}

Returns the names of the emblems representing the state of this device.

The naming follows the freedesktop.org specification.

### QString Device::icon() const {#icon}

Returns the name of the icon representing this device.

The naming follows the freedesktop.org specification.

### template \<typename DevIface\> bool Device::is() const {#is}

Tests if a device provides a given device interface.

```cpp
if (device.is<Solid::StorageDrive>()) {
    // ...
}
```

### bool Device::isDeviceInterface(const Solid::DeviceInterface::Type &*type*) const {#isDeviceInterface}

Tests if a device interface `type` is available from the device.

```cpp
if (device.isDeviceInterface(Solid::DeviceInterface::StorageAccess)) {
    // ...
}
```

### bool Device::isValid() const {#isValid}

Returns if this device is valid (available in the system).

### \[static\] QList\<Solid::Device\> Device::listFromQuery(const Solid::Predicate &*predicate*, const QString &*parentUdi* = QString()) {#listFromQuery}

Returns a list of devices matching the given `predicate` query.

The `parentUdi` should match the provider for the device. For example:

- /org/kde/solid/udev
- /org/freedesktop/UPower
- /org/freedesktop/UDisks2

*See also* [Solid::Predicate](solid-index.md)

### \[static\] QList\<Solid::Device\> Device::listFromQuery(const QString &*predicate*, const QString &*parentUdi* = QString()) {#listFromQuery-1}

This function overloads [Device::listFromQuery()](solid-device.md#listFromQuery).

### \[static\] QList\<Solid::Device\> Device::listFromType(const Solid::DeviceInterface::Type &*type*, const QString &*parentUdi* = QString()) {#listFromType}

Returns a list of devices matching the given `type`.

The `parentUdi` should match the provider for the device. For example:

- /org/kde/solid/udev
- /org/freedesktop/UPower
- /org/freedesktop/UDisks2

### Solid::Device Device::parent() const {#parent}

Returns the parent of the Device.

*See also* [parentUdi](solid-device.md#parentUdi)()

### QString Device::parentUdi() const {#parentUdi}

Returns the Universal Device Identifier (UDI) of the Device's parent.

### QString Device::product() const {#product}

Returns the name of the product corresponding to this device.

### \[static\] Solid::Device Device::storageAccessFromPath(const QString &*path*) {#storageAccessFromPath}

Returns the Device containing the filesystem for the given `path`.

For Devices implementing the [StorageVolume](solid-storagevolume.md) interface, only ones matching UsageType::FileSystem are returned, i.e. no backing encrypted volumes.

*See also* [QFileInfo::canonicalFilePath](https://doc.qt.io/qt-6/qfileinfo.html#canonicalFilePath)

### QString Device::udi() const {#udi}

Returns the Universal Device Identifier `udi`.

> **Warning:** Don't use the UDI for anything except communication with Solid. Also don't store UDIs as there's no guarantee that the UDI stays the same when the hardware setup changed. The UDI is a unique identifier that is local to the computer in question and for the current boot session. The UDIs may change after a reboot. Similar hardware in other computers may have different values; different hardware could have the same UDI.

### QString Device::vendor() const {#vendor}

Returns the name of the device vendor.
