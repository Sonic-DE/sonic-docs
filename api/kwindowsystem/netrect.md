---
title: "NETRect Struct"
description: "Simple rectangle class for NET classes."
---

# NETRect Struct

Simple rectangle class for NET classes. [More...](#details)

- **Header:** `#include <NETRect>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KWindowSystem)`  
  `target_link_libraries(mytarget PRIVATE KF6::KWindowSystem)`

[List of all members, including inherited members](netrect-members.md)

## Detailed Description {#details}

This class is a convenience class defining a rectangle as a point x,y with a size width by height. The existence of this class is to keep the implementation from being dependent on a separate framework/library;

[NETRect](netrect.md) is only used by the NET API. Usually [QRect](https://doc.qt.io/qt-6/qrect.html) is the appropriate class for representing a rectangle.

## Member Variable Documentation {#member-variable-documentation}

### NETPoint NETRect::pos {#pos-var}

This variable holds the position of the rectangle's top left corner.

*See also* [NETPoint](netpoint.md)

### NETSize NETRect::size {#size-var}

This variable holds the size of the rectangle.

*See also* [NETSize](netsize.md)
