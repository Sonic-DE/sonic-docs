---
title: "KCapacityBar Class"
description: "This widget shows a bar which is filled to show the level of usage of a certain device."
---

# KCapacityBar Class

This widget shows a bar which is filled to show the level of usage of a certain device. [More...](#details)

- **Header:** `#include <KCapacityBar>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kcapacitybar-members.md)

## Public Types

- [enum KCapacityBar::DrawTextMode](#DrawTextMode-enum)

## Properties

- [barHeight : int](#barHeight-prop)
- [continuous : bool](#continuous-prop)
- [drawTextMode : DrawTextMode](#drawTextMode-prop)
- [fillFullBlocks : bool](#fillFullBlocks-prop)
- [horizontalTextAlignment : Qt::Alignment](#horizontalTextAlignment-prop)
- [text : QString](#text-prop)
- [value : int](#value-prop)

## Public Functions

- [KCapacityBar(QWidget \*parent = nullptr)](#KCapacityBar)
- [KCapacityBar(KCapacityBar::DrawTextMode drawTextMode, QWidget \*parent = nullptr)](#KCapacityBar-1)
- [int barHeight() const](#barHeight)
- [bool continuous() const](#continuous)
- [void drawCapacityBar(QPainter \*p, const QRect &rect) const](#drawCapacityBar)
- [void drawCapacityBar(QPainter \*p, const QRect &rect, QStyle::State state) const](#drawCapacityBar-1) (since 6.12)
- [KCapacityBar::DrawTextMode drawTextMode() const](#drawTextMode)
- [bool fillFullBlocks() const](#fillFullBlocks)
- [Qt::Alignment horizontalTextAlignment() const](#horizontalTextAlignment)
- [void setBarHeight(int barHeight)](#setBarHeight)
- [void setContinuous(bool continuous)](#setContinuous)
- [void setDrawTextMode(KCapacityBar::DrawTextMode mode)](#setDrawTextMode)
- [void setFillFullBlocks(bool fillFullBlocks)](#setFillFullBlocks)
- [void setHorizontalTextAlignment(Qt::Alignment textAlignment)](#setHorizontalTextAlignment)
- [void setText(const QString &text)](#setText)
- [void setValue(int value)](#setValue)
- [QString text() const](#text)
- [int value() const](#value)

## Detailed Description {#details}

This widget represents a bar which goal is to show the level of usage of a device. Its look is similar to a progress bar, but different, because this widget does not want to give a notion of progress.

## Member Type Documentation {#member-type-documentation}

### enum KCapacityBar::DrawTextMode {#DrawTextMode-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KCapacityBar::DrawTextInline` | `0` | If any text set, draw it into the capacity bar |
| `KCapacityBar::DrawTextOutline` | `1` | If any text set, draw it out of the capacity bar |

## Property Documentation {#property-documentation}

### barHeight : int {#barHeight-prop}

**Access functions:**

- `int` **[barHeight](kcapacitybar.md#barHeight)**() const
- `void` **[setBarHeight](kcapacitybar.md#setBarHeight)**(`int` *barHeight*)

### continuous : bool {#continuous-prop}

**Access functions:**

- `bool` **[continuous](kcapacitybar.md#continuous)**() const
- `void` **[setContinuous](kcapacitybar.md#setContinuous)**(`bool` *continuous*)

### drawTextMode : DrawTextMode {#drawTextMode-prop}

**Access functions:**

- `KCapacityBar::DrawTextMode` **[drawTextMode](kcapacitybar.md#drawTextMode)**() const
- `void` **[setDrawTextMode](kcapacitybar.md#setDrawTextMode)**(`KCapacityBar::DrawTextMode` *mode*)

### fillFullBlocks : bool {#fillFullBlocks-prop}

**Access functions:**

- `bool` **[fillFullBlocks](kcapacitybar.md#fillFullBlocks)**() const
- `void` **[setFillFullBlocks](kcapacitybar.md#setFillFullBlocks)**(`bool` *fillFullBlocks*)

### horizontalTextAlignment : Qt::Alignment {#horizontalTextAlignment-prop}

**Access functions:**

- `Qt::Alignment` **[horizontalTextAlignment](kcapacitybar.md#horizontalTextAlignment)**() const
- `void` **[setHorizontalTextAlignment](kcapacitybar.md#setHorizontalTextAlignment)**(`Qt::Alignment` *textAlignment*)

### text : QString {#text-prop}

**Access functions:**

- `QString` **[text](kcapacitybar.md#text)**() const
- `void` **[setText](kcapacitybar.md#setText)**(const `QString` &*text*)

### value : int {#value-prop}

**Access functions:**

- `int` **[value](kcapacitybar.md#value)**() const
- `void` **[setValue](kcapacitybar.md#setValue)**(`int` *value*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KCapacityBar::KCapacityBar(QWidget \**parent* = nullptr) {#KCapacityBar}

Constructs a capacity bar with [DrawTextOutline](kcapacitybar.md#DrawTextMode-enum) as draw text mode.

`parent` The parent of the widget.

### \[explicit\] KCapacityBar::KCapacityBar(KCapacityBar::DrawTextMode *drawTextMode*, QWidget \**parent* = nullptr) {#KCapacityBar-1}

Capacity bar constructor.

`drawTextMode` If any text set, whether to draw it into the capacity bar or not.

`parent` The parent of the widget.

### int KCapacityBar::barHeight() const {#barHeight}

Returns the preferred height of the capacity bar.

> **Note:** Getter function for property [barHeight](kcapacitybar.md#barHeight-prop).

*See also* [setBarHeight](kcapacitybar.md#setBarHeight)()

### bool KCapacityBar::continuous() const {#continuous}

Returns whether the fill of the capacity bar should be continuous or block-based.

> **Note:** Getter function for property [continuous](kcapacitybar.md#continuous-prop).

*See also* [setContinuous](kcapacitybar.md#setContinuous)()

### void KCapacityBar::drawCapacityBar(QPainter \**p*, const QRect &*rect*) const {#drawCapacityBar}

This method allows you to draw the widget, directly, for example on item delegates. You only need the painter object and the rect where this widget should be drawn.

### \[since 6.12\] void KCapacityBar::drawCapacityBar(QPainter \**p*, const QRect &*rect*, QStyle::State *state*) const {#drawCapacityBar-1}

This method allows you to draw the widget, directly, for example on item delegates. You need the painter object and the rect where this widget should be drawn, and the state that it should be painted in.

For example, when in a selected delegate, setting the correct state ensures that the bar keeps sufficient contrast to the selection color.

This function was introduced in Qt 6.12.

### KCapacityBar::DrawTextMode KCapacityBar::drawTextMode() const {#drawTextMode}

The way text is drawn, inside the capacity bar or outside of it

> **Note:** Getter function for property [drawTextMode](kcapacitybar.md#drawTextMode-prop).

*See also* [setDrawTextMode](kcapacitybar.md#setDrawTextMode)()

### bool KCapacityBar::fillFullBlocks() const {#fillFullBlocks}

Returns whether the last block shown can be cut off when necessary.

> **Note:** Getter function for property [fillFullBlocks](kcapacitybar.md#fillFullBlocks-prop).

*See also* [setFillFullBlocks](kcapacitybar.md#setFillFullBlocks)()

### Qt::Alignment KCapacityBar::horizontalTextAlignment() const {#horizontalTextAlignment}

Returns the horizontal alignment for the text that will be drawn.

> **Note:** Getter function for property [horizontalTextAlignment](kcapacitybar.md#horizontalTextAlignment-prop).

*See also* [setHorizontalTextAlignment](kcapacitybar.md#setHorizontalTextAlignment)()

### void KCapacityBar::setBarHeight(int *barHeight*) {#setBarHeight}

Sets the height (in pixels) of the bar.

`barHeight` The preferred height (in pixels) of the capacity bar.

> **Note:** If you set a certain text and the capacity bar is in inline mode, the height of the bar will be the maximum of the font height and this value.

> **Note:** If you set a certain text and the capacity bar is in outline mode, the height of the whole capacity bar will be bigger than this value. Take in count the height of this widget is got from adding the bar height, the font metrics height and a small separator between the bar and the outline text.

> **Note:** Its value is 12 pixels by default.

> **Note:** Setter function for property [barHeight](kcapacitybar.md#barHeight-prop).

*See also* [barHeight](kcapacitybar.md#barHeight)()

### void KCapacityBar::setContinuous(bool *continuous*) {#setContinuous}

Sets whether the fill of the capacity bar should be continuous or in block mode.

`continuous` If true, the fill of the capacity bar is done in a continuous way. In other case, the fill is done with separated blocks.

> **Note:** Its value is true by default.

> **Note:** Setter function for property [continuous](kcapacitybar.md#continuous-prop).

*See also* [continuous](kcapacitybar.md#continuous)()

### void KCapacityBar::setDrawTextMode(KCapacityBar::DrawTextMode *mode*) {#setDrawTextMode}

Set the way text is drawn if any is set

`mode` If any text set, whether to draw it into the capacity bar or not.

> **Note:** Setter function for property [drawTextMode](kcapacitybar.md#drawTextMode-prop).

*See also* [drawTextMode](kcapacitybar.md#drawTextMode)()

### void KCapacityBar::setFillFullBlocks(bool *fillFullBlocks*) {#setFillFullBlocks}

When the capacity bar is non-continuous, sets whether the last block shown should be drawn full or can be cut off (depending on the capacity bar width, and the value set on it).

`fillFullBlocks` If true, the last block drawn will be fully filled, on other case, the last block drawn could be cut off.

> **Note:** This method is only relevant if the capacity bar is in non-continuous mode.

Its value is true by default.

> **Note:** Setter function for property [fillFullBlocks](kcapacitybar.md#fillFullBlocks-prop).

*See also* [fillFullBlocks](kcapacitybar.md#fillFullBlocks)(), [setContinuous](kcapacitybar.md#setContinuous), [continuous](kcapacitybar.md#continuous)

### void KCapacityBar::setHorizontalTextAlignment(Qt::Alignment *textAlignment*) {#setHorizontalTextAlignment}

If the capacity bar is in outline text mode, draw the text with `textAlignment` alignment.

`textAlignment` Sets the horizontal alignment for the text if the capacity bar is in outline text mode.

> **Note:** If `textAlignemt` contains vertical alignment flags, they will be ignored.

> **Note:** If the capacity bar is in inline text mode, the text is always centered, and both vertical and horizontal flags set through this method are ignored.

> **Note:** Its value is centered by default.

> **Note:** Setter function for property [horizontalTextAlignment](kcapacitybar.md#horizontalTextAlignment-prop).

*See also* [horizontalTextAlignment](kcapacitybar.md#horizontalTextAlignment)()

### void KCapacityBar::setText(const QString &*text*) {#setText}

Sets the text for the capacity bar.

`text` The text that the capacity bar will show.

This is an empty string by default.

> **Note:** Setter function for property [text](kcapacitybar.md#text-prop).

*See also* [text](kcapacitybar.md#text)()

### void KCapacityBar::setValue(int *value*) {#setValue}

Capacity bar fill value.

`value` This parameter can take values from 0 to 100.

Its value is 0 by default.

> **Note:** Setter function for property [value](kcapacitybar.md#value-prop).

*See also* [value](kcapacitybar.md#value)()

### QString KCapacityBar::text() const {#text}

Returns the text that the capacity bar will show.

> **Note:** Getter function for property [text](kcapacitybar.md#text-prop).

*See also* [setText](kcapacitybar.md#setText)()

### int KCapacityBar::value() const {#value}

Returns the fill value of the capacity bar.

> **Note:** Getter function for property [value](kcapacitybar.md#value-prop).

*See also* [setValue](kcapacitybar.md#setValue)()
