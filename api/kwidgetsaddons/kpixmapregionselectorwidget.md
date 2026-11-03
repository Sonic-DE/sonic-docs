---
title: "KPixmapRegionSelectorWidget Class"
description: "KPixmapRegionSelectorWidget is a widget that shows a picture and provides the user with a friendly way to select a rectangular subregion of the pixmap."
---

# KPixmapRegionSelectorWidget Class

[KPixmapRegionSelectorWidget](kpixmapregionselectorwidget.md) is a widget that shows a picture and provides the user with a friendly way to select a rectangular subregion of the pixmap. [More...](#details)

- **Header:** `#include <KPixmapRegionSelectorWidget>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kpixmapregionselectorwidget-members.md)

## Public Types

- [enum KPixmapRegionSelectorWidget::RotateDirection](#RotateDirection-enum)

## Properties

- [pixmap : QPixmap](#pixmap-prop)

## Public Functions

- [KPixmapRegionSelectorWidget(QWidget \*parent = nullptr)](#KPixmapRegionSelectorWidget)
- [QPixmap pixmap() const](#pixmap)
- [void resetSelection()](#resetSelection)
- [void rotate(KPixmapRegionSelectorWidget::RotateDirection direction)](#rotate)
- [QImage selectedImage() const](#selectedImage)
- [QRect selectedRegion() const](#selectedRegion)
- [void setFreeSelectionAspectRatio()](#setFreeSelectionAspectRatio)
- [void setMaximumWidgetSize(int width, int height)](#setMaximumWidgetSize)
- [void setPixmap(const QPixmap &pixmap)](#setPixmap)
- [void setSelectedRegion(const QRect &rect)](#setSelectedRegion)
- [void setSelectionAspectRatio(int width, int height)](#setSelectionAspectRatio)
- [QRect unzoomedSelectedRegion() const](#unzoomedSelectedRegion)

## Public Slots

- [void rotateClockwise()](#rotateClockwise)
- [void rotateCounterclockwise()](#rotateCounterclockwise)

## Signals

- [void pixmapRotated()](#pixmapRotated)

## Protected Functions

- [QMenu \*createPopupMenu()](#createPopupMenu)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum KPixmapRegionSelectorWidget::RotateDirection {#RotateDirection-enum}

This enum provides a rotation direction.

| Constant | Value | Description |
| --- | --- | --- |
| `KPixmapRegionSelectorWidget::Rotate90` | `0` | Rotate 90 degrees to the right. |
| `KPixmapRegionSelectorWidget::Rotate180` | `1` | Rotate 180 degrees. |
| `KPixmapRegionSelectorWidget::Rotate270` | `2` | Rotate 90 degrees to the left. |

*See also* [KPixmapRegionSelectorWidget::rotate](kpixmapregionselectorwidget.md#rotate)()

## Property Documentation {#property-documentation}

### pixmap : QPixmap {#pixmap-prop}

**Access functions:**

- `QPixmap` **[pixmap](kpixmapregionselectorwidget.md#pixmap)**() const
- `void` **[setPixmap](kpixmapregionselectorwidget.md#setPixmap)**(const `QPixmap` &*pixmap*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KPixmapRegionSelectorWidget::KPixmapRegionSelectorWidget(QWidget \**parent* = nullptr) {#KPixmapRegionSelectorWidget}

Constructor for a [KPixmapRegionSelectorWidget](kpixmapregionselectorwidget.md).

### \[virtual protected\] QMenu \*KPixmapRegionSelectorWidget::createPopupMenu() {#createPopupMenu}

Creates a [QMenu](https://doc.qt.io/qt-6/qmenu.html) with the menu that appears when clicking with the right button on the label

### QPixmap KPixmapRegionSelectorWidget::pixmap() const {#pixmap}

Returns the original whole pixmap that we're using in this widget as the pixmap the user is selecting a region from.

> **Note:** Getter function for property [pixmap](kpixmapregionselectorwidget.md#pixmap-prop).

*See also* [setPixmap](kpixmapregionselectorwidget.md#setPixmap)()

### \[signal\] void KPixmapRegionSelectorWidget::pixmapRotated() {#pixmapRotated}

### void KPixmapRegionSelectorWidget::resetSelection() {#resetSelection}

Resets the selection to use the whole image

### void KPixmapRegionSelectorWidget::rotate(KPixmapRegionSelectorWidget::RotateDirection *direction*) {#rotate}

Rotates the image as specified by the `direction` parameter, also tries to rotate the selected region so that it doesn't change, as long as the forced aspect ratio setting is respected, in other case, the selected region is reset.

### \[slot\] void KPixmapRegionSelectorWidget::rotateClockwise() {#rotateClockwise}

Rotates the current image 90º clockwise

### \[slot\] void KPixmapRegionSelectorWidget::rotateCounterclockwise() {#rotateCounterclockwise}

Rotates the current image 90º counterclockwise

### QImage KPixmapRegionSelectorWidget::selectedImage() const {#selectedImage}

Returns a [QImage](https://doc.qt.io/qt-6/qimage.html) object with just the region the user selected from the image

### QRect KPixmapRegionSelectorWidget::selectedRegion() const {#selectedRegion}

Returns the selected region ( in zoomed pixmap coordinates )

*See also* [setSelectedRegion](kpixmapregionselectorwidget.md#setSelectedRegion)()

### void KPixmapRegionSelectorWidget::setFreeSelectionAspectRatio() {#setFreeSelectionAspectRatio}

Allows the user to do a selection which has any aspect ratio. This is the default.

*See also* [setSelectionAspectRatio](kpixmapregionselectorwidget.md#setSelectionAspectRatio)()

### void KPixmapRegionSelectorWidget::setMaximumWidgetSize(int *width*, int *height*) {#setMaximumWidgetSize}

Sets the maximum size for the widget. If the image is larger than this (either horizontally or vertically), it's scaled to adjust to the maximum size (preserving the aspect ratio)

### void KPixmapRegionSelectorWidget::setPixmap(const QPixmap &*pixmap*) {#setPixmap}

Sets the pixmap which will be shown for the user to select a region from.

`pixmap` The pixmap. Must be non-null.

> **Note:** Setter function for property [pixmap](kpixmapregionselectorwidget.md#pixmap-prop).

*See also* [pixmap](kpixmapregionselectorwidget.md#pixmap)()

### void KPixmapRegionSelectorWidget::setSelectedRegion(const QRect &*rect*) {#setSelectedRegion}

Sets the selected region to be `rect` (in zoomed pixmap coordinates)

*See also* [selectedRegion](kpixmapregionselectorwidget.md#selectedRegion)()

### void KPixmapRegionSelectorWidget::setSelectionAspectRatio(int *width*, int *height*) {#setSelectionAspectRatio}

Sets the aspect ration that the selected subimage should have. The way to select it, is specifying an example valid `width` and `height`.

*See also* [setFreeSelectionAspectRatio](kpixmapregionselectorwidget.md#setFreeSelectionAspectRatio)()

### QRect KPixmapRegionSelectorWidget::unzoomedSelectedRegion() const {#unzoomedSelectedRegion}

Returns the selected region ( in unzoomed, original pixmap coordinates )
