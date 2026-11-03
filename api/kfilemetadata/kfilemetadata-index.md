---
title: "KFileMetaData"
description: "Library for extracting the text and metadata from a number of different files."
---

# KFileMetaData

Library for extracting the text and metadata from a number of different files.

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

- [KFileMetaData C++ Classes](kfilemetadata-module.md)
