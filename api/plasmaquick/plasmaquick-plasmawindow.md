---
title: "PlasmaQuick::PlasmaWindow Class"
description: "Creates a QQuickWindow themed in a Plasma style with background."
---

# PlasmaQuick::PlasmaWindow Class

Creates a [QQuickWindow](https://doc.qt.io/qt-6/qquickwindow.html) themed in a Plasma style with background. [More...](#details)

- **Header:** `#include <PlasmaQuick/PlasmaWindow>`
- **CMake:** `find_package(PlasmaQuick REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Plasma::PlasmaQuick)`
- **Inherits:** [QQuickWindow](https://doc.qt.io/qt-6/qquickwindow.html)
- **Inherited By:** [PlasmaQuick::PopupPlasmaWindow](plasmaquick-popupplasmawindow.md)

[List of all members, including inherited members](plasmaquick-plasmawindow-members.md)

## Public Types

- [enum PlasmaWindow::BackgroundHints](#BackgroundHints-enum)

## Properties

- [backgroundCutout : QRect](#backgroundCutout-prop)
- [backgroundCutoutBlur : bool](#backgroundCutoutBlur-prop)
- [backgroundHints : BackgroundHints](#backgroundHints-prop)
- [borders : Qt::Edges](#borders-prop)
- [\[read-only\] bottomPadding : qreal](#bottomPadding-prop)
- [\[read-only\] leftPadding : qreal](#leftPadding-prop)
- [mainItem : QQuickItem\*](#mainItem-prop)
- [\[read-only\] rightPadding : qreal](#rightPadding-prop)
- [\[read-only\] topPadding : qreal](#topPadding-prop)

## Public Functions

- [QMargins padding() const](#padding)
- [void setBorders(Qt::Edges bordersToShow)](#setBorders)
- [void setMainItem(QQuickItem \*mainItem)](#setMainItem)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum PlasmaWindow::BackgroundHints {#BackgroundHints-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `PlasmaQuick::PlasmaWindow::StandardBackground` | `0` | The standard background from the theme is drawn |
| `PlasmaQuick::PlasmaWindow::SolidBackground` | `1` | The solid version of the background is preferred |

## Property Documentation {#property-documentation}

### backgroundCutout : QRect {#backgroundCutout-prop}

Part of the window, for an item that draws its own background there: the window draws no background, blur or contrast in it. Empty for none.

**Access functions:**

- `QRect` **backgroundCutout**() const
- `void` **setBackgroundCutout**(const `QRect` &*cutout*)

**Notifier signal:**

- `void` **backgroundCutoutChanged**()

### backgroundCutoutBlur : bool {#backgroundCutoutBlur-prop}

Whether what is behind the cutout gets blurred.

**Access functions:**

- `bool` **backgroundCutoutBlur**() const
- `void` **setBackgroundCutoutBlur**(`bool` *blur*)

**Notifier signal:**

- `void` **[backgroundCutoutChanged](plasmaquick-plasmawindow.md#backgroundCutout-prop)**()

### backgroundHints : BackgroundHints {#backgroundHints-prop}

Defines the background used for the window

**Access functions:**

- `PlasmaQuick::PlasmaWindow::BackgroundHints` **backgroundHints**() const
- `void` **setBackgroundHints**(`PlasmaQuick::PlasmaWindow::BackgroundHints` *hints*)

**Notifier signal:**

- `void` **backgroundHintsChanged**()

### borders : Qt::Edges {#borders-prop}

Tells what borders are enabled of its background

**Access functions:**

- `Qt::Edges` **borders**()
- `void` **[setBorders](plasmaquick-plasmawindow.md#setBorders)**(`Qt::Edges` *bordersToShow*)

**Notifier signal:**

- `void` **bordersChanged**()

### \[read-only\] bottomPadding : qreal {#bottomPadding-prop}

**Access functions:**

- `qreal` **bottomPadding**() const

**Notifier signal:**

- `void` **paddingChanged**()

### \[read-only\] leftPadding : qreal {#leftPadding-prop}

**Access functions:**

- `qreal` **leftPadding**() const

**Notifier signal:**

- `void` **[paddingChanged](plasmaquick-plasmawindow.md#bottomPadding-prop)**()

### mainItem : QQuickItem\* {#mainItem-prop}

The main QML item that will be displayed in the Dialog

**Access functions:**

- `QQuickItem` \***mainItem**() const
- `void` **[setMainItem](plasmaquick-plasmawindow.md#setMainItem)**(`QQuickItem` \**mainItem*)

**Notifier signal:**

- `void` **mainItemChanged**()

### \[read-only\] rightPadding : qreal {#rightPadding-prop}

**Access functions:**

- `qreal` **rightPadding**() const

**Notifier signal:**

- `void` **[paddingChanged](plasmaquick-plasmawindow.md#bottomPadding-prop)**()

### \[read-only\] topPadding : qreal {#topPadding-prop}

**Access functions:**

- `qreal` **topPadding**() const

**Notifier signal:**

- `void` **[paddingChanged](plasmaquick-plasmawindow.md#bottomPadding-prop)**()

## Member Function Documentation {#member-function-documentation}

### QMargins PlasmaWindow::padding() const {#padding}

Returns the padding that are placed around the [mainItem](plasmaquick-plasmawindow.md#mainItem-prop) When setting size hints on the window this should be factored in.

### void PlasmaWindow::setBorders(Qt::Edges *bordersToShow*) {#setBorders}

Changes which rounded corners are shown on the window. Margins remain the same The default is all borders

> **Note:** Setter function for property [borders](plasmaquick-plasmawindow.md#borders-prop).

*See also* [borders](plasmaquick-plasmawindow.md#borders-prop)()

### void PlasmaWindow::setMainItem(QQuickItem \**mainItem*) {#setMainItem}

The main QML item that will be displayed in the Dialog

> **Note:** Setter function for property [mainItem](plasmaquick-plasmawindow.md#mainItem-prop).

*See also* [mainItem](plasmaquick-plasmawindow.md#mainItem-prop)()
