---
title: "KColorButton Class"
description: "A pushbutton to display or allow user selection of a color."
---

# KColorButton Class

A pushbutton to display or allow user selection of a color. [More...](#details)

- **Header:** `#include <KColorButton>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QPushButton](https://doc.qt.io/qt-6/qpushbutton.html)

[List of all members, including inherited members](kcolorbutton-members.md)

## Properties

- [alphaChannelEnabled : bool](#alphaChannelEnabled-prop)
- [color : QColor](#color-prop)
- [defaultColor : QColor](#defaultColor-prop)

## Public Functions

- [KColorButton(QWidget \*parent = nullptr)](#KColorButton)
- [KColorButton(const QColor &c, QWidget \*parent = nullptr)](#KColorButton-1)
- [KColorButton(const QColor &c, const QColor &defaultColor, QWidget \*parent = nullptr)](#KColorButton-2)
- [QColor color() const](#color)
- [QColor defaultColor() const](#defaultColor)
- [bool isAlphaChannelEnabled() const](#isAlphaChannelEnabled)
- [void setAlphaChannelEnabled(bool alpha)](#setAlphaChannelEnabled)
- [void setColor(const QColor &c)](#setColor)
- [void setDefaultColor(const QColor &c)](#setDefaultColor)

## Signals

- [void changed(const QColor &newColor)](#changed)

## Detailed Description {#details}

This widget can be used to display or allow user selection of a color.

*See also* [QColorDialog](https://doc.qt.io/qt-6/qcolordialog.html)

## Property Documentation {#property-documentation}

### alphaChannelEnabled : bool {#alphaChannelEnabled-prop}

**Access functions:**

- `bool` **[isAlphaChannelEnabled](kcolorbutton.md#isAlphaChannelEnabled)**() const
- `void` **[setAlphaChannelEnabled](kcolorbutton.md#setAlphaChannelEnabled)**(`bool` *alpha*)

### color : QColor {#color-prop}

**Access functions:**

- `QColor` **[color](kcolorbutton.md#color)**() const
- `void` **[setColor](kcolorbutton.md#setColor)**(const `QColor` &*c*)

**Notifier signal:**

- `void` **[changed](kcolorbutton.md#changed)**(const `QColor` &*newColor*)

### defaultColor : QColor {#defaultColor-prop}

**Access functions:**

- `QColor` **[defaultColor](kcolorbutton.md#defaultColor)**() const
- `void` **[setDefaultColor](kcolorbutton.md#setDefaultColor)**(const `QColor` &*c*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KColorButton::KColorButton(QWidget \**parent* = nullptr) {#KColorButton}

Creates a color button.

### \[explicit\] KColorButton::KColorButton(const QColor &*c*, QWidget \**parent* = nullptr) {#KColorButton-1}

Creates a color button with an initial color `c`.

### KColorButton::KColorButton(const QColor &*c*, const QColor &*defaultColor*, QWidget \**parent* = nullptr) {#KColorButton-2}

Creates a color button with an initial color `c` and default color `defaultColor`.

### \[signal\] void KColorButton::changed(const QColor &*newColor*) {#changed}

Emitted when the color of the widget is changed, either with [setColor](kcolorbutton.md#setColor)() or via user selection.

> **Note:** Notifier signal for property [color](kcolorbutton.md#color-prop).

### QColor KColorButton::color() const {#color}

Returns the currently chosen color.

> **Note:** Getter function for property [color](kcolorbutton.md#color-prop).

*See also* [setColor](kcolorbutton.md#setColor)()

### QColor KColorButton::defaultColor() const {#defaultColor}

Returns the default color or an invalid color if no default color is set.

> **Note:** Getter function for property [defaultColor](kcolorbutton.md#defaultColor-prop).

*See also* [setDefaultColor](kcolorbutton.md#setDefaultColor)()

### bool KColorButton::isAlphaChannelEnabled() const {#isAlphaChannelEnabled}

Returns true if the user is allowed to change the alpha component.

> **Note:** Getter function for property [alphaChannelEnabled](kcolorbutton.md#alphaChannelEnabled-prop).

### void KColorButton::setAlphaChannelEnabled(bool *alpha*) {#setAlphaChannelEnabled}

When set to true, allow the user to change the alpha component of the color. The default value is false.

> **Note:** Setter function for property [alphaChannelEnabled](kcolorbutton.md#alphaChannelEnabled-prop).

*See also* [isAlphaChannelEnabled](kcolorbutton.md#isAlphaChannelEnabled)()

### void KColorButton::setColor(const QColor &*c*) {#setColor}

Sets the current color to `c`.

> **Note:** Setter function for property [color](kcolorbutton.md#color-prop).

*See also* [color](kcolorbutton.md#color)()

### void KColorButton::setDefaultColor(const QColor &*c*) {#setDefaultColor}

Sets the default color to `c`.

> **Note:** Setter function for property [defaultColor](kcolorbutton.md#defaultColor-prop).

*See also* [defaultColor](kcolorbutton.md#defaultColor)()
