---
title: "Syndication"
description: "RSS/Atom parser library."
---

# Syndication

RSS/Atom parser library.

Syndication is a parser library for RSS and Atom feeds.

RSS (0.9/1.0, 0.91..2.0) and Atom (0.3 and 1.0) feeds are supported.

Syndication offers a unified, format-agnostic view on the parsed feed, so that the using application does not need to distinguish between feed formats.

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

- [Syndication C++ Classes](syndication-module.md)
