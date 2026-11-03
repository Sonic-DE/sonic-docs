---
title: "KMemoryInfo Class"
description: "The KMemoryInfo class provides an interface to get memory information (RAM/SWAP)."
---

# KMemoryInfo Class

The [KMemoryInfo](kmemoryinfo.md) class provides an interface to get memory information (RAM/SWAP). [More...](#details)

- **Header:** `#include <KMemoryInfo>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

[List of all members, including inherited members](kmemoryinfo-members.md)

## Public Functions

- [KMemoryInfo()](#KMemoryInfo)
- [quint64 availablePhysical() const](#availablePhysical)
- [quint64 buffers() const](#buffers)
- [quint64 cached() const](#cached)
- [quint64 freePhysical() const](#freePhysical)
- [quint64 freeSwapFile() const](#freeSwapFile)
- [bool isNull() const](#isNull)
- [quint64 totalPhysical() const](#totalPhysical)
- [quint64 totalSwapFile() const](#totalSwapFile)
- [bool KMemoryInfo::operator!=(const KMemoryInfo &other) const](#operator-not-eq)
- [bool KMemoryInfo::operator==(const KMemoryInfo &other) const](#operator-eq-eq)

## Detailed Description {#details}

To use the class, simply create an instance.

```cpp
KMemoryInfo memInfo;
if (!memInfo.isNull()) {
    ...
}
```

## Member Function Documentation {#member-function-documentation}

### KMemoryInfo::KMemoryInfo() {#KMemoryInfo}

Constructs a class with a snapshot of the state of the memory. If an error occurs, a null object is returned.

*See also* [isNull](kmemoryinfo.md#isNull)

### quint64 KMemoryInfo::availablePhysical() const {#availablePhysical}

The available memory is the free RAM without considering caches and buffers allocated by the operating system.

> **Note:** You should always use this value to check if there is enough RAM for your data.

Returns The memory available to the processes in bytes.

*See also* [freePhysical](kmemoryinfo.md#freePhysical)

### quint64 KMemoryInfo::buffers() const {#buffers}

Returns The size of RAM used as buffers in bytes. This value can be zero.

### quint64 KMemoryInfo::cached() const {#cached}

Returns The size of RAM used as cache in bytes.

### quint64 KMemoryInfo::freePhysical() const {#freePhysical}

The free memory is the amount of free RAM as reported by the operating system. This value is often tainted with caches and buffers used by the operating system, resulting in a low value.

> **Note:** Don't use this value to determine if you have enough RAM for your data.

Returns the free RAM reported by OS in bytes.

*See also* [availablePhysical](kmemoryinfo.md#availablePhysical)

### quint64 KMemoryInfo::freeSwapFile() const {#freeSwapFile}

Returns The free swap size in bytes.

### bool KMemoryInfo::isNull() const {#isNull}

Returns true if the class is null, otherwise false.

### quint64 KMemoryInfo::totalPhysical() const {#totalPhysical}

Returns The total system RAM in bytes.

### quint64 KMemoryInfo::totalSwapFile() const {#totalSwapFile}

Returns The size of swap file in bytes.

> **Note:** On an operating system where the paging file is dynamically allocated, this value can be zero when no memory pages are swapped.

### bool KMemoryInfo::operator!=(const KMemoryInfo &*other*) const {#operator-not-eq}

Returns true if this memoryinfo is different from the other memoryinfo, otherwise false.

### bool KMemoryInfo::operator==(const KMemoryInfo &*other*) const {#operator-eq-eq}

Returns true if this memoryinfo is equal to the other memoryinfo, otherwise false.
