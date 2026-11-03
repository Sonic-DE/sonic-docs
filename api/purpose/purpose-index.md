---
title: "Purpose"
description: "Framework for providing abstractions to get the developer's purposes fulfilled.."
---

# Purpose

Framework for providing abstractions to get the developer's purposes fulfilled..

Framework for providing abstractions to get the developer's purposes fulfilled.

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

- [Purpose C++ Classes](purpose-module.md)
- [PurposeWidgets C++ Classes](../purposewidgets/purposewidgets-module.md)
- [Purpose QML Types](../purposeqml/org-kde-purpose-qmlmodule.md)
