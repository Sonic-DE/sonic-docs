---
title: "KConfig"
description: "Widgets for configuration dialogs."
---

# KConfig

Widgets for configuration dialogs.

[KConfigWidgets](kconfigwidgets-module.md) provides easy-to-use classes to create configuration dialogs, as well as a set of widgets which uses [KConfig](../kconfigcore/kconfig.md) to store their settings.

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

- [KConfigWidgets C++ Classes](kconfigwidgets-module.md)
