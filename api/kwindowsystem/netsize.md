---
title: ""
description: "Simple size class for NET classes."
---

# 

Simple size class for NET classes. [More...](#details)

- Header: NETSize
- CMake: find\_package(KF6 REQUIRED COMPONENTS KWindowSystem) target\_link\_libraries(mytarget PRIVATE KF6::KWindowSystem)

## Detailed Description {#details}

This class is a convenience class defining a size width by height. The existence of this class is to keep the implementation from being dependent on a separate framework/library.

[NETSize](netsize.md) is only used by the NET API. Usually [QSize](https://doc.qt.io/qt-6/qsize.html) is the appropriate class for representing a size.

## Member Function Documentation {#member-function-documentation}

### NETSize::NETSize() {#NETSize}

Constructor to initialize this size to 0x0

## Member Variable Documentation {#member-variable-documentation}

### int NETSize::height {#height-var}

The size's height.

### int NETSize::width {#width-var}

The size's width.
