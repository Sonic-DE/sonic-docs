---
title: "NETIcon Struct"
description: "Simple icon class for NET classes."
---

# NETIcon Struct

Simple icon class for NET classes. [More...](#details)

- **Header:** `#include <NETIcon>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KWindowSystem)`  
  `target_link_libraries(mytarget PRIVATE KF6::KWindowSystem)`

[List of all members, including inherited members](neticon-members.md)

## Public Functions

- [NETIcon()](#NETIcon)

## Detailed Description {#details}

This class is a convenience class defining an icon of size width by height. The existence of this class is to keep the implementation from being dependent on a separate framework/library.

[NETIcon](neticon.md) is only used by the NET API. Usually [QIcon](https://doc.qt.io/qt-6/qicon.html) is the appropriate class for representing an icon.

## Member Function Documentation {#member-function-documentation}

### NETIcon::NETIcon() {#NETIcon}

Constructor to initialize this icon to 0x0 with data=0.

## Member Variable Documentation {#member-variable-documentation}

### unsigned char \* NETIcon::data {#data-var}

Image data for the icon.

This is an array of 32bit packed CARDINAL ARGB with high byte being A, low byte being B. First two bytes are width, height. Data is in rows, left to right and top to bottom.

### NETSize NETIcon::size {#size-var}

This variable holds the size of the icon.

*See also* [NETSize](netsize.md)
