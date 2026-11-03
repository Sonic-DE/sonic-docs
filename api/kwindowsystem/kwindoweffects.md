---
title: "KWindowEffects Namespace"
description: "Namespace for common standardized window effects."
---

# KWindowEffects Namespace

Namespace for common standardized window effects. [More...](#details)

- Header: KWindowEffects
- CMake: find\_package(KF6 REQUIRED COMPONENTS KWindowSystem) target\_link\_libraries(mytarget PRIVATE KF6::KWindowSystem)

## Detailed Description {#details}

## Type Documentation {#type-documentation}

### enum KWindowEffects::Effect {#Effect-enum}

| Constant |   |
| --- | --- |
| `KWindowEffects::Slide` | `1` |
| `KWindowEffects::BlurBehind` | `7` |
| `KWindowEffects::BackgroundContrast` | `9` |

### enum KWindowEffects::SlideFromLocation {#SlideFromLocation-enum}

| Constant |   |
| --- | --- |
| `KWindowEffects::NoEdge` | `0` |
| `KWindowEffects::TopEdge` | `1` |
| `KWindowEffects::RightEdge` | `2` |
| `KWindowEffects::BottomEdge` | `3` |
| `KWindowEffects::LeftEdge` | `4` |

## Function Documentation {#function-documentation}

### void KWindowEffects::enableBackgroundContrast(QWindow \**window*, bool *enable* = true, qreal *contrast* = 1, qreal *intensity* = 1, qreal *saturation* = 1, const QRegion &*region* = QRegion()) {#enableBackgroundContrast}

Instructs the window manager to modify the color of the background in the specified region behind the given window, in order to improve the contrast and readability of any text in the translucent window. The given region will overwrite any previous backgroundcontrast region. Passing a null region will enable the blur effect for the whole window. The region is relative to the top-left corner of the client area.

If `enable` is `false`, blur will be disabled for the whole window (`region` is ignored).

Note that you will usually want to set the region to the shape of the window, excluding any shadow or halo.

`window` The window for which to enable the background contrast effect

`enable` Enable the effect if `true`, disable it if `false`

`brightness` How to modify the area brightness: from 0 (make it black) to 2 (make it white), 1 leaves it unchanged

`region` The region within the window where the background will be modified, specified in logical pixels

### void KWindowEffects::enableBlurBehind(QWindow \**window*, bool *enable* = true, const QRegion &*region* = QRegion()) {#enableBlurBehind}

Instructs the window manager to blur the background in the specified region behind the given window. The given region will overwrite any previous blur-behind region. Passing a null region will enable the blur effect for the whole window. The region is relative to the top-left corner of the client area.

If `enable` is `false`, blur will be disabled for the whole window (`region` is ignored).

Note that you will usually want to set the region to the shape of the window, excluding any shadow or halo.

`window` The window for which to enable the blur effect

`enable` Enable the effect if `true`, disable it if `false`

`region` The region within the window where the background will be blurred, specified in logical pixels

### bool KWindowEffects::isEffectAvailable(KWindowEffects::Effect *effect*) {#isEffectAvailable}

Returns if an atom property is available

`effect` the effect we want to check

### void KWindowEffects::slideWindow(QWindow \**window*, KWindowEffects::SlideFromLocation *location*, int *offset* = -1) {#slideWindow}

Mark a window as sliding from screen edge

`id` of the window on which we want to apply the effect

`location` edge of the screen from which we want the sliding effect. Desktop and Floating won't have effect. `offset` distance in pixels from the screen edge defined by location
