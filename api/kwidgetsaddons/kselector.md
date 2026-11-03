---
title: "KSelector Class"
description: "Base class for other widgets which provides the ability to choose from a one-dimensional range of values."
---

# KSelector Class

Base class for other widgets which provides the ability to choose from a one-dimensional range of values. [More...](#details)

- **Header:** `#include <KSelector>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QAbstractSlider](https://doc.qt.io/qt-6/qabstractslider.html)
- **Inherited By:** [KGradientSelector](kgradientselector.md)

[List of all members, including inherited members](kselector-members.md)

## Properties

- [arrowDirection : Qt::ArrowType](#arrowDirection-prop)
- [indent : bool](#indent-prop)
- [maxValue : int](#maxValue-prop)
- [minValue : int](#minValue-prop)
- [value : int](#value-prop)

## Public Functions

- [KSelector(QWidget \*parent = nullptr)](#KSelector)
- [KSelector(Qt::Orientation o, QWidget \*parent = nullptr)](#KSelector-1)
- [Qt::ArrowType arrowDirection() const](#arrowDirection)
- [QRect contentsRect() const](#contentsRect)
- [bool indent() const](#indent)
- [void setArrowDirection(Qt::ArrowType direction)](#setArrowDirection)
- [void setIndent(bool i)](#setIndent)

## Protected Functions

- [void drawArrow(QPainter \*painter, const QPoint &pos)](#drawArrow)
- [void drawContents(QPainter \*)](#drawContents)

## Detailed Description {#details}

An example is the [KGradientSelector](kgradientselector.md) which allows to choose from a range of colors.

A custom drawing routine for the widget surface has to be provided by the subclass.

## Property Documentation {#property-documentation}

### arrowDirection : Qt::ArrowType {#arrowDirection-prop}

**Access functions:**

- `Qt::ArrowType` **[arrowDirection](kselector.md#arrowDirection)**() const
- `void` **[setArrowDirection](kselector.md#setArrowDirection)**(`Qt::ArrowType` *direction*)

### indent : bool {#indent-prop}

**Access functions:**

- `bool` **[indent](kselector.md#indent)**() const
- `void` **[setIndent](kselector.md#setIndent)**(`bool` *i*)

### maxValue : int {#maxValue-prop}

### minValue : int {#minValue-prop}

### value : int {#value-prop}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KSelector::KSelector(QWidget \**parent* = nullptr) {#KSelector}

Constructs a horizontal one-dimensional selection widget.

### \[explicit\] KSelector::KSelector(Qt::Orientation *o*, QWidget \**parent* = nullptr) {#KSelector-1}

Constructs a one-dimensional selection widget with a given orientation.

### Qt::ArrowType KSelector::arrowDirection() const {#arrowDirection}

Returns the current arrow direction

> **Note:** Getter function for property [arrowDirection](kselector.md#arrowDirection-prop).

*See also* [setArrowDirection](kselector.md#setArrowDirection)()

### QRect KSelector::contentsRect() const {#contentsRect}

Returns the rectangle on which subclasses should draw.

### \[virtual protected\] void KSelector::drawArrow(QPainter \**painter*, const QPoint &*pos*) {#drawArrow}

Override this function to draw the cursor which indicates the current value.

### \[virtual protected\] void KSelector::drawContents(*QPainter \**) {#drawContents}

Override this function to draw the contents of the control. The default implementation does nothing.

Draw only within [contentsRect](kselector.md#contentsRect)().

### bool KSelector::indent() const {#indent}

Returns whether the indent option is set.

> **Note:** Getter function for property [indent](kselector.md#indent-prop).

*See also* [setIndent](kselector.md#setIndent)()

### void KSelector::setArrowDirection(Qt::ArrowType *direction*) {#setArrowDirection}

Sets the arrow direction.

> **Note:** Setter function for property [arrowDirection](kselector.md#arrowDirection-prop).

*See also* [arrowDirection](kselector.md#arrowDirection)()

### void KSelector::setIndent(bool *i*) {#setIndent}

Sets the indent option of the widget to i.

This determines whether a shaded frame is drawn.

> **Note:** Setter function for property [indent](kselector.md#indent-prop).

*See also* [indent](kselector.md#indent)()
