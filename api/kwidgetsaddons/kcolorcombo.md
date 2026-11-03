---
title: "KColorCombo Class"
description: "Combobox for colors."
---

# KColorCombo Class

Combobox for colors. [More...](#details)

- **Header:** `#include <KColorCombo>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QComboBox](https://doc.qt.io/qt-6/qcombobox.html)

[List of all members, including inherited members](kcolorcombo-members.md)

## Properties

- [color : QColor](#color-prop)
- [colors : QList\<QColor\>](#colors-prop)

## Public Functions

- [KColorCombo(QWidget \*parent = nullptr)](#KColorCombo)
- [QColor color() const](#color)
- [QList\<QColor\> colors() const](#colors)
- [bool isCustomColor() const](#isCustomColor)
- [void setColor(const QColor &col)](#setColor)
- [void setColors(const QList\<QColor\> &colors)](#setColors)
- [void showEmptyList()](#showEmptyList)

## Signals

- [void activated(const QColor &col)](#activated)
- [void highlighted(const QColor &col)](#highlighted)

## Detailed Description {#details}

The combobox provides some preset colors to be selected, and an entry to select a custom color using a color dialog.

## Property Documentation {#property-documentation}

### color : QColor {#color-prop}

**Access functions:**

- `QColor` **[color](kcolorcombo.md#color)**() const
- `void` **[setColor](kcolorcombo.md#setColor)**(const `QColor` &*col*)

**Notifier signal:**

- `void` **[activated](kcolorcombo.md#activated)**(const `QColor` &*col*)

### colors : QList\<QColor\> {#colors-prop}

**Access functions:**

- `QList`\<`QColor`\> **[colors](kcolorcombo.md#colors)**() const
- `void` **[setColors](kcolorcombo.md#setColors)**(const `QList`\<`QColor`\> &*colors*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KColorCombo::KColorCombo(QWidget \**parent* = nullptr) {#KColorCombo}

Constructs a color combo box.

### \[signal\] void KColorCombo::activated(const QColor &*col*) {#activated}

Emitted when a new color box has been selected.

> **Note:** Notifier signal for property [color](kcolorcombo.md#color-prop).

### QColor KColorCombo::color() const {#color}

Returns the currently selected color.

> **Note:** Getter function for property [color](kcolorcombo.md#color-prop).

*See also* [setColor](kcolorcombo.md#setColor)()

### QList\<QColor\> KColorCombo::colors() const {#colors}

Return the list of colors available for selection.

> **Note:** Getter function for property [colors](kcolorcombo.md#colors-prop).

*See also* [setColors](kcolorcombo.md#setColors)()

### \[signal\] void KColorCombo::highlighted(const QColor &*col*) {#highlighted}

Emitted when a new item has been highlighted.

### bool KColorCombo::isCustomColor() const {#isCustomColor}

Find whether the currently selected color is a custom color selected using a color dialog.

### void KColorCombo::setColor(const QColor &*col*) {#setColor}

Selects the color `col`.

> **Note:** Setter function for property [color](kcolorcombo.md#color-prop).

*See also* [color](kcolorcombo.md#color)()

### void KColorCombo::setColors(const QList\<QColor\> &*colors*) {#setColors}

Set a custom list of colors to choose from, in place of the standard list.

`colors` list of colors. If empty, the selection list reverts to the standard list.

> **Note:** Setter function for property [colors](kcolorcombo.md#colors-prop).

*See also* [colors](kcolorcombo.md#colors)()

### void KColorCombo::showEmptyList() {#showEmptyList}

Clear the color list and don't show it, till the next [setColor](kcolorcombo.md#setColor)() call
