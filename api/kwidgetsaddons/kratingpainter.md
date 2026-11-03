---
title: "KRatingPainter Class"
description: "Utility class that draws a row of stars for a rating value."
---

# KRatingPainter Class

Utility class that draws a row of stars for a rating value. [More...](#details)

- **Header:** `#include <KRatingPainter>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`

[List of all members, including inherited members](kratingpainter-members.md)

## Public Functions

- [KRatingPainter()](#KRatingPainter)
- [Qt::Alignment alignment() const](#alignment)
- [QPixmap customPixmap() const](#customPixmap)
- [bool halfStepsEnabled() const](#halfStepsEnabled)
- [QIcon icon() const](#icon)
- [bool isEnabled() const](#isEnabled)
- [Qt::LayoutDirection layoutDirection() const](#layoutDirection)
- [int maxRating() const](#maxRating)
- [void paint(QPainter \*painter, const QRect &rect, int rating, int hoverRating = -1) const](#paint)
- [int ratingFromPosition(const QRect &rect, const QPoint &pos) const](#ratingFromPosition)
- [void setAlignment(Qt::Alignment align)](#setAlignment)
- [void setCustomPixmap(const QPixmap &pixmap)](#setCustomPixmap)
- [void setEnabled(bool enabled)](#setEnabled)
- [void setHalfStepsEnabled(bool enabled)](#setHalfStepsEnabled)
- [void setIcon(const QIcon &icon)](#setIcon)
- [void setLayoutDirection(Qt::LayoutDirection direction)](#setLayoutDirection)
- [void setMaxRating(int max)](#setMaxRating)
- [void setSpacing(int spacing)](#setSpacing)
- [int spacing() const](#spacing)

## Static Public Members

- [int getRatingFromPosition(const QRect &rect, Qt::Alignment align, Qt::LayoutDirection direction, const QPoint &pos)](#getRatingFromPosition)
- [void paintRating(QPainter \*p, const QRect &rect, Qt::Alignment align, int rating, int hoverRating = -1)](#paintRating)

## Detailed Description {#details}

The [KRatingPainter](kratingpainter.md) also allows to determine a rating value from a position in the draw area. it supports all different alignments and custom icons.

For showing a rating in a widget see [KRatingWidget](kratingwidget.md).

## Member Function Documentation {#member-function-documentation}

### KRatingPainter::KRatingPainter() {#KRatingPainter}

Create a new [KRatingPainter](kratingpainter.md). For most cases the static methods [paintRating](kratingpainter.md#paintRating) and [getRatingFromPosition](kratingpainter.md#getRatingFromPosition) should be sufficient.

### Qt::Alignment KRatingPainter::alignment() const {#alignment}

The alignment of the stars.

*See also* [setAlignment](kratingpainter.md#setAlignment)

### QPixmap KRatingPainter::customPixmap() const {#customPixmap}

The custom pixmap set to draw a star. If no custom pixmap has been set, an invalid pixmap is returned.

*See also* [setCustomPixmap](kratingpainter.md#setCustomPixmap)

### \[static\] int KRatingPainter::getRatingFromPosition(const QRect &*rect*, Qt::Alignment *align*, Qt::LayoutDirection *direction*, const QPoint &*pos*) {#getRatingFromPosition}

Get the rating that would be selected if the user clicked position pos within rect if the rating has been drawn with [paintRating](kratingpainter.md#paintRating)() using the same rect and align values.

Returns The new rating or -1 if pos is outside of the rating area.

### bool KRatingPainter::halfStepsEnabled() const {#halfStepsEnabled}

If half steps are enabled one star equals to 2 rating points and uneven rating values result in half-stars being drawn.

*See also* [setHalfStepsEnabled](kratingpainter.md#setHalfStepsEnabled)

### QIcon KRatingPainter::icon() const {#icon}

The icon used to draw a star. In case a custom pixmap has been set this value is ignored.

*See also* [setIcon](kratingpainter.md#setIcon), [setCustomPixmap](kratingpainter.md#setCustomPixmap)

### bool KRatingPainter::isEnabled() const {#isEnabled}

The rating can be painted in a disabled state where no color is used and hover ratings are ignored.

*See also* [setEnabled](kratingpainter.md#setEnabled)

### Qt::LayoutDirection KRatingPainter::layoutDirection() const {#layoutDirection}

The layout direction. If RTL the stars representing the rating value will be drawn from the right.

*See also* [setLayoutDirection](kratingpainter.md#setLayoutDirection)

### int KRatingPainter::maxRating() const {#maxRating}

The maximum rating, i.e. how many stars are drawn in total.

*See also* [setMaxRating](kratingpainter.md#setMaxRating)

### void KRatingPainter::paint(QPainter \**painter*, const QRect &*rect*, int *rating*, int *hoverRating* = -1) const {#paint}

Draw the rating.

`painter` The painter to draw the rating to.

`rect` The geometry of the rating. The alignment of the rating is used relative to this value.

`rating` The actual rating value to draw.

`hoverRating` The hover rating indicates the position the user hovers the mouse pointer at. This will provide visual feedback about the new rating if the user would actually click as well as the difference to the current rating.

### \[static\] void KRatingPainter::paintRating(QPainter \**p*, const QRect &*rect*, Qt::Alignment *align*, int *rating*, int *hoverRating* = -1) {#paintRating}

Convenience method that paints a rating into the given rect.

LayoutDirection is read from [QPainter](https://doc.qt.io/qt-6/qpainter.html).

`align` can be aligned vertically and horizontally. Using [Qt::AlignJustify](https://doc.qt.io/qt-6/qt.html#AlignmentFlag-enum) will insert spacing between the stars.

### int KRatingPainter::ratingFromPosition(const QRect &*rect*, const QPoint &*pos*) const {#ratingFromPosition}

Calculate the rating value from mouse position pos.

Returns the rating corresponding to pos or -1 if pos is outside of the configured rect.

### void KRatingPainter::setAlignment(Qt::Alignment *align*) {#setAlignment}

The alignment of the stars in the drawing rect. All alignment flags are supported.

*See also* [alignment](kratingpainter.md#alignment)()

### void KRatingPainter::setCustomPixmap(const QPixmap &*pixmap*) {#setCustomPixmap}

Set a custom pixmap.

*See also* [customPixmap](kratingpainter.md#customPixmap)()

### void KRatingPainter::setEnabled(bool *enabled*) {#setEnabled}

Enable or disable the rating. Default is enabled.

*See also* [isEnabled](kratingpainter.md#isEnabled)()

### void KRatingPainter::setHalfStepsEnabled(bool *enabled*) {#setHalfStepsEnabled}

If half steps are enabled (the default) then one rating step corresponds to half a star.

*See also* [halfStepsEnabled](kratingpainter.md#halfStepsEnabled)()

### void KRatingPainter::setIcon(const QIcon &*icon*) {#setIcon}

Set a custom icon. Defaults to "rating".

*See also* [icon](kratingpainter.md#icon)()

### void KRatingPainter::setLayoutDirection(Qt::LayoutDirection *direction*) {#setLayoutDirection}

LTR or RTL

*See also* [layoutDirection](kratingpainter.md#layoutDirection)()

### void KRatingPainter::setMaxRating(int *max*) {#setMaxRating}

The maximum rating. Defaults to 10.

*See also* [maxRating](kratingpainter.md#maxRating)()

### void KRatingPainter::setSpacing(int *spacing*) {#setSpacing}

Set the spacing between rating pixmaps. Be aware that for justified horizontal alignment this values may be ignored.

*See also* [spacing](kratingpainter.md#spacing)()

### int KRatingPainter::spacing() const {#spacing}

The spacing between rating pixmaps.

*See also* [setSpacing](kratingpainter.md#setSpacing)
