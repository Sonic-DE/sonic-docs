---
title: "Attica::Icon Class"
description: "The Icon class contains information about an icon."
---

# Attica::Icon Class

The Icon class contains information about an icon. [More...](#details)

- **Header:** `#include <Attica/Icon>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Attica)`  
  `target_link_libraries(mytarget PRIVATE KF6::Attica)`

[List of all members, including inherited members](attica-icon-members.md)

## Public Types

- [Icon::List](#List-typedef)

## Public Functions

- [Icon()](#Icon)
- [uint height() const](#height)
- [void setHeight(uint height)](#setHeight)
- [void setUrl(const QUrl &url)](#setUrl)
- [void setWidth(uint width)](#setWidth)
- [QUrl url() const](#url)
- [uint width() const](#width)

## Detailed Description {#details}

It consists of a Url and icon size information.

## Member Type Documentation {#member-type-documentation}

### Icon::List {#List-typedef}

## Member Function Documentation {#member-function-documentation}

### Icon::Icon() {#Icon}

Creates an empty Icon

### uint Icon::height() const {#height}

*See also* [setHeight](attica-icon.md#setHeight)()

### void Icon::setHeight(uint *height*) {#setHeight}

*See also* [height](attica-icon.md#height)()

### void Icon::setUrl(const QUrl &*url*) {#setUrl}

*See also* [url](attica-icon.md#url)()

### void Icon::setWidth(uint *width*) {#setWidth}

*See also* [width](attica-icon.md#width)()

### QUrl Icon::url() const {#url}

*See also* [setUrl](attica-icon.md#setUrl)()

### uint Icon::width() const {#width}

*See also* [setWidth](attica-icon.md#setWidth)()
