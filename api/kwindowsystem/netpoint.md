---
title: ""
description: "Simple point class for NET classes."
---

# 

Simple point class for NET classes. [More...](#details)

- Header: netwm\_def.h
- CMake: find\_package(KF6 REQUIRED COMPONENTS KWindowSystem) target\_link\_libraries(mytarget PRIVATE KF6::KWindowSystem)

## Detailed Description {#details}

This class is a convenience class defining a point x, y. The existence of this class is to keep the implementation from being dependent on a separate framework/library.

[NETPoint](netpoint.md) is only used by the NET API. Usually [QPoint](https://doc.qt.io/qt-6/qpoint.html) is the appropriate class for representing a point.

## Member Function Documentation {#member-function-documentation}

### NETPoint::NETPoint() {#NETPoint}

Constructor to initialize this point to 0,0.

## Member Variable Documentation {#member-variable-documentation}

### int NETPoint::x {#x-var}

This variable holds the point's X coordinate.

### int NETPoint::y {#y-var}

This variable holds the point's Y coordinate.
