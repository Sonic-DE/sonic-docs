---
title: "KExiv2"
description: "Todo."
---

# KExiv2

Todo.

libKExiv2 is a wrapper around [exiv2](https://exiv2.org/), providing read/write access to EXIF, IPTC and XMP metadata.

The main differences to exiv2 are:

- Functions take standard Qt containers as parameters
- Helper functions for GPS data
- Transparent XMP sidecar support

To get started, have a look at the [KExiv2Iface::KExiv2](kexiv2iface-kexiv2.md) class.

## Using the Module {#using-the-module}

Using a Qt module's C++ API requires linking against the module library, either directly or through other dependencies. Several build tools have dedicated support for this, including CMake and [qmake](https://doc.qt.io/qt-6/resources.html#qmake).

### Building with CMake {#building-with-cmake}

Use the `find_package()` command to locate the library:

```cpp
find_package(KExiv2Qt6 REQUIRED)
target_link_libraries(mytarget PRIVATE KExiv2Qt6)
```

For more details, see the [Build with CMake](https://doc.qt.io/qt-6/cmake-manual.html) overview.

## API Reference {#api-reference}

- [KExiv2 C++ Classes](kexiv2-module.md)

## Licenses {#licenses}

TODO
