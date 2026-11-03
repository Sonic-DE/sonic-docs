---
title: "Obsolete Members for KIconEffect"
description: "Deprecated members of KIconEffect."
parent: "kiconthemes/kiconeffect"
---

# Obsolete Members for KIconEffect

**The following members of class [KIconEffect](kiconeffect.md) are deprecated.** We strongly advise against using them in new code.

## Public Types

- [\[deprecated in 6.5\] enum KIconEffect::Effects](#Effects-enum)

## Public Functions

- [KIconEffect()](#KIconEffect) (deprecated in 6.5)
- [QImage apply(const QImage &src, int group, int state) const](#apply) (deprecated in 6.5)
- [QPixmap apply(const QPixmap &src, int group, int state) const](#apply-1) (deprecated in 6.5)
- [QImage apply(const QImage &src, int effect, float value, const QColor &rgb, bool trans) const](#apply-2) (deprecated in 6.5)
- [QPixmap apply(const QPixmap &src, int effect, float value, const QColor &rgb, bool trans) const](#apply-3) (deprecated in 6.5)
- [QImage apply(const QImage &src, int effect, float value, const QColor &rgb, const QColor &rgb2, bool trans) const](#apply-4) (deprecated in 6.5)
- [QPixmap apply(const QPixmap &src, int effect, float value, const QColor &rgb, const QColor &rgb2, bool trans) const](#apply-5) (deprecated in 6.5)
- [QImage doublePixels(const QImage &src) const](#doublePixels) (deprecated in 6.5)
- [QString fingerprint(int group, int state) const](#fingerprint) (deprecated in 6.5)
- [bool hasEffect(int group, int state) const](#hasEffect) (deprecated in 6.5)
- [void init()](#init) (deprecated in 6.5)

## Obsolete Member Type Documentation {#obsolete-member-type-documentation}

### \[deprecated in 6.5\] enum KIconEffect::Effects {#Effects-enum}

This enum is deprecated since 6.5. We strongly advise against using it in new code.

This is the enumeration of all possible icon effects.

| Constant | Value | Description |
| --- | --- | --- |
| `KIconEffect::NoEffect` | `0` | Do not apply any icon effect |
| `KIconEffect::ToGray` | `1` | Tints the icon gray |
| `KIconEffect::Colorize` | `2` | Tints the icon with a specific color |
| `KIconEffect::ToGamma` | `3` | Change the gamma value of the icon |
| `KIconEffect::DeSaturate` | `4` | Reduce the saturation of the icon |
| `KIconEffect::ToMonochrome` | `5` | Produces a monochrome icon |

use the static API

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[deprecated in 6.5\] KIconEffect::KIconEffect() {#KIconEffect}

This function is deprecated since 6.5. We strongly advise against using it in new code.

Create a new [KIconEffect](kiconeffect.md). You will most likely never have to use this to create a new [KIconEffect](kiconeffect.md) yourself, as you can use the [KIconEffect](kiconeffect.md) provided by the global [KIconLoader](kiconloader.md) (which itself is accessible by [KIconLoader::global](kiconloader.md#global)()) through its iconEffect() function.

use the static API

### \[deprecated in 6.5\] QImage KIconEffect::apply(const QImage &*src*, int *group*, int *state*) const {#apply}

This function is deprecated since 6.5. We strongly advise against using it in new code.

Applies an effect to an image. The effect to apply depends on the `group` and `state` parameters, and is configured by the user.

`src` The image.

`group` The group for the icon, see [KIconLoader::Group](kiconloader.md#Group-enum)

`state` The icon's state, see [KIconLoader::States](kiconloader.md#States-enum)

Returns An image with the effect applied.

use the static API

### \[deprecated in 6.5\] QPixmap KIconEffect::apply(const QPixmap &*src*, int *group*, int *state*) const {#apply-1}

This function is deprecated since 6.5. We strongly advise against using it in new code.

Applies an effect to a pixmap.

`src` The pixmap.

`group` The group for the icon, see [KIconLoader::Group](kiconloader.md#Group-enum)

`state` The icon's state, see [KIconLoader::States](kiconloader.md#States-enum)

Returns A pixmap with the effect applied.

use the static API

### \[deprecated in 6.5\] QImage KIconEffect::apply(const QImage &*src*, int *effect*, float *value*, const QColor &*rgb*, bool *trans*) const {#apply-2}

This function is deprecated since 6.5. We strongly advise against using it in new code.

Applies an effect to an image.

`src` The image.

`effect` The effect to apply, one of [KIconEffect::Effects](kiconeffect-obsolete.md#Effects-enum).

`value` Strength of the effect. 0 \<= `value` \<= 1.

`rgb` Color parameter for effects that need one.

`trans` Add Transparency if trans = true.

Returns An image with the effect applied.

use the static API

### \[deprecated in 6.5\] QPixmap KIconEffect::apply(const QPixmap &*src*, int *effect*, float *value*, const QColor &*rgb*, bool *trans*) const {#apply-3}

This function is deprecated since 6.5. We strongly advise against using it in new code.

Applies an effect to a pixmap.

`src` The pixmap.

`effect` The effect to apply, one of [KIconEffect::Effects](kiconeffect-obsolete.md#Effects-enum).

`value` Strength of the effect. 0 \<= `value` \<= 1.

`rgb` Color parameter for effects that need one.

`trans` Add Transparency if trans = true.

Returns A pixmap with the effect applied.

use the static API

### \[deprecated in 6.5\] QImage KIconEffect::apply(const QImage &*src*, int *effect*, float *value*, const QColor &*rgb*, const QColor &*rgb2*, bool *trans*) const {#apply-4}

This function is deprecated since 6.5. We strongly advise against using it in new code.

Applies an effect to an image.

`src` The image.

`effect` The effect to apply, one of [KIconEffect::Effects](kiconeffect-obsolete.md#Effects-enum).

`value` Strength of the effect. 0 \<= `value` \<= 1.

`rgb` Color parameter for effects that need one.

`trans` Add Transparency if trans = true.

Returns An image with the effect applied.

use the static API

### \[deprecated in 6.5\] QPixmap KIconEffect::apply(const QPixmap &*src*, int *effect*, float *value*, const QColor &*rgb*, const QColor &*rgb2*, bool *trans*) const {#apply-5}

This function is deprecated since 6.5. We strongly advise against using it in new code.

Applies an effect to a pixmap.

`src` The pixmap.

`effect` The effect to apply, one of [KIconEffect::Effects](kiconeffect-obsolete.md#Effects-enum).

`value` Strength of the effect. 0 \<= `value` \<= 1.

`rgb` Color parameter for effects that need one.

`trans` Add Transparency if trans = true.

Returns A pixmap with the effect applied.

use the static API

### \[deprecated in 6.5\] QImage KIconEffect::doublePixels(const QImage &*src*) const {#doublePixels}

This function is deprecated since 6.5. We strongly advise against using it in new code.

Returns an image twice as large, consisting of 2x2 pixels.

`src` the image.

Returns the scaled image.

use the static API

### \[deprecated in 6.5\] QString KIconEffect::fingerprint(int *group*, int *state*) const {#fingerprint}

This function is deprecated since 6.5. We strongly advise against using it in new code.

Returns a fingerprint for the effect by encoding the given `group` and `state` into a [QString](https://doc.qt.io/qt-6/qstring.html).

This is useful for caching.

`group` the group, see [KIconLoader::Group](kiconloader.md#Group-enum)

`state` the state, see [KIconLoader::States](kiconloader.md#States-enum)

Returns the fingerprint of the given `group` + `state`

use the static API

### \[deprecated in 6.5\] bool KIconEffect::hasEffect(int *group*, int *state*) const {#hasEffect}

This function is deprecated since 6.5. We strongly advise against using it in new code.

Tests whether an effect has been configured for the given icon group.

`group` the group to check, see [KIconLoader::Group](kiconloader.md#Group-enum)

`state` the state to check, see [KIconLoader::States](kiconloader.md#States-enum)

Returns true if an effect is configured for the given `group` in `state`, otherwise false.

use the static API

*See also* [KIconLoader::Group](kiconloader.md#Group-enum), [KIconLoader::States](kiconloader.md#States-enum)

### \[deprecated in 6.5\] void KIconEffect::init() {#init}

This function is deprecated since 6.5. We strongly advise against using it in new code.

Rereads configuration.

use the static API
