---
title: "KPixmapRegionSelectorDialog Class"
description: "A dialog that uses a KPixmapRegionSelectorWidget to allow the user to select a region of an image."
---

# KPixmapRegionSelectorDialog Class

A dialog that uses a [KPixmapRegionSelectorWidget](kpixmapregionselectorwidget.md) to allow the user to select a region of an image. [More...](#details)

- **Header:** `#include <KPixmapRegionSelectorDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](kpixmapregionselectordialog-members.md)

## Public Functions

- [KPixmapRegionSelectorDialog(QWidget \*parent = nullptr)](#KPixmapRegionSelectorDialog)
- [void adjustRegionSelectorWidgetSizeToFitScreen()](#adjustRegionSelectorWidgetSizeToFitScreen)
- [KPixmapRegionSelectorWidget \*pixmapRegionSelectorWidget() const](#pixmapRegionSelectorWidget)

## Static Public Members

- [QImage getSelectedImage(const QPixmap &pixmap, QWidget \*parent = nullptr)](#getSelectedImage)
- [QImage getSelectedImage(const QPixmap &pixmap, int aspectRatioWidth, int aspectRatioHeight, QWidget \*parent = nullptr)](#getSelectedImage-1)
- [QRect getSelectedRegion(const QPixmap &pixmap, QWidget \*parent = nullptr)](#getSelectedRegion)
- [QRect getSelectedRegion(const QPixmap &pixmap, int aspectRatioWidth, int aspectRatioHeight, QWidget \*parent = nullptr)](#getSelectedRegion-1)

## Detailed Description {#details}

If you want to use special features like forcing the selected area to have a fixed aspect ratio, you can use [pixmapRegionSelectorWidget](kpixmapregionselectordialog.md#pixmapRegionSelectorWidget)() to get the pointer to the [KPixmapRegionSelectorWidget](kpixmapregionselectorwidget.md) object and set the desired options there.

There are some convenience methods that allow to easily show a dialog for the user to select a region of an image, and just care about the selected image.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KPixmapRegionSelectorDialog::KPixmapRegionSelectorDialog(QWidget \**parent* = nullptr) {#KPixmapRegionSelectorDialog}

The constructor of an empty [KPixmapRegionSelectorDialog](kpixmapregionselectordialog.md), you have to call later the setPixmap method of the [KPixmapRegionSelectorWidget](kpixmapregionselectorwidget.md) widget of the new object.

### void KPixmapRegionSelectorDialog::adjustRegionSelectorWidgetSizeToFitScreen() {#adjustRegionSelectorWidgetSizeToFitScreen}

Adjusts the size of the [KPixmapRegionSelectorWidget](kpixmapregionselectorwidget.md) to not overflow the screen size

### \[static\] QImage KPixmapRegionSelectorDialog::getSelectedImage(const QPixmap &*pixmap*, QWidget \**parent* = nullptr) {#getSelectedImage}

Creates a modal dialog, lets the user to select a region of the `pixmap` and returns when the dialog is closed.

Returns the selected image, or an invalid image if the user pressed the Cancel button.

### \[static\] QImage KPixmapRegionSelectorDialog::getSelectedImage(const QPixmap &*pixmap*, int *aspectRatioWidth*, int *aspectRatioHeight*, QWidget \**parent* = nullptr) {#getSelectedImage-1}

Creates a modal dialog, lets the user to select a region of the `pixmap` with the same aspect ratio than `aspectRatioWidth` x `aspectRatioHeight` and returns when the dialog is closed.

Returns the selected image, or an invalid image if the user pressed the Cancel button.

### \[static\] QRect KPixmapRegionSelectorDialog::getSelectedRegion(const QPixmap &*pixmap*, QWidget \**parent* = nullptr) {#getSelectedRegion}

Creates a modal dialog, lets the user to select a region of the `pixmap` and returns when the dialog is closed.

Returns the selected rectangle, or an invalid rectangle if the user pressed the Cancel button.

### \[static\] QRect KPixmapRegionSelectorDialog::getSelectedRegion(const QPixmap &*pixmap*, int *aspectRatioWidth*, int *aspectRatioHeight*, QWidget \**parent* = nullptr) {#getSelectedRegion-1}

Creates a modal dialog, lets the user to select a region of the `pixmap` with the same aspect ratio than `aspectRatioWidth` x `aspectRatioHeight` and returns when the dialog is closed.

Returns the selected rectangle, or an invalid rectangle if the user pressed the Cancel button.

### KPixmapRegionSelectorWidget \*KPixmapRegionSelectorDialog::pixmapRegionSelectorWidget() const {#pixmapRegionSelectorWidget}

Returns the [KPixmapRegionSelectorWidget](kpixmapregionselectorwidget.md) widget so that additional parameters can be set by using it.
