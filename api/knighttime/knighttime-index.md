---
title: "KNightTime"
description: "Helpers for scheduling the dark-light cycle."
---

# KNightTime

Helpers for scheduling the dark-light cycle.

This library provides a C++ API that provides information about the times of the dark-light cycle. It can be used to implement such as adjusting the screen color temperature depending on time of day, etc.

## Using the Module {#using-the-module}

Using a Qt module's C++ API requires linking against the module library, either directly or through other dependencies. Several build tools have dedicated support for this, including CMake and [qmake](https://doc.qt.io/qt-6/resources.html#qmake).

### Building with CMake {#building-with-cmake}

Use the `find_package()` command to locate the needed module component in the `Qt6` package:

```cpp
find_package(Qt6 REQUIRED COMPONENTS KNightTime)
target_link_libraries(mytarget PRIVATE Qt6::KNightTime)
```

For more details, see the Build with CMake overview.

## API Reference {#api-reference}

- [KNightTime C++ Classes](knighttime-module.md)
