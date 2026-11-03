---
title: "KWindowShadowTile Class"
description: "The KWindowShadowTile class provides a platform-indendent shadow tile representation."
---

# KWindowShadowTile Class

The [KWindowShadowTile](kwindowshadowtile.md) class provides a platform-indendent shadow tile representation. [More...](#details)

- **Header:** `#include <KWindowShadowTile>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KWindowSystem)`  
  `target_link_libraries(mytarget PRIVATE KF6::KWindowSystem)`

[List of all members, including inherited members](kwindowshadowtile-members.md)

## Public Types

- [\[alias\] KWindowShadowTile::Ptr](#Ptr-typedef)

## Public Functions

- [KWindowShadowTile()](#KWindowShadowTile)
- [bool create()](#create)
- [QImage image() const](#image)
- [bool isCreated() const](#isCreated)
- [void setImage(const QImage &image)](#setImage)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### \[alias\] KWindowShadowTile::Ptr {#Ptr-typedef}

## Member Function Documentation {#member-function-documentation}

### KWindowShadowTile::KWindowShadowTile() {#KWindowShadowTile}

### bool KWindowShadowTile::create() {#create}

Allocates the native platform resources associated with the [KWindowShadowTile](kwindowshadowtile.md).

Normally it should not be necessary to call this method as [KWindowShadow](kwindowshadow.md) will implicitly call create() on your behalf.

Returns `true` if the creation succeeded, otherwise returns `false`.

### QImage KWindowShadowTile::image() const {#image}

Returns the image stored in the [KWindowShadowTile](kwindowshadowtile.md).

*See also* [setImage](kwindowshadowtile.md#setImage)()

### bool KWindowShadowTile::isCreated() const {#isCreated}

Returns `true` if the platform resources associated with the tile have been allocated.

### void KWindowShadowTile::setImage(const QImage &*image*) {#setImage}

Sets the `image` on the [KWindowShadowTile](kwindowshadowtile.md).

Notice that once the native platform resources have been allocated for the tile, you are not allowed to change the image. In order to do so, you need to create a new tile.

*See also* [image](kwindowshadowtile.md#image)()
