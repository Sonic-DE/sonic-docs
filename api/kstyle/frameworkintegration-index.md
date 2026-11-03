---
title: "FrameworkIntegration"
description: "Integration of Qt application with KDE workspaces."
---

# FrameworkIntegration

Integration of Qt application with KDE workspaces.

Framework Integration is a set of plugins responsible for better integration of Qt applications when running on a KDE Plasma workspace.

Applications do not need to link to this directly.

The library KF6Style provides integration with KDE Plasma Workspace settings for Qt styles.

Derive your Qt style from [KStyle](kstyle-module.md) to automatically inherit various settings from the KDE Plasma Workspace, providing a consistent user experience. For example, this will ensure a consistent single-click or double-click activation setting, and the use of standard themed icons.

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

- [KStyle C++ Classes](kstyle-module.md)
