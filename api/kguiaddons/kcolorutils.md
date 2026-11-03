---
title: "KColorUtils Namespace"
description: "A set of methods used to work with colors."
---

# KColorUtils Namespace

A set of methods used to work with colors. [More...](#details)

- Header: KColorUtils
- CMake: find\_package(KF6 REQUIRED COMPONENTS GuiAddons) target\_link\_libraries(mytarget PRIVATE KF6::GuiAddons)

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### qreal KColorUtils::chroma(*const QColor &*) {#chroma}

Calculate the chroma of a color. The range is from 0.0 (none) to 1.0 (full).

The result is computed in linear (not sRGB) color space.

*See also* [https://en.wikipedia.org/wiki/Colorfulness](https://en.wikipedia.org/wiki/Colorfulness)

### qreal KColorUtils::contrastRatio(*const QColor &*, *const QColor &*) {#contrastRatio}

Calculate the contrast ratio between two colors, according to the W3C/WCAG2.0 algorithm, (Lmax + 0.05)/(Lmin + 0.05), where Lmax and Lmin are the luma values of the lighter color and the darker color, respectively.

A contrast ration of 5:1 (result == 5.0) is the minimum for "normal" text to be considered readable (large text can go as low as 3:1). The ratio ranges from 1:1 (result == 1.0) to 21:1 (result == 21.0).

*See also* [KColorUtils::luma](kcolorutils.md#luma)

### QColor KColorUtils::darken(*const QColor &*, qreal *amount* = 0.5, qreal *chromaGain* = 1.0) {#darken}

Adjust the luma of a color by changing its distance from black.

- amount == 1.0 gives black
- amount == 0.5 results in a color whose luma is halfway between 0.0 and that of the original color
- amount == 0.0 gives the original color
- amount == -1.0 gives a color that is 'twice as far from black' as the original color, that is luma(result) == 2\*luma(color)

`amount` factor by which to adjust the luma component of the color `chromaGain` (optional) factor by which to adjust the chroma component of the color; 1.0 means no change, 0.0 minimizes chroma

*See also* [KColorUtils::shade](kcolorutils.md#shade)

### void KColorUtils::getHcy(*const QColor &*, qreal \**hue*, qreal \**chroma*, qreal \**luma*, qreal \**alpha* = nullptr) {#getHcy}

Calculate hue, chroma and luma of a color in one call.

The range of hue is from 0.0 (red) to almost 1.0 (slightly blue-ish red). The range of chroma is from 0.0 (none) to 1.0 (full). The range of luma is from 0.0 (black) to 1.0 (white).

The hue, chroma and luma values are computed in linear (not sRGB) color space.

### QColor KColorUtils::hcyColor(qreal *hue*, qreal *chroma*, qreal *luma*, qreal *alpha* = 1.0) {#hcyColor}

Return a [QColor](https://doc.qt.io/qt-6/qcolor.html) based on the given hue, chroma, luma and alpha values.

The range of hue is cyclical. For example, 0.0 and 1.0 are both red while -0.166667 and 0.833333 are both magenta. The range of chroma is from 0.0 (none) to 1.0 (full). Out of range values will be clamped. The range of luma is from 0.0 (black) to 1.0 (white). Out of range values will be clamped.

The hue, chroma and luma values are computed in linear (not sRGB) color space.

### qreal KColorUtils::hue(*const QColor &*) {#hue}

Calculate the hue of a color. The range is from 0.0 (red) to almost 1.0 (slightly blue-ish red).

The result is computed in linear (not sRGB) color space and may differ slightly from [QColor::hue](https://doc.qt.io/qt-6/qcolor.html#hue)().

*See also* [https://en.wikipedia.org/wiki/Hue](https://en.wikipedia.org/wiki/Hue)

### QColor KColorUtils::lighten(*const QColor &*, qreal *amount* = 0.5, qreal *chromaInverseGain* = 1.0) {#lighten}

Adjust the luma of a color by changing its distance from white.

- amount == 1.0 gives white
- amount == 0.5 results in a color whose luma is halfway between 1.0 and that of the original color
- amount == 0.0 gives the original color
- amount == -1.0 gives a color that is 'twice as far from white' as the original color, that is luma(result) == 1.0 - 2\*(1.0 - luma(color))

`amount` factor by which to adjust the luma component of the color

`chromaInverseGain` (optional) factor by which to adjust the chroma component of the color; 1.0 means no change, 0.0 maximizes chroma

*See also* [KColorUtils::shade](kcolorutils.md#shade)

### qreal KColorUtils::luma(*const QColor &*) {#luma}

Calculate the luma of a color. Luma is weighted sum of gamma-adjusted R'G'B' components of a color. The result is similar to [qGray](https://doc.qt.io/qt-6/qcolor.html#qGray). The range is from 0.0 (black) to 1.0 (white).

The result is computed in linear (not sRGB) color space.

[KColorUtils::darken](kcolorutils.md#darken)(), [KColorUtils::lighten](kcolorutils.md#lighten)() and [KColorUtils::shade](kcolorutils.md#shade)() operate on the luma of a color.

*See also* [http://en.wikipedia.org/wiki/Luma_(video)](http://en.wikipedia.org/wiki/Luma_(video))

### QColor KColorUtils::mix(const QColor &*c1*, const QColor &*c2*, qreal *bias* = 0.5) {#mix}

Blend two colors into a new color by linear combination.

```cpp
QColor lighter = KColorUtils::mix(myColor, Qt::white)
```

`c1` first color.

`c2` second color.

`bias` weight to be used for the mix. `bias` \<= 0 gives `c1`,

`bias` \>= 1 gives `c2`. `bias` == 0.5 gives a 50% blend of `c1` and `c2`.

### QColor KColorUtils::overlayColors(const QColor &*base*, const QColor &*paint*, QPainter::CompositionMode *comp* = QPainter::CompositionMode\_SourceOver) {#overlayColors}

Blend two colors into a new color by painting the second color over the first using the specified composition mode.

```cpp
QColor white(Qt::white);
white.setAlphaF(0.5);
QColor lighter = KColorUtils::overlayColors(myColor, white);
```

`base` the base color (alpha channel is ignored).

`paint` the color to be overlaid onto the base color.

`comp` the CompositionMode used to do the blending.

### QColor KColorUtils::shade(*const QColor &*, qreal *lumaAmount*, qreal *chromaAmount* = 0.0) {#shade}

Adjust the luma and chroma components of a color. The amount is added to the corresponding component.

`lumaAmount` amount by which to adjust the luma component of the color; 0.0 results in no change, -1.0 turns anything black, 1.0 turns anything white

`chromaAmount` (optional) amount by which to adjust the chroma component of the color; 0.0 results in no change, -1.0 minimizes chroma, 1.0 maximizes chroma

*See also* [KColorUtils::luma](kcolorutils.md#luma)

### QColor KColorUtils::tint(const QColor &*base*, const QColor &*color*, qreal *amount* = 0.3) {#tint}

Create a new color by tinting one color with another. This function is meant for creating additional colors withings the same class (background, foreground) from colors in a different class. Therefore when `amount` is low, the luma of `base` is mostly preserved, while the hue and chroma of `color` is mostly inherited.

`base` color to be tinted

`color` color with which to tint

`amount` how strongly to tint the base; 0.0 gives @p base, 1.0 gives @p color
