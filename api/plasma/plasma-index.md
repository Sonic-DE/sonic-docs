---
title: "Plasma"
description: "Plasma Stuff."
---

# Plasma

Plasma Stuff.

Foundational libraries, components, and tools of the Plasma workspaces.

## Using the Module {#using-the-module}

Using a Qt module's C++ API requires linking against the module library, either directly or through other dependencies. Several build tools have dedicated support for this, including CMake and [qmake](https://doc.qt.io/qt-6/resources.html#qmake).

### Building with CMake {#building-with-cmake}

Use the `find_package()` command to locate the needed module component in the `Qt6` package:

```cpp
find_package(Qt6 REQUIRED COMPONENTS Plasma)
target_link_libraries(mytarget PRIVATE Qt6::Plasma)
```

For more details, see the Build with CMake overview.

## API Reference {#api-reference}

- [Plasma C++ Classes](plasma-module.md)
- [Plasma Quick C++ Classes](../plasmaquick/plasmaquick-module.md)
- [Plasma Core QML Types](../plasmacore/org-kde-plasma-core-qmlmodule.md)
- [Plasma Components QML Types](../plasmacomponents/org-kde-plasma-components-qmlmodule.md)
- [Plasma Extras QML Types](../plasmaextras/org-kde-plasma-extras-qmlmodule.md)
- [Plasmoid QML Types](../plasmaquick/org-kde-plasma-plasmoid-qmlmodule.md)
- [Plasmoid Configuration QML Types](../plasmaquick/org-kde-plasma-configuration-qmlmodule.md)
