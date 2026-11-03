---
title: "KJobWidgets"
description: "Widgets for showing progress of asynchronous jobs.."
---

# KJobWidgets

Widgets for showing progress of asynchronous jobs..

Widgets for showing progress of asynchronous jobs.

## Using the Module {#using-the-module}

Using a Qt module's C++ API requires linking against the module library, either directly or through other dependencies. Several build tools have dedicated support for this, including CMake and qmake.

### Building with CMake {#building-with-cmake}

Use the `find_package()` command to locate the needed module component in the `Qt6` package:

```cpp
find_package(Qt6 REQUIRED COMPONENTS KF6)
target_link_libraries(mytarget PRIVATE Qt6::KF6)
```

For more details, see the Build with CMake overview.

## API Reference {#api-reference}

- [KJobWidgets C++ Classes](kjobwidgets-module.md)
