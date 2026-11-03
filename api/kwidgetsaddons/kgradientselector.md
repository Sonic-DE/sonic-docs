---
title: "KGradientSelector Class"
description: "Allows the user to choose from a one-dimensional range of colors which is given as a gradient between two colors provided by the programmer."
---

# KGradientSelector Class

Allows the user to choose from a one-dimensional range of colors which is given as a gradient between two colors provided by the programmer. [More...](#details)

- **Header:** `#include <KGradientSelector>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [KSelector](kselector.md)

[List of all members, including inherited members](kgradientselector-members.md)

## Properties

- [firstColor : QColor](#firstColor-prop)
- [firstText : QString](#firstText-prop)
- [secondColor : QColor](#secondColor-prop)
- [secondText : QString](#secondText-prop)

## Public Functions

- [KGradientSelector(QWidget \*parent = nullptr)](#KGradientSelector)
- [KGradientSelector(Qt::Orientation o, QWidget \*parent = nullptr)](#KGradientSelector-1)
- [QColor firstColor() const](#firstColor)
- [QString firstText() const](#firstText)
- [QColor secondColor() const](#secondColor)
- [QString secondText() const](#secondText)
- [void setColors(const QColor &col1, const QColor &col2)](#setColors)
- [void setFirstColor(const QColor &col)](#setFirstColor)
- [void setFirstText(const QString &t)](#setFirstText)
- [void setSecondColor(const QColor &col)](#setSecondColor)
- [void setSecondText(const QString &t)](#setSecondText)
- [void setStops(const QGradientStops &stops)](#setStops)
- [void setText(const QString &t1, const QString &t2)](#setText)
- [QGradientStops stops() const](#stops)

## Protected Functions

- [QSize minimumSize() const](#minimumSize)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### firstColor : QColor {#firstColor-prop}

**Access functions:**

- `QColor` **[firstColor](kgradientselector.md#firstColor)**() const
- `void` **[setFirstColor](kgradientselector.md#setFirstColor)**(const `QColor` &*col*)

### firstText : QString {#firstText-prop}

**Access functions:**

- `QString` **[firstText](kgradientselector.md#firstText)**() const
- `void` **[setFirstText](kgradientselector.md#setFirstText)**(const `QString` &*t*)

### secondColor : QColor {#secondColor-prop}

**Access functions:**

- `QColor` **[secondColor](kgradientselector.md#secondColor)**() const
- `void` **[setSecondColor](kgradientselector.md#setSecondColor)**(const `QColor` &*col*)

### secondText : QString {#secondText-prop}

**Access functions:**

- `QString` **[secondText](kgradientselector.md#secondText)**() const
- `void` **[setSecondText](kgradientselector.md#setSecondText)**(const `QString` &*t*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KGradientSelector::KGradientSelector(QWidget \**parent* = nullptr) {#KGradientSelector}

Constructs a horizontal color selector which contains a gradient between white and black.

### \[explicit\] KGradientSelector::KGradientSelector(Qt::Orientation *o*, QWidget \**parent* = nullptr) {#KGradientSelector-1}

Constructs a colors selector with orientation `o` which contains a gradient between white and black.

### QColor KGradientSelector::firstColor() const {#firstColor}

> **Note:** Getter function for property [firstColor](kgradientselector.md#firstColor-prop).

*See also* [setFirstColor](kgradientselector.md#setFirstColor)()

### QString KGradientSelector::firstText() const {#firstText}

> **Note:** Getter function for property [firstText](kgradientselector.md#firstText-prop).

*See also* [setFirstText](kgradientselector.md#setFirstText)()

### \[virtual protected\] QSize KGradientSelector::minimumSize() const {#minimumSize}

### QColor KGradientSelector::secondColor() const {#secondColor}

> **Note:** Getter function for property [secondColor](kgradientselector.md#secondColor-prop).

*See also* [setSecondColor](kgradientselector.md#setSecondColor)()

### QString KGradientSelector::secondText() const {#secondText}

> **Note:** Getter function for property [secondText](kgradientselector.md#secondText-prop).

*See also* [setSecondText](kgradientselector.md#setSecondText)()

### void KGradientSelector::setColors(const QColor &*col1*, const QColor &*col2*) {#setColors}

Sets the two colors which span the gradient.

### void KGradientSelector::setFirstColor(const QColor &*col*) {#setFirstColor}

Set each color on its own.

> **Note:** Setter function for property [firstColor](kgradientselector.md#firstColor-prop).

*See also* [firstColor](kgradientselector.md#firstColor)()

### void KGradientSelector::setFirstText(const QString &*t*) {#setFirstText}

Set each description on its own

> **Note:** Setter function for property [firstText](kgradientselector.md#firstText-prop).

*See also* [firstText](kgradientselector.md#firstText)()

### void KGradientSelector::setSecondColor(const QColor &*col*) {#setSecondColor}

> **Note:** Setter function for property [secondColor](kgradientselector.md#secondColor-prop).

*See also* [secondColor](kgradientselector.md#secondColor)()

### void KGradientSelector::setSecondText(const QString &*t*) {#setSecondText}

> **Note:** Setter function for property [secondText](kgradientselector.md#secondText-prop).

*See also* [secondText](kgradientselector.md#secondText)()

### void KGradientSelector::setStops(const QGradientStops &*stops*) {#setStops}

Sets the colors that make up the gradient. Any previously set colors are removed.

*See also* [stops](kgradientselector.md#stops)()

### void KGradientSelector::setText(const QString &*t1*, const QString &*t2*) {#setText}

### QGradientStops KGradientSelector::stops() const {#stops}

Get the colors that make up the gradient.

*See also* [setStops](kgradientselector.md#setStops)()
