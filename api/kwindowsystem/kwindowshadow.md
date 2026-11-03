---
title: "KWindowShadow Class"
description: "The KWindowShadow class represents a drop-shadow that is drawn by the compositor."
---

# KWindowShadow Class

The [KWindowShadow](kwindowshadow.md) class represents a drop-shadow that is drawn by the compositor. [More...](#details)

- **Header:** `#include <KWindowShadow>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KWindowSystem)`  
  `target_link_libraries(mytarget PRIVATE KF6::KWindowSystem)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kwindowshadow-members.md)

## Public Functions

- [KWindowShadowTile::Ptr bottomLeftTile() const](#bottomLeftTile)
- [KWindowShadowTile::Ptr bottomRightTile() const](#bottomRightTile)
- [KWindowShadowTile::Ptr bottomTile() const](#bottomTile)
- [bool create()](#create)
- [void destroy()](#destroy)
- [bool isCreated() const](#isCreated)
- [KWindowShadowTile::Ptr leftTile() const](#leftTile)
- [QMargins padding() const](#padding)
- [KWindowShadowTile::Ptr rightTile() const](#rightTile)
- [void setBottomLeftTile(KWindowShadowTile::Ptr tile)](#setBottomLeftTile)
- [void setBottomRightTile(KWindowShadowTile::Ptr tile)](#setBottomRightTile)
- [void setBottomTile(KWindowShadowTile::Ptr tile)](#setBottomTile)
- [void setLeftTile(KWindowShadowTile::Ptr tile)](#setLeftTile)
- [void setPadding(const QMargins &padding)](#setPadding)
- [void setRightTile(KWindowShadowTile::Ptr tile)](#setRightTile)
- [void setTopLeftTile(KWindowShadowTile::Ptr tile)](#setTopLeftTile)
- [void setTopRightTile(KWindowShadowTile::Ptr tile)](#setTopRightTile)
- [void setTopTile(KWindowShadowTile::Ptr tile)](#setTopTile)
- [void setWindow(QWindow \*window)](#setWindow)
- [KWindowShadowTile::Ptr topLeftTile() const](#topLeftTile)
- [KWindowShadowTile::Ptr topRightTile() const](#topRightTile)
- [KWindowShadowTile::Ptr topTile() const](#topTile)
- [QWindow \*window() const](#window)

## Detailed Description {#details}

The [KWindowShadow](kwindowshadow.md) is composed of multiple tiles. The top left tile, the top right tile, the bottom left tile, and the bottom right tile are rendered as they are. The top tile and the bottom tile are stretched in x direction; the left tile and the right tile are stretched in y direction. Several [KWindowShadow](kwindowshadow.md) objects can share shadow tiles to reduce memory usage. You have to specify [padding](kwindowshadow.md#padding)() along the shadow tiles. The padding values indicate how much the [KWindowShadow](kwindowshadow.md) sticks outside the decorated window.

Once the [KWindowShadow](kwindowshadow.md) is created, you're not allowed to attach or detach any shadow tiles, change [padding](kwindowshadow.md#padding)(), or change [window](kwindowshadow.md#window)(). In order to do so, you have to [destroy](kwindowshadow.md#destroy)() the shadow first, update relevant properties, and [create](kwindowshadow.md#create)() the shadow again.

## Member Function Documentation {#member-function-documentation}

### KWindowShadowTile::Ptr KWindowShadow::bottomLeftTile() const {#bottomLeftTile}

Returns the bottom-left tile attached to the [KWindowShadow](kwindowshadow.md).

*See also* [setBottomLeftTile](kwindowshadow.md#setBottomLeftTile)()

### KWindowShadowTile::Ptr KWindowShadow::bottomRightTile() const {#bottomRightTile}

Returns the bottom-right tile attached to the [KWindowShadow](kwindowshadow.md).

*See also* [setBottomRightTile](kwindowshadow.md#setBottomRightTile)()

### KWindowShadowTile::Ptr KWindowShadow::bottomTile() const {#bottomTile}

Returns the bottom tile attached to the [KWindowShadow](kwindowshadow.md).

*See also* [setBottomTile](kwindowshadow.md#setBottomTile)()

### bool KWindowShadow::create() {#create}

Allocates the platform resources associated with the [KWindowShadow](kwindowshadow.md).

Once the native platform resources have been allocated, you're not allowed to attach or detach shadow tiles, change the padding or the target window. If you want to do so, you must [destroy](kwindowshadow.md#destroy)() the shadow, change relevant attributes and call create() again.

Returns `true` if the creation succeeded, otherwise returns `false`.

### void KWindowShadow::destroy() {#destroy}

Releases the platform resources associated with the [KWindowShadow](kwindowshadow.md).

Calling destroy() after [window](kwindowshadow.md#window)() had been destroyed will result in a no-op.

### bool KWindowShadow::isCreated() const {#isCreated}

Returns `true` if the platform resources associated with the shadow have been allocated.

### KWindowShadowTile::Ptr KWindowShadow::leftTile() const {#leftTile}

Returns the left tile attached to the [KWindowShadow](kwindowshadow.md).

*See also* [setLeftTile](kwindowshadow.md#setLeftTile)()

### QMargins KWindowShadow::padding() const {#padding}

Returns the padding of the [KWindowShadow](kwindowshadow.md).

The padding values specify the visible extents of the shadow. The top left tile is rendered with an offset of -padding().left() and -padding().top().

*See also* [setPadding](kwindowshadow.md#setPadding)()

### KWindowShadowTile::Ptr KWindowShadow::rightTile() const {#rightTile}

Returns the right tile attached to the [KWindowShadow](kwindowshadow.md).

*See also* [setRightTile](kwindowshadow.md#setRightTile)()

### void KWindowShadow::setBottomLeftTile(KWindowShadowTile::Ptr *tile*) {#setBottomLeftTile}

Attaches the bottom-left `tile` to the [KWindowShadow](kwindowshadow.md).

*See also* [bottomLeftTile](kwindowshadow.md#bottomLeftTile)()

### void KWindowShadow::setBottomRightTile(KWindowShadowTile::Ptr *tile*) {#setBottomRightTile}

Attaches the bottom-right `tile` to the [KWindowShadow](kwindowshadow.md).

*See also* [bottomRightTile](kwindowshadow.md#bottomRightTile)()

### void KWindowShadow::setBottomTile(KWindowShadowTile::Ptr *tile*) {#setBottomTile}

Attaches the bottom `tile` to the [KWindowShadow](kwindowshadow.md).

*See also* [bottomTile](kwindowshadow.md#bottomTile)()

### void KWindowShadow::setLeftTile(KWindowShadowTile::Ptr *tile*) {#setLeftTile}

Attaches the left `tile` to the [KWindowShadow](kwindowshadow.md).

*See also* [leftTile](kwindowshadow.md#leftTile)()

### void KWindowShadow::setPadding(const QMargins &*padding*) {#setPadding}

Sets the `padding` on the [KWindowShadow](kwindowshadow.md).

If the padding values are smaller than the sizes of the shadow tiles, then the shadow will overlap with the [window](kwindowshadow.md#window)() and will be rendered behind [window](kwindowshadow.md#window)(). E.g. if all padding values are set to 0, then the shadow will be completely occluded by the [window](kwindowshadow.md#window)().

*See also* [padding](kwindowshadow.md#padding)()

### void KWindowShadow::setRightTile(KWindowShadowTile::Ptr *tile*) {#setRightTile}

Attaches the right `tile` to the [KWindowShadow](kwindowshadow.md).

*See also* [rightTile](kwindowshadow.md#rightTile)()

### void KWindowShadow::setTopLeftTile(KWindowShadowTile::Ptr *tile*) {#setTopLeftTile}

Attaches the top-left `tile` to the [KWindowShadow](kwindowshadow.md).

*See also* [topLeftTile](kwindowshadow.md#topLeftTile)()

### void KWindowShadow::setTopRightTile(KWindowShadowTile::Ptr *tile*) {#setTopRightTile}

Attaches the top-right `tile` to the [KWindowShadow](kwindowshadow.md).

*See also* [topRightTile](kwindowshadow.md#topRightTile)()

### void KWindowShadow::setTopTile(KWindowShadowTile::Ptr *tile*) {#setTopTile}

Attaches the top `tile` to the [KWindowShadow](kwindowshadow.md).

*See also* [topTile](kwindowshadow.md#topTile)()

### void KWindowShadow::setWindow(QWindow \**window*) {#setWindow}

Sets the `window` behind which the [KWindowShadow](kwindowshadow.md) will be rendered.

Note that the [KWindowShadow](kwindowshadow.md) does not track the platform surface. If for whatever reason the native platform surface is deleted and then created, you must to [destroy](kwindowshadow.md#destroy)() the shadow and [create](kwindowshadow.md#create)() it again yourself.

*See also* [window](kwindowshadow.md#window)()

### KWindowShadowTile::Ptr KWindowShadow::topLeftTile() const {#topLeftTile}

Returns the top-left tile attached to the [KWindowShadow](kwindowshadow.md).

*See also* [setTopLeftTile](kwindowshadow.md#setTopLeftTile)()

### KWindowShadowTile::Ptr KWindowShadow::topRightTile() const {#topRightTile}

Returns the top-right tile attached to the [KWindowShadow](kwindowshadow.md).

*See also* [setTopRightTile](kwindowshadow.md#setTopRightTile)()

### KWindowShadowTile::Ptr KWindowShadow::topTile() const {#topTile}

Returns the top tile attached to the [KWindowShadow](kwindowshadow.md).

*See also* [setTopTile](kwindowshadow.md#setTopTile)()

### QWindow \*KWindowShadow::window() const {#window}

Returns the window behind which the [KWindowShadow](kwindowshadow.md) will be rendered.

*See also* [setWindow](kwindowshadow.md#setWindow)()
