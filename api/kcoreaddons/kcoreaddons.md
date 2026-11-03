---
title: "KCoreAddons Namespace"
description: "Provides utility functions for metadata about the KCoreAddons library."
---

# KCoreAddons Namespace

Provides utility functions for metadata about the [KCoreAddons](kcoreaddons-module.md) library. [More...](#details)

- Header: KCoreAddons
- CMake: find\_package(KF6 REQUIRED COMPONENTS CoreAddons) target\_link\_libraries(mytarget PRIVATE KF6::CoreAddons)

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### unsigned int KCoreAddons::version() {#version}

Returns a numerical version number of [KCoreAddons](kcoreaddons-module.md) at run-time in the form 0xMMNNPP (MM = major, NN = minor, PP = patch) This can be compared using the macro [QT\_VERSION\_CHECK](https://doc.qt.io/qt-6/qtversionchecks.html#QT_VERSION_CHECK).

For example:

```cpp
if (KCoreAddons::version() < QT_VERSION_CHECK(5,19,0))
```

This may be a different version than the version the application was compiled against.

### QString KCoreAddons::versionString() {#versionString}

Returns the version number of [KCoreAddons](kcoreaddons-module.md) at run-time as a string (for example, "5.19.0").

This may be a different version than the version the application was compiled against.
