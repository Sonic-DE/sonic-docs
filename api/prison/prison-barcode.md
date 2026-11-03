---
title: "Prison::Barcode Class"
description: "This class was introduced in Qt 6.0."
---

# Prison::Barcode Class

This class was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <Prison/Barcode>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Prison)`  
  `target_link_libraries(mytarget PRIVATE KF6::Prison)`

[List of all members, including inherited members](prison-barcode-members.md)

## Public Types

- [enum Barcode::Dimensions](#Dimensions-enum)

## Public Functions

- [QColor backgroundColor() const](#backgroundColor)
- [QByteArray byteArrayData() const](#byteArrayData)
- [QString data() const](#data)
- [Prison::Barcode::Dimensions dimensions() const](#dimensions)
- [QColor foregroundColor() const](#foregroundColor)
- [Prison::BarcodeType format() const](#format)
- [QSizeF minimumSize() const](#minimumSize)
- [QSizeF preferredSize(qreal devicePixelRatio) const](#preferredSize)
- [void setBackgroundColor(const QColor &backgroundcolor)](#setBackgroundColor)
- [void setData(const QByteArray &data)](#setData)
- [void setData(const QString &data)](#setData-1)
- [void setForegroundColor(const QColor &foregroundcolor)](#setForegroundColor)
- [QImage toImage(const QSizeF &size)](#toImage)

## Static Public Members

- [std::optional\<Prison::Barcode\> create(Prison::BarcodeType type)](#create)

## Detailed Description {#details}

A barcode generator for a fixed barcode format.

> **Note:** This replaces Prison::createBarcode and AbstractBarcode\* from KF5. You can create Barcode instances directly now and specify the format in its constructor. Rather than checking for createBarcode returning a `nullptr`, check whether the format is not Prison::Null.

## Member Type Documentation {#member-type-documentation}

### enum Barcode::Dimensions {#Dimensions-enum}

Dimensions of the barcode.

| Constant | Value | Description |
| --- | --- | --- |
| `Prison::Barcode::NoDimensions` | `0` | Null barcode |
| `Prison::Barcode::OneDimension` | `1` | One-dimension barcode |
| `Prison::Barcode::TwoDimensions` | `2` | 2D matrix code |

## Member Function Documentation {#member-function-documentation}

### QColor Barcode::backgroundColor() const {#backgroundColor}

Returns the background color (by default white) to be used for the barcode.

*See also* [setBackgroundColor](prison-barcode.md#setBackgroundColor)()

### QByteArray Barcode::byteArrayData() const {#byteArrayData}

Binary data encoded in this barcode.

This returns an empty [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) if textual content is set.

*See also* [data](prison-barcode.md#data)()

### \[static\] std::optional\<Prison::Barcode\> Barcode::create(Prison::BarcodeType *type*) {#create}

Create a new barcode generator.

If a format is requested that is not supported by the current build due to missing/disabled optional dependencies, [Barcode::format](prison-barcode.md#format)() will return Prison::Null.

### QString Barcode::data() const {#data}

Textual content encoded in this barcode.

This returns an empty [QString](https://doc.qt.io/qt-6/qstring.html) if binary content is set.

*See also* [setData](prison-barcode.md#setData)(), [byteArrayData](prison-barcode.md#byteArrayData)()

### Prison::Barcode::Dimensions Barcode::dimensions() const {#dimensions}

Returns the amount of dimensions of the barcode.

### QColor Barcode::foregroundColor() const {#foregroundColor}

Returns the foreground color (by default black) to be used for the barcode.

*See also* [setForegroundColor](prison-barcode.md#setForegroundColor)()

### Prison::BarcodeType Barcode::format() const {#format}

Barcode format of this barcode generator.

### QSizeF Barcode::minimumSize() const {#minimumSize}

The minimal amount of pixels needed to represent this barcode without loss of information.

That is, the size of the barcode image if each line or dot is just one pixel wide. On normal screens that is not enough for barcode scanners to reliably detect the barcode though.

*See also* [preferredSize](prison-barcode.md#preferredSize)

### QSizeF Barcode::preferredSize(qreal *devicePixelRatio*) const {#preferredSize}

The recommended size for this barcode when shown on a screen.

This is typically significantly larger than trueMinimumSize() so that barcode scanners tend to reliably detect the code. As this depends on the physical resolution of the output, you have to pass the device pixel ration of the output screen here.

`devicePixelRatio` The device pixel ratio of the screen this is shown on.

*See also* trueMinimumSize

### void Barcode::setBackgroundColor(const QColor &*backgroundcolor*) {#setBackgroundColor}

sets the background color

`backgroundcolor` the new background color

*See also* [backgroundColor](prison-barcode.md#backgroundColor)()

### void Barcode::setData(const QByteArray &*data*) {#setData}

Sets binary data to be drawn as a barcode.

Prefer the [QString](https://doc.qt.io/qt-6/qstring.html) overload if your content is purely textual, to reduce the risk of encoding issues for non-ASCII content.

Calling this function does not do any repaints of anything, they are your own responsibility.

`data` binary barcode content

*See also* [data](prison-barcode.md#data)()

### void Barcode::setData(const QString &*data*) {#setData-1}

Sets textual data to be drawn as a barcode.

Only use this function if your content is textual, use the [QByteArray](https://doc.qt.io/qt-6/qbytearray.html) overload when your content contains non-textual binary content.

Calling this function does not do any repaints of anything, they are your own responsibility.

`data` textual barcode content

### void Barcode::setForegroundColor(const QColor &*foregroundcolor*) {#setForegroundColor}

sets the foreground color

`foregroundcolor` the new foreground color

*See also* [foregroundColor](prison-barcode.md#foregroundColor)()

### QImage Barcode::toImage(const QSizeF &*size*) {#toImage}

Creates a image with a barcode on

Returns [QImage](https://doc.qt.io/qt-6/qimage.html) with a barcode on, trying to match the requested `size`

If one of the dimensions of `size` is smaller than the matching dimension in [minimumSize](prison-barcode.md#minimumSize)(), a null [QImage](https://doc.qt.io/qt-6/qimage.html) will be returned
