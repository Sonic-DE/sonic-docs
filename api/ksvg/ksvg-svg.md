---
title: "KSvg::Svg Class"
description: "A theme aware image-centric SVG class."
---

# KSvg::Svg Class

A theme aware image-centric SVG class. [More...](#details)

- **Header:** `#include <KSvg/Svg>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Svg)`  
  `target_link_libraries(mytarget PRIVATE KF6::Svg)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)
- **Inherited By:** [KSvg::FrameSvg](ksvg-framesvg.md)

[List of all members, including inherited members](ksvg-svg-members.md)

## Public Types

- [enum Svg::ColorSet](#ColorSet-enum)
- [enum Svg::Status](#Status-enum)
- [enum Svg::StyleSheetColor](#StyleSheetColor-enum)

## Properties

- [colorSet : KSvg::Svg::ColorSet](#colorSet-prop)
- [\[read-only\] fromCurrentImageSet : bool](#fromCurrentImageSet-prop)
- [imagePath : QString](#imagePath-prop)
- [multipleImages : bool](#multipleImages-prop)
- [size : QSizeF](#size-prop)
- [status : KSvg::Svg::Status](#status-prop)
- [usingRenderingCache : bool](#usingRenderingCache-prop)

## Public Functions

- [Svg(QObject \*parent = nullptr)](#Svg)
- [void clearColorOverrides()](#clearColorOverrides)
- [QColor color(KSvg::Svg::StyleSheetColor colorName) const](#color)
- [QMap\<KSvg::Svg::StyleSheetColor, QColor\> colorOverrides() const](#colorOverrides) (since 6.18)
- [KSvg::Svg::ColorSet colorSet() const](#colorSet)
- [bool containsMultipleImages() const](#containsMultipleImages)
- [qreal devicePixelRatio() const](#devicePixelRatio)
- [QRectF elementRect(QStringView elementId) const](#elementRect)
- [QRectF elementRect(const QString &elementId) const](#elementRect-1)
- [QSizeF elementSize(const QString &elementId) const](#elementSize)
- [bool fromCurrentImageSet() const](#fromCurrentImageSet)
- [bool hasElement(QStringView elementId) const](#hasElement)
- [bool hasElement(const QString &elementId) const](#hasElement-1)
- [QImage image(const QSize &size, const QString &elementID = QString())](#image)
- [QString imagePath() const](#imagePath)
- [KSvg::ImageSet \*imageSet() const](#imageSet)
- [bool isUsingRenderingCache() const](#isUsingRenderingCache)
- [bool isValid() const](#isValid)
- [void paint(QPainter \*painter, const QPointF &point, const QString &elementID = QString())](#paint)
- [void paint(QPainter \*painter, const QRectF &rect, const QString &elementID = QString())](#paint-1)
- [void paint(QPainter \*painter, int x, int y, const QString &elementID = QString())](#paint-2)
- [void paint(QPainter \*painter, int x, int y, int width, int height, const QString &elementID = QString())](#paint-3)
- [QPixmap pixmap(const QString &elementID = QString())](#pixmap)
- [void resize()](#resize)
- [void resize(const QSizeF &size)](#resize-1)
- [void resize(qreal width, qreal height)](#resize-2)
- [void setColor(KSvg::Svg::StyleSheetColor colorName, const QColor &color)](#setColor)
- [void setColorSet(KSvg::Svg::ColorSet colorSet)](#setColorSet)
- [void setColors(const QMap\<KSvg::Svg::StyleSheetColor, QColor\> &colors)](#setColors) (since 6.18)
- [void setContainsMultipleImages(bool multiple)](#setContainsMultipleImages)
- [void setDevicePixelRatio(qreal factor)](#setDevicePixelRatio)
- [void setImagePath(const QString &svgFilePath)](#setImagePath)
- [void setImageSet(KSvg::ImageSet \*theme)](#setImageSet)
- [void setStatus(KSvg::Svg::Status status)](#setStatus)
- [void setUsingRenderingCache(bool useCache)](#setUsingRenderingCache)
- [QSizeF size() const](#size)
- [KSvg::Svg::Status status() const](#status)

## Signals

- [void colorHintChanged()](#colorHintChanged)
- [void colorSetChanged(KSvg::Svg::ColorSet colorSet)](#colorSetChanged)
- [void fromCurrentImageSetChanged(bool fromCurrentImageSet)](#fromCurrentImageSetChanged)
- [void imagePathChanged()](#imagePathChanged)
- [void imageSetChanged(KSvg::ImageSet \*imageSet)](#imageSetChanged)
- [void repaintNeeded()](#repaintNeeded)
- [void sizeChanged()](#sizeChanged)
- [void statusChanged(KSvg::Svg::Status status)](#statusChanged)

## Detailed Description {#details}

[KSvg::Svg](ksvg-svg.md) provides a class for rendering SVG images to a [QPainter](https://doc.qt.io/qt-6/qpainter.html) in a convenient manner. Unless an absolute path to a file is provided, it loads the SVG document using [KSvg::ImageSet](ksvg-imageset.md). It also provides a number of internal optimizations to help lower the cost of painting SVGs, such as caching.

*See also* [KSvg::FrameSvg](ksvg-index.md)

## Member Type Documentation {#member-type-documentation}

### enum Svg::ColorSet {#ColorSet-enum}

| Constant |   |
| --- | --- |
| `KSvg::Svg::View` | `0` |
| `KSvg::Svg::Window` | `1` |
| `KSvg::Svg::Button` | `2` |
| `KSvg::Svg::Selection` | `3` |
| `KSvg::Svg::Tooltip` | `4` |
| `KSvg::Svg::Complementary` | `5` |
| `KSvg::Svg::Header` | `6` |

### enum Svg::Status {#Status-enum}

| Constant |   |
| --- | --- |
| `KSvg::Svg::Normal` | `0` |
| `KSvg::Svg::Selected` | `1` |
| `KSvg::Svg::Inactive` | `2` |

### enum Svg::StyleSheetColor {#StyleSheetColor-enum}

| Constant |   |
| --- | --- |
| `KSvg::Svg::Text` | `0` |
| `KSvg::Svg::Background` | `1` |
| `KSvg::Svg::Highlight` | `2` |
| `KSvg::Svg::HighlightedText` | `3` |
| `KSvg::Svg::PositiveText` | `4` |
| `KSvg::Svg::NeutralText` | `5` |
| `KSvg::Svg::NegativeText` | `6` |
| `KSvg::Svg::ButtonText` | `7` |
| `KSvg::Svg::ButtonBackground` | `8` |
| `KSvg::Svg::ButtonHover` | `9` |
| `KSvg::Svg::ButtonFocus` | `10` |
| `KSvg::Svg::ButtonHighlightedText` | `11` |
| `KSvg::Svg::ButtonPositiveText` | `12` |
| `KSvg::Svg::ButtonNeutralText` | `13` |
| `KSvg::Svg::ButtonNegativeText` | `14` |
| `KSvg::Svg::ViewText` | `15` |
| `KSvg::Svg::ViewBackground` | `16` |
| `KSvg::Svg::ViewHover` | `17` |
| `KSvg::Svg::ViewFocus` | `18` |
| `KSvg::Svg::ViewHighlightedText` | `19` |
| `KSvg::Svg::ViewPositiveText` | `20` |
| `KSvg::Svg::ViewNeutralText` | `21` |
| `KSvg::Svg::ViewNegativeText` | `22` |
| `KSvg::Svg::TooltipText` | `23` |
| `KSvg::Svg::TooltipBackground` | `24` |
| `KSvg::Svg::TooltipHover` | `25` |
| `KSvg::Svg::TooltipFocus` | `26` |
| `KSvg::Svg::TooltipHighlightedText` | `27` |
| `KSvg::Svg::TooltipPositiveText` | `28` |
| `KSvg::Svg::TooltipNeutralText` | `29` |
| `KSvg::Svg::TooltipNegativeText` | `30` |
| `KSvg::Svg::ComplementaryText` | `31` |
| `KSvg::Svg::ComplementaryBackground` | `32` |
| `KSvg::Svg::ComplementaryHover` | `33` |
| `KSvg::Svg::ComplementaryFocus` | `34` |
| `KSvg::Svg::ComplementaryHighlightedText` | `35` |
| `KSvg::Svg::ComplementaryPositiveText` | `36` |
| `KSvg::Svg::ComplementaryNeutralText` | `37` |
| `KSvg::Svg::ComplementaryNegativeText` | `38` |
| `KSvg::Svg::HeaderText` | `39` |
| `KSvg::Svg::HeaderBackground` | `40` |
| `KSvg::Svg::HeaderHover` | `41` |
| `KSvg::Svg::HeaderFocus` | `42` |
| `KSvg::Svg::HeaderHighlightedText` | `43` |
| `KSvg::Svg::HeaderPositiveText` | `44` |
| `KSvg::Svg::HeaderNeutralText` | `45` |
| `KSvg::Svg::HeaderNegativeText` | `46` |
| `KSvg::Svg::Frame` | `47` |

## Property Documentation {#property-documentation}

### colorSet : KSvg::Svg::ColorSet {#colorSet-prop}

**Access functions:**

- `KSvg::Svg::ColorSet` **[colorSet](ksvg-svg.md#colorSet)**() const
- `void` **[setColorSet](ksvg-svg.md#setColorSet)**(`KSvg::Svg::ColorSet` *colorSet*)

**Notifier signal:**

- `void` **[colorSetChanged](ksvg-svg.md#colorSetChanged)**(`KSvg::Svg::ColorSet` *colorSet*)

### \[read-only\] fromCurrentImageSet : bool {#fromCurrentImageSet-prop}

**Access functions:**

- `bool` **[fromCurrentImageSet](ksvg-svg.md#fromCurrentImageSet)**() const

**Notifier signal:**

- `void` **[fromCurrentImageSetChanged](ksvg-svg.md#fromCurrentImageSetChanged)**(`bool` *fromCurrentImageSet*)

### imagePath : QString {#imagePath-prop}

**Access functions:**

- `QString` **[imagePath](ksvg-svg.md#imagePath)**() const
- virtual `void` **[setImagePath](ksvg-svg.md#setImagePath)**(const `QString` &*svgFilePath*)

**Notifier signal:**

- `void` **[imagePathChanged](ksvg-svg.md#imagePathChanged)**()

### multipleImages : bool {#multipleImages-prop}

**Access functions:**

- `bool` **[containsMultipleImages](ksvg-svg.md#containsMultipleImages)**() const
- `void` **[setContainsMultipleImages](ksvg-svg.md#setContainsMultipleImages)**(`bool` *multiple*)

### size : QSizeF {#size-prop}

**Access functions:**

- `QSizeF` **[size](ksvg-svg.md#size)**() const
- `void` **[resize](ksvg-svg.md#resize-2)**(`qreal` *width*, `qreal` *height*)
- `void` **[resize](ksvg-svg.md#resize-1)**(const `QSizeF` &*size*)
- `void` **[resize](ksvg-svg.md#resize)**()

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

**Notifier signal:**

- `void` **[sizeChanged](ksvg-svg.md#sizeChanged)**()

### status : KSvg::Svg::Status {#status-prop}

**Access functions:**

- `KSvg::Svg::Status` **[status](ksvg-svg.md#status)**() const
- `void` **[setStatus](ksvg-svg.md#setStatus)**(`KSvg::Svg::Status` *status*)

**Notifier signal:**

- `void` **[statusChanged](ksvg-svg.md#statusChanged)**(`KSvg::Svg::Status` *status*)

### usingRenderingCache : bool {#usingRenderingCache-prop}

**Access functions:**

- `bool` **[isUsingRenderingCache](ksvg-svg.md#isUsingRenderingCache)**() const
- `void` **[setUsingRenderingCache](ksvg-svg.md#setUsingRenderingCache)**(`bool` *useCache*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Svg::Svg(QObject \**parent* = nullptr) {#Svg}

This method constructs an SVG object that implicitly shares and caches rendering.

Unlike QSvgRenderer, which this class uses internally, [KSvg::Svg](ksvg-svg.md) represents an image generated from an SVG. As such, it has a related size and transform matrix (the latter being provided by the painter used to paint the image).

The size is initialized to be the SVG's native size.

`parent` options [QObject](https://doc.qt.io/qt-6/qobject.html) to parent this to

*See also* [KSvg::ImageSet](ksvg-index.md)

### void Svg::clearColorOverrides() {#clearColorOverrides}

### QColor Svg::color(KSvg::Svg::StyleSheetColor *colorName*) const {#color}

*See also* [setColor](ksvg-svg.md#setColor)()

### \[signal\] void Svg::colorHintChanged() {#colorHintChanged}

This signal is emitted whenever the color hint has changed.

### \[since 6.18\] QMap\<KSvg::Svg::StyleSheetColor, QColor\> Svg::colorOverrides() const {#colorOverrides}

Returns the color overrides.

This function was introduced in Qt 6.18.

### KSvg::Svg::ColorSet Svg::colorSet() const {#colorSet}

Returns the color set for this Svg

> **Note:** Getter function for property [colorSet](ksvg-svg.md#colorSet-prop).

*See also* [setColorSet](ksvg-svg.md#setColorSet)()

### \[signal\] void Svg::colorSetChanged(KSvg::Svg::ColorSet *colorSet*) {#colorSetChanged}

This signal is emitted when the color set has changed.

> **Note:** Notifier signal for property [colorSet](ksvg-svg.md#colorSet-prop).

### bool Svg::containsMultipleImages() const {#containsMultipleImages}

This method returns whether the SVG contains multiple images.

If this is `true`, the SVG will be treated as a collection of related images, rather than a consistent drawing.

Returns `true` if the SVG will be treated as containing multiple images, `false` if it will be treated as a coherent image.

> **Note:** Getter function for property [multipleImages](ksvg-svg.md#multipleImages-prop).

*See also* [setContainsMultipleImages](ksvg-svg.md#setContainsMultipleImages)()

### qreal Svg::devicePixelRatio() const {#devicePixelRatio}

This method returns the device pixel ratio for this Svg.

*See also* [setDevicePixelRatio](ksvg-svg.md#setDevicePixelRatio)()

### QRectF Svg::elementRect(QStringView *elementId*) const {#elementRect}

### \[invokable\] QRectF Svg::elementRect(const QString &*elementId*) const {#elementRect-1}

This method returns the bounding rect of a given element.

This is the bounding rect of the element with ID `elementId` after the SVG has been scaled (see [resize](ksvg-svg.md#resize)()). Note that this is unaffected by the [containsMultipleImages](ksvg-svg.md#containsMultipleImages) property.

`elementId` the id of the element to check

Returns the current rect of a given element, given the current size of the SVG

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] QSizeF Svg::elementSize(const QString &*elementId*) const {#elementSize}

This method returns the size of a given element.

This is the size of the element with ID `elementId` after the SVG has been scaled (see [resize](ksvg-svg.md#resize)()). Note that this is unaffected by the [containsMultipleImages](ksvg-svg.md#containsMultipleImages) property.

`elementId` the id of the element to check

Returns the size of a given element, given the current size of the SVG

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### bool Svg::fromCurrentImageSet() const {#fromCurrentImageSet}

This method returns whether the current theme has this SVG, without having to fall back to the default theme.

Returns true if the svg is loaded from the current theme

> **Note:** Getter function for property [fromCurrentImageSet](ksvg-svg.md#fromCurrentImageSet-prop).

*See also* [ImageSet::currentImageSetHasImage](ksvg-imageset.md#currentImageSetHasImage)

### \[signal\] void Svg::fromCurrentImageSetChanged(bool *fromCurrentImageSet*) {#fromCurrentImageSetChanged}

This signal is emitted when the value of [fromCurrentImageSet](ksvg-svg.md#fromCurrentImageSet)() has changed.

> **Note:** Notifier signal for property [fromCurrentImageSet](ksvg-svg.md#fromCurrentImageSet-prop).

### bool Svg::hasElement(QStringView *elementId*) const {#hasElement}

### \[invokable\] bool Svg::hasElement(const QString &*elementId*) const {#hasElement-1}

This method checks whether an element exists in the loaded SVG.

`elementId` the id of the element to check for

Returns `true` if the element is defined in the SVG, otherwise `false`

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] QImage Svg::image(const QSize &*size*, const QString &*elementID* = QString()) {#image}

This method returns an image of the SVG represented by this object.

The size of the image will be the size of this Svg object ([size](ksvg-svg.md#size)()) if [containsMultipleImages](ksvg-svg.md#containsMultipleImages) is `true`; otherwise, it will be the size of the requested element after the whole SVG has been scaled to [size](ksvg-svg.md#size)().

`elementID` the ID string of the element to render, or an empty string for the whole SVG (the default)

Returns a [QPixmap](https://doc.qt.io/qt-6/qpixmap.html) of the rendered SVG

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### QString Svg::imagePath() const {#imagePath}

This method returns the SVG file to render.

If this SVG is themed, this will be a relative path, and will not include a file extension.

Returns either an absolute path to an SVG file, or an image name

> **Note:** Getter function for property [imagePath](ksvg-svg.md#imagePath-prop).

*See also* [setImagePath](ksvg-svg.md#setImagePath)(), [ImageSet::imagePath](ksvg-imageset.md#imagePath)()

### \[signal\] void Svg::imagePathChanged() {#imagePathChanged}

This signal is emitted whenever the image path has changed.

> **Note:** Notifier signal for property [imagePath](ksvg-svg.md#imagePath-prop).

### KSvg::ImageSet \*Svg::imageSet() const {#imageSet}

This method returns the [KSvg::ImageSet](ksvg-imageset.md) used by this Svg object.

This determines how relative image paths are interpreted.

Returns the theme used by this Svg

*See also* [setImageSet](ksvg-svg.md#setImageSet)()

### \[signal\] void Svg::imageSetChanged(KSvg::ImageSet \**imageSet*) {#imageSetChanged}

This signal is emitted when the image set has changed.

### bool Svg::isUsingRenderingCache() const {#isUsingRenderingCache}

Whether the rendering cache is being used.

This method returns whether the Svg object is using caching for rendering results.

> **Note:** Getter function for property [usingRenderingCache](ksvg-svg.md#usingRenderingCache-prop).

### \[invokable\] bool Svg::isValid() const {#isValid}

This method checks whether this object is backed by a valid SVG file.

This method can be expensive as it causes disk access.

Returns `true` if the SVG file exists and the document is valid, otherwise `false`.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void Svg::paint(QPainter \**painter*, const QPointF &*point*, const QString &*elementID* = QString()) {#paint}

This method paints all or part of the SVG represented by this object.

The size of the painted area will be the size of this Svg object ([size](ksvg-svg.md#size)()) if [containsMultipleImages](ksvg-svg.md#containsMultipleImages) is `true`; otherwise, it will be the size of the requested element after the whole SVG has been scaled to [size](ksvg-svg.md#size)().

`painter` the [QPainter](https://doc.qt.io/qt-6/qpainter.html) to use

`point` the position to start drawing; the entire svg will be drawn starting at this point.

`elementID` the ID string of the element to render, or an empty string for the whole SVG (the default)

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void Svg::paint(QPainter \**painter*, const QRectF &*rect*, const QString &*elementID* = QString()) {#paint-1}

This method paints all or part of the SVG represented by this object.

`painter` the [QPainter](https://doc.qt.io/qt-6/qpainter.html) to use

`rect` the rect to draw into; if smaller than the current size the drawing is starting at this point.

`elementID` the ID string of the element to render, or an empty string for the whole SVG (the default)

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void Svg::paint(QPainter \**painter*, int *x*, int *y*, const QString &*elementID* = QString()) {#paint-2}

This method paints all or part of the SVG represented by this object.

The size of the painted area will be the size of this Svg object ([size](ksvg-svg.md#size)()) if [containsMultipleImages](ksvg-svg.md#containsMultipleImages) is `true`; otherwise, it will be the size of the requested element after the whole SVG has been scaled to [size](ksvg-svg.md#size)().

`painter` the [QPainter](https://doc.qt.io/qt-6/qpainter.html) to use

`x` the horizontal coordinate to start painting from

`y` the vertical coordinate to start painting from

`elementID` the ID string of the element to render, or an empty string for the whole SVG (the default)

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void Svg::paint(QPainter \**painter*, int *x*, int *y*, int *width*, int *height*, const QString &*elementID* = QString()) {#paint-3}

This method paints all or part of the SVG represented by this object.

`painter` the [QPainter](https://doc.qt.io/qt-6/qpainter.html) to use

`x` the horizontal coordinate to start painting from

`y` the vertical coordinate to start painting from

`width` the width of the element to draw

`height` the height of the element do draw

`elementID` the ID string of the element to render, or an empty string for the whole SVG (the default)

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] QPixmap Svg::pixmap(const QString &*elementID* = QString()) {#pixmap}

This method returns a pixmap of the SVG represented by this object.

The size of the pixmap will be the size of this Svg object ([size](ksvg-svg.md#size)()) if [containsMultipleImages](ksvg-svg.md#containsMultipleImages) is `true`; otherwise, it will be the size of the requested element after the whole SVG has been scaled to [size](ksvg-svg.md#size)().

`elementID` the ID string of the element to render, or an empty string for the whole SVG (the default)

Returns a [QPixmap](https://doc.qt.io/qt-6/qpixmap.html) of the rendered SVG

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[signal\] void Svg::repaintNeeded() {#repaintNeeded}

This signal is emitted whenever the SVG data has changed in such a way that a repaint is required.

Any usage of an SVG object that does the painting itself must connect to this signal and respond by updating the painting. Note that connecting to [ImageSet::imageSetChanged](ksvg-imageset.md#imageSetChanged) is incorrect in such a use case as the SVG itself may not be updated yet nor may theme change be the only case when a repaint is needed. Also note that classes or QML code which take Svg objects as parameters for their own painting all respond to this signal so that in those cases manually responding to the signal is unnecessary; ONLY when direct, manual painting with an Svg object is done in application code is this signal used.

### \[invokable\] void Svg::resize() {#resize}

This method resizes the rendered image to the natural size of the SVG.

Rendering will actually take place on the next call to paint.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

> **Note:** Setter function for property [size](ksvg-svg.md#size-prop).

### \[invokable\] void Svg::resize(const QSizeF &*size*) {#resize-1}

This method resizes the rendered image.

Rendering will actually take place on the next call to paint.

If [containsMultipleImages](ksvg-svg.md#containsMultipleImages) is `true`, each element of the SVG will be rendered at this size by default; otherwise, the entire image will be scaled to this size and each element will be scaled appropriately.

`size` the new size of the image

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

> **Note:** Setter function for property [size](ksvg-svg.md#size-prop).

### \[invokable\] void Svg::resize(qreal *width*, qreal *height*) {#resize-2}

This method resizes the rendered image.

Rendering will actually take place on the next call to paint.

If [containsMultipleImages](ksvg-svg.md#containsMultipleImages) is `true`, each element of the SVG will be rendered at this size by default; otherwise, the entire image will be scaled to this size and each element will be scaled appropriately.

`width` the new width

`height` the new height

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

> **Note:** Setter function for property [size](ksvg-svg.md#size-prop).

### void Svg::setColor(KSvg::Svg::StyleSheetColor *colorName*, const QColor &*color*) {#setColor}

*See also* [color](ksvg-svg.md#color)()

### void Svg::setColorSet(KSvg::Svg::ColorSet *colorSet*) {#setColorSet}

This method sets a color set for the SVG. Set a color set for the Svg. if the Svg uses stylesheets and has elements that are either `TextColor` or `BackgroundColor` class, make them use `ButtonTextColor` / `ButtonBackgroundColor` or `ViewTextColor` / `ViewBackgroundColor`

> **Note:** Setter function for property [colorSet](ksvg-svg.md#colorSet-prop).

*See also* [colorSet](ksvg-svg.md#colorSet)()

### \[since 6.18\] void Svg::setColors(const QMap\<KSvg::Svg::StyleSheetColor, QColor\> &*colors*) {#setColors}

Sets the specified stylesheet `colors`.

This function was introduced in Qt 6.18.

*See also* [color](ksvg-svg.md#color)(), [colorOverrides](ksvg-svg.md#colorOverrides)(), [clearColorOverrides](ksvg-svg.md#clearColorOverrides)()

### void Svg::setContainsMultipleImages(bool *multiple*) {#setContainsMultipleImages}

This method sets whether the SVG contains a single image or multiple ones.

If this is set to `true`, the SVG will be treated as a collection of related images, rather than a consistent drawing.

In particular, when individual elements are rendered, this affects whether the elements are resized to [size](ksvg-svg.md#size)() by default. See [paint](ksvg-svg.md#paint)() and [pixmap](ksvg-svg.md#pixmap)().

`multiple` true if the svg contains multiple images

> **Note:** Setter function for property [multipleImages](ksvg-svg.md#multipleImages-prop).

*See also* [containsMultipleImages](ksvg-svg.md#containsMultipleImages)(), [paint](ksvg-svg.md#paint)(), [pixmap](ksvg-svg.md#pixmap)()

### void Svg::setDevicePixelRatio(qreal *factor*) {#setDevicePixelRatio}

This method sets the device pixel ratio for the Svg.

This is the ratio between image pixels and device-independent pixels. The SVG will produce pixmaps scaled by [devicePixelRatio](ksvg-svg.md#devicePixelRatio), but all the sizes and element rects will not be altered. The default value is 1.0 and the scale will be done rounded to the floor integer.

Setting it to something higher will make all the elements of this SVG appear bigger.

*See also* [devicePixelRatio](ksvg-svg.md#devicePixelRatio)()

### \[virtual\] void Svg::setImagePath(const QString &*svgFilePath*) {#setImagePath}

This method sets the SVG file to render.

Relative paths are looked for in the current Svg theme, and should not include the file extension (.svg and .svgz files will be searched for). include the file extension; files with the .svg and .svgz extensions will be found automatically.

If the parent object of this Svg is a KSvg::Applet, relative paths will be searched for in the applet's package first.

`svgFilePath` either an absolute path to an SVG file, or an image name.

> **Note:** Setter function for property [imagePath](ksvg-svg.md#imagePath-prop).

*See also* [ImageSet::imagePath](ksvg-imageset.md#imagePath)()

### void Svg::setImageSet(KSvg::ImageSet \**theme*) {#setImageSet}

This method sets the [KSvg::ImageSet](ksvg-imageset.md) to use with this Svg object.

By default, Svg objects use KSvg::ImageSet::default().

This determines how relative image paths are interpreted.

`theme` the theme object to use

*See also* [imageSet](ksvg-svg.md#imageSet)()

### void Svg::setStatus(KSvg::Svg::Status *status*) {#setStatus}

This method sets the image in a selected status.

SVGs can be colored with system color themes. If `status` is selected, `TextColor` will become `HighlightedText` color, and `BackgroundColor` will become `HighlightColor`. This can be used to make SVG-based graphics such as symbolic icons look correct together. Supported statuses are `Normal` and `Selected`.

> **Note:** Setter function for property [status](ksvg-svg.md#status-prop).

*See also* [status](ksvg-svg.md#status)()

### void Svg::setUsingRenderingCache(bool *useCache*) {#setUsingRenderingCache}

This method sets whether or not to cache the results of rendering to pixmaps.

If the SVG is resized and re-rendered often (and does not keep using the same small set of pixmap dimensions), then it may be less efficient to do disk caching. A good example might be a progress meter that uses an Svg object to paint itself: the meter will be changing often enough, with enough unpredictability and without re-use of the previous pixmaps to not get a gain from caching.

Most Svg objects should use the caching feature, however. Therefore, the default is to use the render cache.

`useCache` true to cache rendered pixmaps

> **Note:** Setter function for property [usingRenderingCache](ksvg-svg.md#usingRenderingCache-prop).

*See also* [isUsingRenderingCache](ksvg-svg.md#isUsingRenderingCache)()

### QSizeF Svg::size() const {#size}

This method returns the size of the SVG.

If the SVG has been resized with [resize](ksvg-svg.md#resize)(), that size will be returned; otherwise, the natural size of the SVG will be returned.

If [containsMultipleImages](ksvg-svg.md#containsMultipleImages) is `true`, each element of the SVG will be rendered at this size by default.

Returns the current size of the SVG

> **Note:** Getter function for property [size](ksvg-svg.md#size-prop).

### \[signal\] void Svg::sizeChanged() {#sizeChanged}

This signal is emitted whenever the size has changed.

> **Note:** Notifier signal for property [size](ksvg-svg.md#size-prop).

*See also* [resize](ksvg-svg.md#resize)()

### KSvg::Svg::Status Svg::status() const {#status}

This method returns the Svg object's status.

> **Note:** Getter function for property [status](ksvg-svg.md#status-prop).

*See also* [setStatus](ksvg-svg.md#setStatus)()

### \[signal\] void Svg::statusChanged(KSvg::Svg::Status *status*) {#statusChanged}

This signal is emitted when the status has changed.

> **Note:** Notifier signal for property [status](ksvg-svg.md#status-prop).
