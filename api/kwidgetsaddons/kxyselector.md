---
title: "KXYSelector Class"
description: "Base class for other widgets which provides the ability to choose from a two-dimensional range of values."
---

# KXYSelector Class

Base class for other widgets which provides the ability to choose from a two-dimensional range of values. [More...](#details)

- **Header:** `#include <KXYSelector>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kxyselector-members.md)

## Properties

- [xValue : int](#xValue-prop)
- [yValue : int](#yValue-prop)

## Public Functions

- [KXYSelector(QWidget \*parent = nullptr)](#KXYSelector)
- [QRect contentsRect() const](#contentsRect)
- [void setMarkerColor(const QColor &col)](#setMarkerColor)
- [void setRange(int minX, int minY, int maxX, int maxY)](#setRange)
- [void setValues(int xPos, int yPos)](#setValues)
- [void setXValue(int xPos)](#setXValue)
- [void setYValue(int yPos)](#setYValue)
- [int xValue() const](#xValue)
- [int yValue() const](#yValue)

## Signals

- [void valueChanged(int x, int y)](#valueChanged)

## Protected Functions

- [void drawContents(QPainter \*)](#drawContents)
- [void drawMarker(QPainter \*p, int xp, int yp)](#drawMarker)
- [void valuesFromPosition(int x, int y, int &xVal, int &yVal) const](#valuesFromPosition)

## Detailed Description {#details}

The currently chosen value is indicated by a cross. An example is the KHSSelector which allows to choose from a range of colors, and which is used in KColorDialog.

A custom drawing routine for the widget surface has to be provided by the subclass.

## Property Documentation {#property-documentation}

### xValue : int {#xValue-prop}

**Access functions:**

- `int` **[xValue](kxyselector.md#xValue)**() const
- `void` **[setXValue](kxyselector.md#setXValue)**(`int` *xPos*)

### yValue : int {#yValue-prop}

**Access functions:**

- `int` **[yValue](kxyselector.md#yValue)**() const
- `void` **[setYValue](kxyselector.md#setYValue)**(`int` *yPos*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KXYSelector::KXYSelector(QWidget \**parent* = nullptr) {#KXYSelector}

Constructs a two-dimensional selector widget which has a value range of \[0..100\] in both directions.

### QRect KXYSelector::contentsRect() const {#contentsRect}

Returns the rectangle on which subclasses should draw.

### \[virtual protected\] void KXYSelector::drawContents(*QPainter \**) {#drawContents}

Override this function to draw the contents of the widget. The default implementation does nothing.

Draw within [contentsRect](kxyselector.md#contentsRect)() only.

### \[virtual protected\] void KXYSelector::drawMarker(QPainter \**p*, int *xp*, int *yp*) {#drawMarker}

Override this function to draw the marker which indicates the currently selected value pair.

### void KXYSelector::setMarkerColor(const QColor &*col*) {#setMarkerColor}

Sets the color used to draw the marker

`col` the color

### void KXYSelector::setRange(int *minX*, int *minY*, int *maxX*, int *maxY*) {#setRange}

Sets the range of possible values.

### void KXYSelector::setValues(int *xPos*, int *yPos*) {#setValues}

Sets the current values in horizontal and vertical direction.

`xPos` the horizontal value

`yPos` the vertical value

### void KXYSelector::setXValue(int *xPos*) {#setXValue}

Sets the current horizontal value

`xPos` the horizontal value

> **Note:** Setter function for property [xValue](kxyselector.md#xValue-prop).

*See also* [xValue](kxyselector.md#xValue)()

### void KXYSelector::setYValue(int *yPos*) {#setYValue}

Sets the current vertical value

`yPos` the vertical value

> **Note:** Setter function for property [yValue](kxyselector.md#yValue-prop).

*See also* [yValue](kxyselector.md#yValue)()

### \[signal\] void KXYSelector::valueChanged(int *x*, int *y*) {#valueChanged}

This signal is emitted whenever the user chooses a value, e.g. by clicking with the mouse on the widget.

### \[protected\] void KXYSelector::valuesFromPosition(int *x*, int *y*, int &*xVal*, int &*yVal*) const {#valuesFromPosition}

Converts a pixel position to its corresponding values.

### int KXYSelector::xValue() const {#xValue}

Returns the current value in horizontal direction.

> **Note:** Getter function for property [xValue](kxyselector.md#xValue-prop).

*See also* [setXValue](kxyselector.md#setXValue)()

### int KXYSelector::yValue() const {#yValue}

Returns the current value in vertical direction.

> **Note:** Getter function for property [yValue](kxyselector.md#yValue-prop).

*See also* [setYValue](kxyselector.md#setYValue)()
