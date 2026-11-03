---
title: "KXmlGui"
description: "Collection of convenience classes and widgets to manage your own main QtWidgets window."
---

# KXmlGui

Collection of convenience classes and widgets to manage your own main QtWidgets window.

[KXmlGui](kxmlgui-module.md) is a collection of convenience classes and widgets to manage your app's main window.

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

- [KXmlGui C++ Classes](kxmlgui-module.md)
