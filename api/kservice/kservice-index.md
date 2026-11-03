---
title: "KService"
description: "KService allows to query information about installed applications and their associated file types."
---

# KService

KService allows to query information about installed applications and their associated file types.

[KService](kservice-module.md) allows to query information about installed applications and their associated file types.

The two relevant classes are:

- [KService](kservice-index.md): This models an installed application and allows to query various properties about it
- [KApplicationTrader](kapplicationtrader.md): This is used to list available applications as well as applications associated with a given file type

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

- [KService C++ Classes](kservice-module.md)
