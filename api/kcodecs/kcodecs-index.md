---
title: "KCodecs"
description: "Text encoding."
---

# KCodecs

Text encoding.

[KCodecs](kcodecs-module.md) provide a collection of methods to manipulate strings using various encodings.

It can automatically determine the charset of a string, translate XML entities, validate email addresses, and find encodings by name in a more tolerant way than [QTextCodec](https://doc.qt.io/qt-6/qtextcodec.html) (useful e.g. for data coming from the Internet).

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

- [KCodecs C++ Classes](kcodecs-module.md)
