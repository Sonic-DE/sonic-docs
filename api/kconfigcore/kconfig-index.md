---
title: "KConfig"
description: "Persistent platform-independent application settings."
---

# KConfig

Persistent platform-independent application settings.

[KConfig](kconfig.md) provides an advanced configuration system. It is made of two parts: [KConfigCore](kconfigcore-module.md) and [KConfigGui](../kconfiggui/kconfiggui-module.md).

[KConfigCore](kconfigcore-module.md) provides access to the configuration files themselves. It features:

- Code generation: describe your configuration in an XML file, and use kconfig\_compiler to generate classes that read and write configuration entries.
- Cascading configuration files (global settings overridden by local settings).
- Optional shell expansion support.
- The ability to lock down configuration options.

[KConfigGui](../kconfiggui/kconfiggui-module.md) provides a way to hook widgets to the configuration so that they are automatically initialized from the configuration and automatically propagate their changes to their respective configuration files.

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

- [KConfigCore C++ Classes](kconfigcore-module.md)
- [KConfigGui C++ Classes](../kconfiggui/kconfiggui-module.md)
- [KConfigQml C++ Classes](../kconfigqml/kconfigqml-module.md)
- [KConfig QML Types](../kconfigqml/org-kde-config-qmlmodule.md)
- [kconf\_update Tool](kconfupdate.md)
- [The KDE Configuration Compiler](kconfigcompiler.md)
- Obsolete Classes
