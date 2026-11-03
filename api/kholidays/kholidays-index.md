---
title: "KHolidays"
description: "Dates for holidays and other special events."
---

# KHolidays

Dates for holidays and other special events.

This library provides a C++ API that determines holiday and other special events for a geographical region.

## Using the Module {#using-the-module}

Using a Qt module's C++ API requires linking against the module library, either directly or through other dependencies. Several build tools have dedicated support for this, including CMake and [qmake](https://doc.qt.io/qt-6/resources.html#qmake).

### Building with CMake {#building-with-cmake}

Use the `find_package()` command to locate the needed module component in the `Qt6` package:

```cpp
find_package(Qt6 REQUIRED COMPONENTS KF6)
target_link_libraries(mytarget PRIVATE Qt6::KF6)
```

For more details, see the Build with CMake overview.

## API Reference {#api-reference}

- [KHolidays C++ Classes](kholidays-module.md)
- [KHolidays QML Types](org-kde-kholidays-qmlmodule.md)
