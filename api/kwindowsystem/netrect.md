---
title: ""
description: "Simple rectangle class for NET classes."
---

# 

Simple rectangle class for NET classes. [More...](#details)

- Header: NETRect
- CMake: find\_package(KF6 REQUIRED COMPONENTS KWindowSystem) target\_link\_libraries(mytarget PRIVATE KF6::KWindowSystem)

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
