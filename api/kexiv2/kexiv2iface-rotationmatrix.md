---
title: "KExiv2Iface::RotationMatrix Class"
description: "Todo."
---

# KExiv2Iface::RotationMatrix Class

Todo. [More...](#details)

- **Header:** `#include <KExiv2/RotationMatrix>`
- **CMake:** `find_package(KExiv2Qt6 REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE KExiv2Qt6)`

[List of all members, including inherited members](kexiv2iface-rotationmatrix-members.md)

## Public Types

- [enum RotationMatrix::TransformationAction](#TransformationAction-enum)

## Public Functions

- [RotationMatrix()](#RotationMatrix)
- [RotationMatrix(KExiv2Iface::KExiv2::ImageOrientation exifOrientation)](#RotationMatrix-1)
- [RotationMatrix(KExiv2Iface::RotationMatrix::TransformationAction action)](#RotationMatrix-2)
- [KExiv2Iface::KExiv2::ImageOrientation exifOrientation() const](#exifOrientation)
- [bool isNoTransform() const](#isNoTransform)
- [QTransform toTransform() const](#toTransform)
- [QList\<KExiv2Iface::RotationMatrix::TransformationAction\> transformations() const](#transformations)
- [bool RotationMatrix::operator!=(const KExiv2Iface::RotationMatrix &ma) const](#operator-not-eq)
- [KExiv2Iface::RotationMatrix &RotationMatrix::operator\*=(KExiv2Iface::KExiv2::ImageOrientation exifOrientation)](#operator-2a-eq)
- [KExiv2Iface::RotationMatrix &RotationMatrix::operator\*=(KExiv2Iface::RotationMatrix::TransformationAction action)](#operator-2a-eq-1)
- [KExiv2Iface::RotationMatrix &RotationMatrix::operator\*=(QList\<KExiv2Iface::RotationMatrix::TransformationAction\> actions)](#operator-2a-eq-2)
- [KExiv2Iface::RotationMatrix &RotationMatrix::operator\*=(const KExiv2Iface::RotationMatrix &ma)](#operator-2a-eq-3)
- [bool RotationMatrix::operator==(const KExiv2Iface::RotationMatrix &ma) const](#operator-eq-eq)

## Static Public Members

- [QTransform toTransform(KExiv2Iface::KExiv2::ImageOrientation orientation)](#toTransform-1)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum RotationMatrix::TransformationAction {#TransformationAction-enum}

This describes single transform primitives.

Note some of the defined Exif rotation flags combine two of these actions.

The enum values correspond to those defined as JXFORM\_CODE in the often used the JPEG tool transupp.h.

| Constant | Value | Description |
| --- | --- | --- |
| `KExiv2Iface::RotationMatrix::NoTransformation` | `0` | No transformation |
| `KExiv2Iface::RotationMatrix::FlipHorizontal` | `1` | Horizontal flip |
| `KExiv2Iface::RotationMatrix::FlipVertical` | `2` | Vertical flip |
| `KExiv2Iface::RotationMatrix::Rotate90` | `5` | 90-degree clockwise rotation |
| `KExiv2Iface::RotationMatrix::Rotate180` | `6` | 180-degree rotation |
| `KExiv2Iface::RotationMatrix::Rotate180` | `6` | 270-degree clockwise (or 90 ccw) |

## Member Function Documentation {#member-function-documentation}

### RotationMatrix::RotationMatrix() {#RotationMatrix}

Constructs the identity matrix (the matrix describing no transformation).

### RotationMatrix::RotationMatrix(KExiv2Iface::KExiv2::ImageOrientation *exifOrientation*) {#RotationMatrix-1}

Returns the matrix corresponding to the given [TransformationAction](kexiv2iface-rotationmatrix.md#TransformationAction-enum).

### RotationMatrix::RotationMatrix(KExiv2Iface::RotationMatrix::TransformationAction *action*) {#RotationMatrix-2}

Returns the matrix corresponding to the given [TransformationAction](kexiv2iface-rotationmatrix.md#TransformationAction-enum).

### KExiv2Iface::KExiv2::ImageOrientation RotationMatrix::exifOrientation() const {#exifOrientation}

Returns the Exif orienation flag describing this matrix.

Returns ORIENTATION\_UNSPECIFIED if no flag matches this matrix.

### bool RotationMatrix::isNoTransform() const {#isNoTransform}

Returns true of this matrix describes no transformation (is the identity matrix).

### QTransform RotationMatrix::toTransform() const {#toTransform}

Returns a QTransform representing this matrix.

### \[static\] QTransform RotationMatrix::toTransform(KExiv2Iface::KExiv2::ImageOrientation *orientation*) {#toTransform-1}

Returns a QTransform for the given Exif orientation.

### QList\<KExiv2Iface::RotationMatrix::TransformationAction\> RotationMatrix::transformations() const {#transformations}

Returns the actions described by this matrix. The order matters.

Not all possible matrices are supported, but all those that can be combined by Exif rotation flags and the transform actions above.

If [isNoTransform](kexiv2iface-rotationmatrix.md#isNoTransform)() or the matrix is not supported returns an empty list.

### bool RotationMatrix::operator!=(const KExiv2Iface::RotationMatrix &*ma*) const {#operator-not-eq}

### KExiv2Iface::RotationMatrix &RotationMatrix::operator\*=(KExiv2Iface::KExiv2::ImageOrientation *exifOrientation*) {#operator-2a-eq}

Applies the given Exif orientation flag to this matrix.

### KExiv2Iface::RotationMatrix &RotationMatrix::operator\*=(KExiv2Iface::RotationMatrix::TransformationAction *action*) {#operator-2a-eq-1}

Applies the given transform to this matrix.

### KExiv2Iface::RotationMatrix &RotationMatrix::operator\*=(QList\<KExiv2Iface::RotationMatrix::TransformationAction\> *actions*) {#operator-2a-eq-2}

Applies the given transform actions to this matrix.

### KExiv2Iface::RotationMatrix &RotationMatrix::operator\*=(const KExiv2Iface::RotationMatrix &*ma*) {#operator-2a-eq-3}

### bool RotationMatrix::operator==(const KExiv2Iface::RotationMatrix &*ma*) const {#operator-eq-eq}
