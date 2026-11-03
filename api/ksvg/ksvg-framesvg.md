---
title: "KSvg::FrameSvg Class"
description: "Provides an SVG with borders."
---

# KSvg::FrameSvg Class

Provides an SVG with borders. [More...](#details)

- **Header:** `#include <KSvg/FrameSvg>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Svg)`  
  `target_link_libraries(mytarget PRIVATE KF6::Svg)`
- **Inherits:** [KSvg::Svg](ksvg-svg.md)

[List of all members, including inherited members](ksvg-framesvg-members.md)

## Public Types

- [enum FrameSvg::EnabledBorder](#EnabledBorder-enum)
- [enum FrameSvg::LocationPrefix](#LocationPrefix-enum)
- [enum FrameSvg::MarginEdge](#MarginEdge-enum)

## Properties

- [enabledBorders : EnabledBorders](#enabledBorders-prop)

## Public Functions

- [FrameSvg(QObject \*parent = nullptr)](#FrameSvg)
- [QString actualPrefix() const](#actualPrefix)
- [QPixmap alphaMask() const](#alphaMask)
- [bool cacheAllRenderedFrames() const](#cacheAllRenderedFrames)
- [void clearCache()](#clearCache)
- [QRectF contentsRect() const](#contentsRect)
- [KSvg::FrameSvg::EnabledBorders enabledBorders() const](#enabledBorders)
- [qreal fixedMarginSize(const KSvg::FrameSvg::MarginEdge edge) const](#fixedMarginSize)
- [QMarginsF fixedMargins() const](#fixedMargins) (since 6.21)
- [QPixmap framePixmap()](#framePixmap)
- [QSizeF frameSize() const](#frameSize)
- [void getFixedMargins(qreal &left, qreal &top, qreal &right, qreal &bottom) const](#getFixedMargins)
- [void getInset(qreal &left, qreal &top, qreal &right, qreal &bottom) const](#getInset)
- [void getMargins(qreal &left, qreal &top, qreal &right, qreal &bottom) const](#getMargins)
- [bool hasElementPrefix(KSvg::FrameSvg::LocationPrefix location) const](#hasElementPrefix)
- [bool hasElementPrefix(const QString &prefix) const](#hasElementPrefix-1)
- [qreal insetSize(const KSvg::FrameSvg::MarginEdge edge) const](#insetSize)
- [QMarginsF insets() const](#insets) (since 6.21)
- [bool isRepaintBlocked() const](#isRepaintBlocked)
- [qreal marginSize(const KSvg::FrameSvg::MarginEdge edge) const](#marginSize)
- [QMarginsF margins() const](#margins) (since 6.21)
- [QRegion mask() const](#mask)
- [int minimumDrawingHeight()](#minimumDrawingHeight)
- [int minimumDrawingWidth()](#minimumDrawingWidth)
- [void paintFrame(QPainter \*painter, const QPointF &pos = QPointF(0, 0))](#paintFrame)
- [void paintFrame(QPainter \*painter, const QRectF &target, const QRectF &source = QRectF())](#paintFrame-1)
- [QString prefix()](#prefix)
- [void resizeFrame(const QSizeF &size)](#resizeFrame)
- [void setCacheAllRenderedFrames(bool cache)](#setCacheAllRenderedFrames)
- [void setElementPrefix(KSvg::FrameSvg::LocationPrefix location)](#setElementPrefix)
- [void setElementPrefix(const QString &prefix)](#setElementPrefix-1)
- [void setEnabledBorders(const KSvg::FrameSvg::EnabledBorders borders)](#setEnabledBorders)
- [void setImagePath(const QString &path)](#setImagePath)
- [void setRepaintBlocked(bool blocked)](#setRepaintBlocked)

## Detailed Description {#details}

When using SVG images for a background of an object that may change its aspect ratio, such as a dialog, simply scaling a single image may not be enough.

[FrameSvg](ksvg-framesvg.md) allows SVGs to provide several elements for borders as well as a central element, each of which are scaled individually. These elements should be named:

- `center` - the central element, which will be scaled in both directions
- `top` - the top border; the height is fixed, but it will be scaled horizontally to the same width as `center`
- `bottom` - the bottom border; scaled in the same way as `top`
- `left` - the left border; the width is fixed, but it will be scaled vertically to the same height as `center`
- `right` - the right border; scaled in the same way as `left`
- `topleft` - fixed size; must be the same height as `top` and the same width as `left`
- `bottomleft`, `topright`, `bottomright` - similar to `topleft`

`center` must exist, but all the others are optional. `topleft` and `topright` will be ignored if `top` does not exist, and similarly for `bottomleft` and `bottomright`.

*See also* [KSvg::Svg](ksvg-index.md)

## Member Type Documentation {#member-type-documentation}

### enum FrameSvg::EnabledBorder {#EnabledBorder-enum}

**flags FrameSvg::EnabledBorders**

This flag enum specifies which borders should be drawn.

| Constant |   |
| --- | --- |
| `KSvg::FrameSvg::NoBorder` | `0` |
| `KSvg::FrameSvg::TopBorder` | `1` |
| `KSvg::FrameSvg::BottomBorder` | `2` |
| `KSvg::FrameSvg::LeftBorder` | `4` |
| `KSvg::FrameSvg::RightBorder` | `8` |
| `KSvg::FrameSvg::AllBorders` | `TopBorder | BottomBorder | LeftBorder | RightBorder` |

The `EnabledBorders` type is a typedef for `QFlags<EnabledBorder>. `It stores an OR combination of `EnabledBorder` values.

### enum FrameSvg::LocationPrefix {#LocationPrefix-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KSvg::FrameSvg::Floating` | `0` | Free floating. |
| `KSvg::FrameSvg::TopEdge` | `1` | Along the top of the screen. |
| `KSvg::FrameSvg::BottomEdge` | `2` | Along the bottom of the screen. |
| `KSvg::FrameSvg::LeftEdge` | `3` | Along the left side of the screen. |
| `KSvg::FrameSvg::RightEdge` | `4` | Along the right side of the screen. |

### enum FrameSvg::MarginEdge {#MarginEdge-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KSvg::FrameSvg::TopMargin` | `0` | The top margin. |
| `KSvg::FrameSvg::BottomMargin` | `1` | The bottom margin. |
| `KSvg::FrameSvg::LeftMargin` | `2` | The left margin. |
| `KSvg::FrameSvg::RightMargin` | `3` | The right margin. |

## Property Documentation {#property-documentation}

### enabledBorders : EnabledBorders {#enabledBorders-prop}

**Access functions:**

- `KSvg::FrameSvg::EnabledBorders` **[enabledBorders](ksvg-framesvg.md#enabledBorders)**() const
- `void` **[setEnabledBorders](ksvg-framesvg.md#setEnabledBorders)**(const `KSvg::FrameSvg::EnabledBorders` *borders*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] FrameSvg::FrameSvg(QObject \**parent* = nullptr) {#FrameSvg}

Constructs a new [FrameSvg](ksvg-framesvg.md) that paints the proper named subelements as borders. It may also be used as a regular [KSvg::Svg](ksvg-svg.md) object for direct access to elements in the Svg.

`parent` options [QObject](https://doc.qt.io/qt-6/qobject.html) to parent this to

*See also* [KSvg::Theme](ksvg-index.md)

### QString FrameSvg::actualPrefix() const {#actualPrefix}

This method returns the prefix that is actually being used (including a '-' at the end if not empty).

*See also* [prefix](ksvg-framesvg.md#prefix)()

### QPixmap FrameSvg::alphaMask() const {#alphaMask}

This method returns a pixmap whose alpha channel is the opacity of the frame. It may be the frame itself or a special frame with the "mask-" prefix.

### \[invokable\] bool FrameSvg::cacheAllRenderedFrames() const {#cacheAllRenderedFrames}

This method returns whether all the different prefixes should be kept in a cache when rendered.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [setCacheAllRenderedFrames](ksvg-framesvg.md#setCacheAllRenderedFrames)()

### \[invokable\] void FrameSvg::clearCache() {#clearCache}

This method deletes the internal cache.

Calling this method frees memory. Use this if you want to switch the rendered element and you don't plan to switch back to the previous one for a long time.

This only works if setUsingRenderingCache(`true`) has been called.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [KSvg::Svg::setUsingRenderingCache()](ksvg-index.md)

### \[invokable\] QRectF FrameSvg::contentsRect() const {#contentsRect}

This method returns the rectangle of the center element, taking the margins into account.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### KSvg::FrameSvg::EnabledBorders FrameSvg::enabledBorders() const {#enabledBorders}

This is a convenience method to get the enabled borders. Returns what borders are painted

> **Note:** Getter function for property [enabledBorders](ksvg-framesvg.md#enabledBorders-prop).

*See also* [setEnabledBorders](ksvg-framesvg.md#setEnabledBorders)()

### \[invokable\] qreal FrameSvg::fixedMarginSize(const KSvg::FrameSvg::MarginEdge *edge*) const {#fixedMarginSize}

This method returns the margin size for the specified edge.

The margins specify the spacing between the contents and the SVG bounding rect.

Compared to [marginSize](ksvg-framesvg.md#marginSize)(), this does not depend on whether the border is enabled or not.

`edge` the margin edge we want, top, bottom, left or right Returns the margin size

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[since 6.21\] QMarginsF FrameSvg::fixedMargins() const {#fixedMargins}

Returns the margin extents. The margins specify the spacing between the contents and the SVG bounding rect. Compared to [margins](ksvg-framesvg.md#margins)(), this does not depend on whether a border is enabled or not.

This function was introduced in Qt 6.21.

### \[invokable\] QPixmap FrameSvg::framePixmap() {#framePixmap}

This method returns a pixmap of the SVG represented by this object.

Returns a [QPixmap](https://doc.qt.io/qt-6/qpixmap.html) of the rendered SVG

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] QSizeF FrameSvg::frameSize() const {#frameSize}

Returns the size of the frame

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void FrameSvg::getFixedMargins(qreal &*left*, qreal &*top*, qreal &*right*, qreal &*bottom*) const {#getFixedMargins}

This is a convenience method that extracts the size of the four margins and saves their size into the passed variables.

The margins specify the spacing between the contents and the SVG bounding rect.

Compared to [getMargins](ksvg-framesvg.md#getMargins)(), this doesn't depend on whether the borders are enabled or not.

`left` left margin size

`top` top margin size

`right` right margin size

`bottom` bottom margin size

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void FrameSvg::getInset(qreal &*left*, qreal &*top*, qreal &*right*, qreal &*bottom*) const {#getInset}

This is a convenience method that extracts the size of the four inset margins and saves their size into the passed variables.

The insets specify the spacing between the borders and the SVG bounding rect. For example, that space may include things such as drop shadows.

`left` left margin size

`top` top margin size

`right` right margin size

`bottom` bottom margin size

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void FrameSvg::getMargins(qreal &*left*, qreal &*top*, qreal &*right*, qreal &*bottom*) const {#getMargins}

This is a convenience method that extracts the size of the four margins and saves their size into the passed variables.

The margins specify the spacing between the contents and the SVG bounding rect.

If you don't care about the borders being on or off, use [getFixedMargins](ksvg-framesvg.md#getFixedMargins)() instead.

`left` left margin size

`top` top margin size

`right` right margin size

`bottom` bottom margin size

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] bool FrameSvg::hasElementPrefix(KSvg::FrameSvg::LocationPrefix *location*) const {#hasElementPrefix}

This is an overloaded method provided for convenience that is equivalent to hasElementPrefix("north"), hasElementPrefix("south") hasElementPrefix("west") and hasElementPrefix("east").

Returns true if the svg has the necessary elements with the given prefix to draw a frame.

`location` the given prefix we want to check if drawable

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] bool FrameSvg::hasElementPrefix(const QString &*prefix*) const {#hasElementPrefix-1}

This method returns whether the SVG has the necessary elements with the given prefix to draw a frame.

`prefix` the given prefix we want to check if drawable (can have trailing '-' since 5.59)

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] qreal FrameSvg::insetSize(const KSvg::FrameSvg::MarginEdge *edge*) const {#insetSize}

This method returns the insets margin size for the specified edge.

The insets specify the spacing between the borders and the SVG bounding rect. For example, that space may include things such as drop shadows.

`edge` the margin edge we want, top, bottom, left or right

Returns the margin size

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[since 6.21\] QMarginsF FrameSvg::insets() const {#insets}

Returns the inset extents. The insets specify the spacing between the borders and the SVG bounding rect. For example, that space may include things such as drop shadows.

This function was introduced in Qt 6.21.

### bool FrameSvg::isRepaintBlocked() const {#isRepaintBlocked}

This method returns whether we are in a transaction of many changes at once.

This is used to restrict rebuilding generated graphics for each change made.

### \[invokable\] qreal FrameSvg::marginSize(const KSvg::FrameSvg::MarginEdge *edge*) const {#marginSize}

This method returns the margin size for the given edge.

Note that `0` will be returned if the given margin is disabled.

The margins specify the spacing between the contents and the SVG bounding rect.

If you don't care about the border being on or off, use [fixedMarginSize](ksvg-framesvg.md#fixedMarginSize)() instead.

`edge` the margin edge we want, top, bottom, left or right

Returns the margin size

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[since 6.21\] QMarginsF FrameSvg::margins() const {#margins}

Returns the margin extents. The margins specify the spacing between the contents and the SVG bounding rect.

If you don't care about the borders being on or off, use [fixedMargins](ksvg-framesvg.md#fixedMargins)() instead.

This function was introduced in Qt 6.21.

### \[invokable\] QRegion FrameSvg::mask() const {#mask}

This method returns a mask that tightly contains the fully opaque areas of the SVG.

Returns a region of opaque areas

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] int FrameSvg::minimumDrawingHeight() {#minimumDrawingHeight}

This method returns the minimum height required to correctly draw this SVG.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] int FrameSvg::minimumDrawingWidth() {#minimumDrawingWidth}

This method returns the minimum width required to correctly draw this SVG.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void FrameSvg::paintFrame(QPainter \**painter*, const QPointF &*pos* = QPointF(0, 0)) {#paintFrame}

This method paints the loaded SVG with the elements that represents the border.

This is an overloaded member provided for convenience

`painter` the [QPainter](https://doc.qt.io/qt-6/qpainter.html) to use

`pos` where to paint the svg

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void FrameSvg::paintFrame(QPainter \**painter*, const QRectF &*target*, const QRectF &*source* = QRectF()) {#paintFrame-1}

This method paints the loaded SVG with the elements that represents the border.

`painter` the [QPainter](https://doc.qt.io/qt-6/qpainter.html) to use

`target` the target rectangle on the paint device

`source` the portion rectangle of the source image

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] QString FrameSvg::prefix() {#prefix}

This method returns the prefix for SVG elements of the [FrameSvg](ksvg-framesvg.md) (including a '-' at the end if not empty).

Returns the prefix

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [actualPrefix](ksvg-framesvg.md#actualPrefix)()

### \[invokable\] void FrameSvg::resizeFrame(const QSizeF &*size*) {#resizeFrame}

This method resizes the frame, maintaining the same border size.

`size` the new size of the frame

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void FrameSvg::setCacheAllRenderedFrames(bool *cache*) {#setCacheAllRenderedFrames}

This method sets whether saving all the rendered prefixes in a cache or not.

`cache` whether to use the cache.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [cacheAllRenderedFrames](ksvg-framesvg.md#cacheAllRenderedFrames)()

### \[invokable\] void FrameSvg::setElementPrefix(KSvg::FrameSvg::LocationPrefix *location*) {#setElementPrefix}

This method sets the prefix to 'north', 'south', 'west' and 'east' when the location is [TopEdge](ksvg-framesvg.md#LocationPrefix-enum), [BottomEdge](ksvg-framesvg.md#LocationPrefix-enum), [LeftEdge](ksvg-framesvg.md#LocationPrefix-enum) and [RightEdge](ksvg-framesvg.md#LocationPrefix-enum), respectively. Clears the prefix in other cases.

The prefix must exist in the SVG document, which means that this can only be called successfully after [setImagePath](ksvg-framesvg.md#setImagePath) is called.

`location` location in the UI this frame will be drawn

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [hasElementPrefix](ksvg-framesvg.md#hasElementPrefix)(), setElementPrefix

### \[invokable\] void FrameSvg::setElementPrefix(const QString &*prefix*) {#setElementPrefix-1}

This method sets the prefix for the SVG elements to be used for painting.

For example, if prefix is 'active', then instead of using the 'top' element of the SVG file to paint the top border, the 'active-top' element will be used. The same goes for other SVG elements.

If the elements with prefixes are not present, the default ones are used. (for the sake of speed, the test is present only for the 'center' element)

Setting the prefix manually resets the location to Floating.

The prefix must exist in the SVG document, which means that this can only be called successfully after [setImagePath](ksvg-framesvg.md#setImagePath) is called.

`prefix` prefix for the SVG elements that make up the frame

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### void FrameSvg::setEnabledBorders(const KSvg::FrameSvg::EnabledBorders *borders*) {#setEnabledBorders}

This method sets which borders should be painted.

`borders` the borders we want to paint

> **Note:** Setter function for property [enabledBorders](ksvg-framesvg.md#enabledBorders-prop).

*See also* [enabledBorders](ksvg-framesvg.md#enabledBorders)(), [EnabledBorder](ksvg-framesvg.md#EnabledBorder-enum)

### \[override virtual invokable\] void FrameSvg::setImagePath(const QString &*path*) {#setImagePath}

Reimplements: [Svg::setImagePath(const QString &svgFilePath)](ksvg-svg.md#setImagePath).

Loads a new Svg `imagePath` the new file

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### void FrameSvg::setRepaintBlocked(bool *blocked*) {#setRepaintBlocked}

This method sets whether we should block rebuilding generated graphics for each change made.

Setting this to `true` will block rebuilding the generated graphics for each change made and will do these changes in blocks instead.

How to use this method: When making several changes at once to the frame properties–such as prefix, enabled borders, and size–set this property to true to avoid regenerating the graphics for each change. Set it to false again after applying all required changes.

Note that any change will not be visible in the painted frame while this property is set to true.

*See also* [isRepaintBlocked](ksvg-framesvg.md#isRepaintBlocked)()
