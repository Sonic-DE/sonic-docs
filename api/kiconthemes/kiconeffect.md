---
title: "KIconEffect Class"
description: "Applies effects to icons."
---

# KIconEffect Class

Applies effects to icons. [More...](#details)

- **Header:** `#include <KIconEffect>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS IconThemes)`  
  `target_link_libraries(mytarget PRIVATE KF6::IconThemes)`

[List of all members, including inherited members](kiconeffect-members.md)  
[Deprecated members](kiconeffect-obsolete.md)

## Static Public Members

- [void colorize(QImage &image, const QColor &col, float value)](#colorize)
- [void deSaturate(QImage &image, float value)](#deSaturate)
- [void overlay(QImage &src, QImage &overlay)](#overlay)
- [void semiTransparent(QImage &image)](#semiTransparent)
- [void semiTransparent(QPixmap &pixmap)](#semiTransparent-1)
- [void toActive(QImage &image)](#toActive) (since 6.5)
- [void toActive(QPixmap &pixmap)](#toActive-1) (since 6.5)
- [void toDisabled(QImage &image)](#toDisabled) (since 6.5)
- [void toDisabled(QPixmap &pixmap)](#toDisabled-1) (since 6.5)
- [void toGamma(QImage &image, float value)](#toGamma)
- [void toGray(QImage &image, float value)](#toGray)
- [void toMonochrome(QImage &image, const QColor &black, const QColor &white, float value)](#toMonochrome)

## Detailed Description {#details}

This class applies effects to icons depending on their state and group. For example, it can be used to make all disabled icons in a toolbar gray.

*See also* [QIcon::fromTheme](https://doc.qt.io/qt-6/qicon.html#fromTheme)

## Member Function Documentation {#member-function-documentation}

### \[static\] void KIconEffect::colorize(QImage &*image*, const QColor &*col*, float *value*) {#colorize}

Colorizes an image with a specific color.

`image` The image

`col` The color with which the `image` is tinted

`value` Strength of the effect. 0 \<= `value` \<= 1

### \[static\] void KIconEffect::deSaturate(QImage &*image*, float *value*) {#deSaturate}

Desaturates an image.

`image` The image

`value` Strength of the effect. 0 \<= `value` \<= 1

### \[static\] void KIconEffect::overlay(QImage &*src*, QImage &*overlay*) {#overlay}

Overlays an image with an other image.

`src` The image

`overlay` The image to overlay `src` with

### \[static\] void KIconEffect::semiTransparent(QImage &*image*) {#semiTransparent}

Renders an image semi-transparent.

`image` The image

### \[static\] void KIconEffect::semiTransparent(QPixmap &*pixmap*) {#semiTransparent-1}

Renders a pixmap semi-transparent.

`pixmap` The pixmap

### \[static, since 6.5\] void KIconEffect::toActive(QImage &*image*) {#toActive}

Applies an effect for an icon that is in an 'active' state

`image` The image

This function was introduced in Qt 6.5.

### \[static, since 6.5\] void KIconEffect::toActive(QPixmap &*pixmap*) {#toActive-1}

Applies an effect for an icon that is in an 'active' state

`pixmap` The image

This function was introduced in Qt 6.5.

### \[static, since 6.5\] void KIconEffect::toDisabled(QImage &*image*) {#toDisabled}

Applies a disabled effect

`image` The image

This function was introduced in Qt 6.5.

### \[static, since 6.5\] void KIconEffect::toDisabled(QPixmap &*pixmap*) {#toDisabled-1}

Applies a disabled effect

`pixmap` The image

This function was introduced in Qt 6.5.

### \[static\] void KIconEffect::toGamma(QImage &*image*, float *value*) {#toGamma}

Changes the gamma value of an image.

`image` The image

`value` Strength of the effect. 0 \<= `value` \<= 1

### \[static\] void KIconEffect::toGray(QImage &*image*, float *value*) {#toGray}

Tints an image gray.

`image` The image

`value` Strength of the effect. 0 \<= `value` \<= 1

### \[static\] void KIconEffect::toMonochrome(QImage &*image*, const QColor &*black*, const QColor &*white*, float *value*) {#toMonochrome}

Produces a monochrome icon with a given foreground and background color

`image` The image

`white` The color with which the white parts of `image` are painted

`black` The color with which the black parts of `image` are painted

`value` Strength of the effect. 0 \<= `value` \<= 1
