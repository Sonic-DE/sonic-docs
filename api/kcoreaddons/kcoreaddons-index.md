---
title: "KCoreAddons"
description: "Additions to Qt Core."
---

# KCoreAddons

Additions to Qt Core.

[KCoreAddons](kcoreaddons-module.md) are addons to [QtCore](https://doc.qt.io/qt-6/qtcore-module.html)

[KCoreAddons](kcoreaddons-module.md) provides classes built on top of [QtCore](https://doc.qt.io/qt-6/qtcore-module.html) to perform various tasks such as manipulating mime types, autosaving files, creating backup files, generating random sequences, performing text manipulations such as macro replacement, accessing user information and many more.

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

- [KCoreAddons C++ Classes](kcoreaddons-module.md)
- [KCoreAddons QML Types](../kcoreaddonsqml/org-kde-coreaddons-qmlmodule.md)
