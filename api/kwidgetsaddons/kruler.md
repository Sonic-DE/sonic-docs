---
title: "KRuler Class"
description: "A ruler widget."
---

# KRuler Class

A ruler widget. [More...](#details)

- **Header:** `#include <KRuler>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QAbstractSlider](https://doc.qt.io/qt-6/qabstractslider.html)

[List of all members, including inherited members](kruler-members.md)

## Public Types

- [enum KRuler::MetricStyle](#MetricStyle-enum)

## Properties

- [bigMarkDistance : int](#bigMarkDistance-prop)
- [endLabel : QString](#endLabel-prop)
- [\[read-only\] endOffset : int](#endOffset-prop)
- [length : int](#length-prop)
- [lengthFixed : bool](#lengthFixed-prop)
- [littleMarkDistance : int](#littleMarkDistance-prop)
- [mediumMarkDistance : int](#mediumMarkDistance-prop)
- [\[read-only\] offset : int](#offset-prop)
- [pixelPerMark : double](#pixelPerMark-prop)
- [showBigMarks : bool](#showBigMarks-prop)
- [showEndLabel : bool](#showEndLabel-prop)
- [showLittleMarks : bool](#showLittleMarks-prop)
- [showMediumMarks : bool](#showMediumMarks-prop)
- [showPointer : bool](#showPointer-prop)
- [showTinyMarks : bool](#showTinyMarks-prop)
- [tinyMarkDistance : int](#tinyMarkDistance-prop)

## Public Functions

- [KRuler(QWidget \*parent = nullptr)](#KRuler)
- [KRuler(Qt::Orientation orient, QWidget \*parent = nullptr, Qt::WindowFlags f = WindowFlags())](#KRuler-1)
- [KRuler(Qt::Orientation orient, int widgetWidth, QWidget \*parent = nullptr, Qt::WindowFlags f = WindowFlags())](#KRuler-2)
- [int bigMarkDistance() const](#bigMarkDistance)
- [QString endLabel() const](#endLabel)
- [int endOffset() const](#endOffset)
- [int length() const](#length)
- [bool lengthFixed() const](#lengthFixed)
- [int littleMarkDistance() const](#littleMarkDistance)
- [int mediumMarkDistance() const](#mediumMarkDistance)
- [int offset() const](#offset)
- [double pixelPerMark() const](#pixelPerMark)
- [void setBigMarkDistance(int)](#setBigMarkDistance)
- [void setEndLabel(const QString &)](#setEndLabel)
- [void setLength(int)](#setLength)
- [void setLengthFixed(bool fix)](#setLengthFixed)
- [void setLittleMarkDistance(int)](#setLittleMarkDistance)
- [void setMediumMarkDistance(int)](#setMediumMarkDistance)
- [void setOffset(int offset)](#setOffset)
- [void setPixelPerMark(double rate)](#setPixelPerMark)
- [void setRulerMetricStyle(KRuler::MetricStyle)](#setRulerMetricStyle)
- [void setShowBigMarks(bool)](#setShowBigMarks)
- [void setShowEndLabel(bool)](#setShowEndLabel)
- [void setShowEndMarks(bool)](#setShowEndMarks)
- [void setShowLittleMarks(bool)](#setShowLittleMarks)
- [void setShowMediumMarks(bool)](#setShowMediumMarks)
- [void setShowPointer(bool)](#setShowPointer)
- [void setShowTinyMarks(bool)](#setShowTinyMarks)
- [void setTinyMarkDistance(int)](#setTinyMarkDistance)
- [bool showBigMarks() const](#showBigMarks)
- [bool showEndLabel() const](#showEndLabel)
- [bool showEndMarks() const](#showEndMarks)
- [bool showLittleMarks() const](#showLittleMarks)
- [bool showMediumMarks() const](#showMediumMarks)
- [bool showPointer() const](#showPointer)
- [bool showTinyMarks() const](#showTinyMarks)
- [void slideDown(int count = 1)](#slideDown)
- [void slideUp(int count = 1)](#slideUp)
- [int tinyMarkDistance() const](#tinyMarkDistance)

## Public Slots

- [void slotEndOffset(int)](#slotEndOffset)
- [void slotNewOffset(int)](#slotNewOffset)
- [void slotNewValue(int)](#slotNewValue)

## Detailed Description {#details}

The vertical ruler looks similar to this:

```cpp
meters                       inches

------   <--- end mark  ---> ------
    --                            -
    --   <---little mark--->     --
    --                            -
    --                          ---
   ---   <---medium mark          -
    --                           --
    --        tiny mark---->      -
    --                         ----
    --                            -
  ----   <-----big mark          --
    --                            -
  |>--   <--ruler pointer-->   |>--
```

There are tiny marks, little marks, medium marks, and big marks along the ruler.

To receive mouse clicks or mouse moves, the class has to be overloaded.

## Member Type Documentation {#member-type-documentation}

### enum KRuler::MetricStyle {#MetricStyle-enum}

The types of units used.

| Constant |   |
| --- | --- |
| `KRuler::Custom` | `0` |
| `KRuler::Pixel` | `1` |
| `KRuler::Inch` | `2` |
| `KRuler::Millimetres` | `3` |
| `KRuler::Centimetres` | `4` |
| `KRuler::Metres` | `5` |

## Property Documentation {#property-documentation}

### bigMarkDistance : int {#bigMarkDistance-prop}

**Access functions:**

- `int` **[bigMarkDistance](kruler.md#bigMarkDistance)**() const
- `void` **[setBigMarkDistance](kruler.md#setBigMarkDistance)**(*int*)

### endLabel : QString {#endLabel-prop}

**Access functions:**

- `QString` **[endLabel](kruler.md#endLabel)**() const
- `void` **[setEndLabel](kruler.md#setEndLabel)**(*const QString &*)

### \[read-only\] endOffset : int {#endOffset-prop}

**Access functions:**

- `int` **[endOffset](kruler.md#endOffset)**() const

### length : int {#length-prop}

**Access functions:**

- `int` **[length](kruler.md#length)**() const
- `void` **[setLength](kruler.md#setLength)**(*int*)

### lengthFixed : bool {#lengthFixed-prop}

**Access functions:**

- `bool` **[lengthFixed](kruler.md#lengthFixed)**() const
- `void` **[setLengthFixed](kruler.md#setLengthFixed)**(`bool` *fix*)

### littleMarkDistance : int {#littleMarkDistance-prop}

**Access functions:**

- `int` **[littleMarkDistance](kruler.md#littleMarkDistance)**() const
- `void` **[setLittleMarkDistance](kruler.md#setLittleMarkDistance)**(*int*)

### mediumMarkDistance : int {#mediumMarkDistance-prop}

**Access functions:**

- `int` **[mediumMarkDistance](kruler.md#mediumMarkDistance)**() const
- `void` **[setBigMarkDistance](kruler.md#setBigMarkDistance)**(*int*)

### \[read-only\] offset : int {#offset-prop}

**Access functions:**

- `int` **[offset](kruler.md#offset)**() const

### pixelPerMark : double {#pixelPerMark-prop}

**Access functions:**

- `double` **[pixelPerMark](kruler.md#pixelPerMark)**() const
- `void` **[setPixelPerMark](kruler.md#setPixelPerMark)**(`double` *rate*)

### showBigMarks : bool {#showBigMarks-prop}

**Access functions:**

- `bool` **[showBigMarks](kruler.md#showBigMarks)**() const
- `void` **[setShowBigMarks](kruler.md#setShowBigMarks)**(*bool*)

### showEndLabel : bool {#showEndLabel-prop}

**Access functions:**

- `bool` **[showEndLabel](kruler.md#showEndLabel)**() const
- `void` **[setShowEndLabel](kruler.md#setShowEndLabel)**(*bool*)

### showLittleMarks : bool {#showLittleMarks-prop}

**Access functions:**

- `bool` **[showLittleMarks](kruler.md#showLittleMarks)**() const
- `void` **[setShowLittleMarks](kruler.md#setShowLittleMarks)**(*bool*)

### showMediumMarks : bool {#showMediumMarks-prop}

**Access functions:**

- `bool` **[showMediumMarks](kruler.md#showMediumMarks)**() const
- `void` **[setShowMediumMarks](kruler.md#setShowMediumMarks)**(*bool*)

### showPointer : bool {#showPointer-prop}

**Access functions:**

- `bool` **[showPointer](kruler.md#showPointer)**() const
- `void` **[setShowPointer](kruler.md#setShowPointer)**(*bool*)

### showTinyMarks : bool {#showTinyMarks-prop}

**Access functions:**

- `bool` **[showTinyMarks](kruler.md#showTinyMarks)**() const
- `void` **[setShowTinyMarks](kruler.md#setShowTinyMarks)**(*bool*)

### tinyMarkDistance : int {#tinyMarkDistance-prop}

**Access functions:**

- `int` **[tinyMarkDistance](kruler.md#tinyMarkDistance)**() const
- `void` **[setTinyMarkDistance](kruler.md#setTinyMarkDistance)**(*int*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KRuler::KRuler(QWidget \**parent* = nullptr) {#KRuler}

Constructs a horizontal ruler.

### \[explicit\] KRuler::KRuler(Qt::Orientation *orient*, QWidget \**parent* = nullptr, Qt::WindowFlags *f* = Qt::WindowFlags()) {#KRuler-1}

Constructs a ruler with orientation `orient`.

`parent` and `f` are passed to [QFrame](https://doc.qt.io/qt-6/qframe.html). The default look is a raised widget but may be changed with the inherited [QFrame](https://doc.qt.io/qt-6/qframe.html) methods.

`orient` Orientation of the ruler.

`parent` Will be handed over to [QFrame](https://doc.qt.io/qt-6/qframe.html).

`f` Will be handed over to [QFrame](https://doc.qt.io/qt-6/qframe.html).

### KRuler::KRuler(Qt::Orientation *orient*, int *widgetWidth*, QWidget \**parent* = nullptr, Qt::WindowFlags *f* = Qt::WindowFlags()) {#KRuler-2}

Constructs a ruler with orientation `orient` and initial width `widgetWidth`.

The width sets the fixed width of the widget. This is useful if you want to draw the ruler bigger or smaller than the default size.

> **Note:** The size of the marks doesn't change.

`parent` and `f` are passed to [QFrame](https://doc.qt.io/qt-6/qframe.html).

`orient` Orientation of the ruler.

`widgetWidth` Fixed width of the widget.

`parent` Will be handed over to [QFrame](https://doc.qt.io/qt-6/qframe.html).

`f` Will be handed over to [QFrame](https://doc.qt.io/qt-6/qframe.html).

### int KRuler::bigMarkDistance() const {#bigMarkDistance}

Returns the distance between big marks.

> **Note:** Getter function for property [bigMarkDistance](kruler.md#bigMarkDistance-prop).

*See also* [setBigMarkDistance](kruler.md#setBigMarkDistance)()

### QString KRuler::endLabel() const {#endLabel}

> **Note:** Getter function for property [endLabel](kruler.md#endLabel-prop).

*See also* [setEndLabel](kruler.md#setEndLabel)()

### int KRuler::endOffset() const {#endOffset}

> **Note:** Getter function for property [endOffset](kruler.md#endOffset-prop).

### int KRuler::length() const {#length}

> **Note:** Getter function for property [length](kruler.md#length-prop).

*See also* [setLength](kruler.md#setLength)()

### bool KRuler::lengthFixed() const {#lengthFixed}

> **Note:** Getter function for property [lengthFixed](kruler.md#lengthFixed-prop).

*See also* [setLengthFixed](kruler.md#setLengthFixed)()

### int KRuler::littleMarkDistance() const {#littleMarkDistance}

Returns the distance between little marks.

> **Note:** Getter function for property [littleMarkDistance](kruler.md#littleMarkDistance-prop).

*See also* [setLittleMarkDistance](kruler.md#setLittleMarkDistance)()

### int KRuler::mediumMarkDistance() const {#mediumMarkDistance}

> **Note:** Getter function for property [mediumMarkDistance](kruler.md#mediumMarkDistance-prop).

*See also* [setMediumMarkDistance](kruler.md#setMediumMarkDistance)()

### int KRuler::offset() const {#offset}

Returns the current ruler offset.

> **Note:** Getter function for property [offset](kruler.md#offset-prop).

*See also* [setOffset](kruler.md#setOffset)()

### double KRuler::pixelPerMark() const {#pixelPerMark}

Returns the number of pixels between two base marks.

> **Note:** Getter function for property [pixelPerMark](kruler.md#pixelPerMark-prop).

*See also* [setPixelPerMark](kruler.md#setPixelPerMark)()

### void KRuler::setBigMarkDistance(*int*) {#setBigMarkDistance}

Sets distance between big marks.

For English (inches) or metric styles it is twice the medium mark distance.

> **Note:** Setter function for properties [bigMarkDistance](kruler.md#bigMarkDistance-prop) and [mediumMarkDistance](kruler.md#mediumMarkDistance-prop).

*See also* [bigMarkDistance](kruler.md#bigMarkDistance)()

### void KRuler::setEndLabel(*const QString &*) {#setEndLabel}

Sets the label this is drawn at the beginning of the visible part of the ruler to `label`

> **Note:** Setter function for property [endLabel](kruler.md#endLabel-prop).

*See also* [endLabel](kruler.md#endLabel)()

### void KRuler::setLength(*int*) {#setLength}

Sets the length of the ruler, i.e. the difference between the begin mark and the end mark of the ruler.

Same as ([width](https://doc.qt.io/qt-6/qwidget.html#width-prop)() - [offset](kruler.md#offset)())

when the length is not locked, it gets adjusted with the length of the widget.

> **Note:** Setter function for property [length](kruler.md#length-prop).

*See also* [length](kruler.md#length)()

### void KRuler::setLengthFixed(bool *fix*) {#setLengthFixed}

Locks the length of the ruler, i.e. the difference between the two end marks doesn't change when the widget is resized.

`fix` fixes the length, if true

> **Note:** Setter function for property [lengthFixed](kruler.md#lengthFixed-prop).

*See also* [lengthFixed](kruler.md#lengthFixed)()

### void KRuler::setLittleMarkDistance(*int*) {#setLittleMarkDistance}

Sets the distance between little marks.

The default value is 1 in the metric system and 2 in the English (inches) system.

> **Note:** Setter function for property [littleMarkDistance](kruler.md#littleMarkDistance-prop).

*See also* [littleMarkDistance](kruler.md#littleMarkDistance)()

### void KRuler::setMediumMarkDistance(*int*) {#setMediumMarkDistance}

Sets the distance between medium marks.

For English (inches) styles it defaults to twice the little mark distance. For metric styles it defaults to five times the little mark distance.

*See also* [mediumMarkDistance](kruler.md#mediumMarkDistance)()

### void KRuler::setOffset(int *offset*) {#setOffset}

Sets the ruler slide offset.

This is like slideup() or slidedown() with an absolute offset from the start of the ruler.

`offset` Number of pixel to move the ruler up or left from the beginning

*See also* [offset](kruler.md#offset)()

### void KRuler::setPixelPerMark(double *rate*) {#setPixelPerMark}

Sets the number of pixels between two base marks.

Calling this method stretches or shrinks your ruler.

For pixel display ( [MetricStyle](kruler.md#MetricStyle-enum)) the value is 10.0 marks per pixel ;-)

For English (inches) it is 9.0, and for centimetres ~2.835 -\> 3.0 . If you want to magnify your part of display, you have to adjust the mark distance here.

Notice: The double type is only supported to give the possibility of having some double values. It should be used with care. Using values below 10.0 shows visible jumps of markpositions (e.g. 2.345). Using whole numbers is highly recommended.

To use int values use setPixelPerMark((int)your\_int\_value);

default: 1 mark per 10 pixels

> **Note:** Setter function for property [pixelPerMark](kruler.md#pixelPerMark-prop).

*See also* [pixelPerMark](kruler.md#pixelPerMark)()

### void KRuler::setRulerMetricStyle(*KRuler::MetricStyle*) {#setRulerMetricStyle}

Sets up the necessary tasks for the provided styles.

A convenience method.

### void KRuler::setShowBigMarks(*bool*) {#setShowBigMarks}

Shows/hides big marks.

> **Note:** Setter function for property [showBigMarks](kruler.md#showBigMarks-prop).

*See also* [showBigMarks](kruler.md#showBigMarks)()

### void KRuler::setShowEndLabel(*bool*) {#setShowEndLabel}

Show/hide number values of the end marks.

Default is `false`.

> **Note:** Setter function for property [showEndLabel](kruler.md#showEndLabel-prop).

*See also* [showEndLabel](kruler.md#showEndLabel)()

### void KRuler::setShowEndMarks(*bool*) {#setShowEndMarks}

Shows/hides end marks.

*See also* [showEndMarks](kruler.md#showEndMarks)()

### void KRuler::setShowLittleMarks(*bool*) {#setShowLittleMarks}

Shows/hides little marks.

> **Note:** Setter function for property [showLittleMarks](kruler.md#showLittleMarks-prop).

*See also* [showLittleMarks](kruler.md#showLittleMarks)()

### void KRuler::setShowMediumMarks(*bool*) {#setShowMediumMarks}

Shows/hides medium marks.

> **Note:** Setter function for property [showMediumMarks](kruler.md#showMediumMarks-prop).

*See also* [showMediumMarks](kruler.md#showMediumMarks)()

### void KRuler::setShowPointer(*bool*) {#setShowPointer}

Shows/hides the pointer.

> **Note:** Setter function for property [showPointer](kruler.md#showPointer-prop).

*See also* [showPointer](kruler.md#showPointer)()

### void KRuler::setShowTinyMarks(*bool*) {#setShowTinyMarks}

Shows/hides tiny marks.

> **Note:** Setter function for property [showTinyMarks](kruler.md#showTinyMarks-prop).

*See also* [showTinyMarks](kruler.md#showTinyMarks)()

### void KRuler::setTinyMarkDistance(*int*) {#setTinyMarkDistance}

Sets the distance between tiny marks.

This is mostly used in the English system (inches) with distance of 1.

> **Note:** Setter function for property [tinyMarkDistance](kruler.md#tinyMarkDistance-prop).

*See also* [tinyMarkDistance](kruler.md#tinyMarkDistance)()

### bool KRuler::showBigMarks() const {#showBigMarks}

> **Note:** Getter function for property [showBigMarks](kruler.md#showBigMarks-prop).

*See also* [setShowBigMarks](kruler.md#setShowBigMarks)()

### bool KRuler::showEndLabel() const {#showEndLabel}

> **Note:** Getter function for property [showEndLabel](kruler.md#showEndLabel-prop).

*See also* [setShowEndLabel](kruler.md#setShowEndLabel)()

### bool KRuler::showEndMarks() const {#showEndMarks}

*See also* [setShowEndMarks](kruler.md#setShowEndMarks)()

### bool KRuler::showLittleMarks() const {#showLittleMarks}

> **Note:** Getter function for property [showLittleMarks](kruler.md#showLittleMarks-prop).

*See also* [setShowLittleMarks](kruler.md#setShowLittleMarks)()

### bool KRuler::showMediumMarks() const {#showMediumMarks}

> **Note:** Getter function for property [showMediumMarks](kruler.md#showMediumMarks-prop).

*See also* [setShowMediumMarks](kruler.md#setShowMediumMarks)()

### bool KRuler::showPointer() const {#showPointer}

> **Note:** Getter function for property [showPointer](kruler.md#showPointer-prop).

*See also* [setShowPointer](kruler.md#setShowPointer)()

### bool KRuler::showTinyMarks() const {#showTinyMarks}

> **Note:** Getter function for property [showTinyMarks](kruler.md#showTinyMarks-prop).

*See also* [setShowTinyMarks](kruler.md#setShowTinyMarks)()

### void KRuler::slideDown(int *count* = 1) {#slideDown}

Sets the number of pixels by which the ruler may slide down or right. The number of pixels moved is realive to the previous position. The Method makes sense for updating a ruler, which is working with a scrollbar.

This doesn't affect the position of the ruler pointer. Only the visible part of the ruler is moved.

`count` Number of pixel moving up or left relative to the previous position

### void KRuler::slideUp(int *count* = 1) {#slideUp}

Sets the number of pixels by which the ruler may slide up or left. The number of pixels moved is realive to the previous position. The Method makes sense for updating a ruler, which is working with a scrollbar.

This doesn't affect the position of the ruler pointer. Only the visible part of the ruler is moved.

`count` Number of pixel moving up or left relative to the previous position

### \[slot\] void KRuler::slotEndOffset(*int*) {#slotEndOffset}

### \[slot\] void KRuler::slotNewOffset(*int*) {#slotNewOffset}

Sets the ruler marks to a new position.

The pointer is NOT updated. [QWidget::repaint](https://doc.qt.io/qt-6/qwidget.html#repaint)() is called afterwards.

### \[slot\] void KRuler::slotNewValue(*int*) {#slotNewValue}

Sets the pointer to a new position.

The offset is NOT updated. [QWidget::repaint](https://doc.qt.io/qt-6/qwidget.html#repaint)() is called afterwards.

### int KRuler::tinyMarkDistance() const {#tinyMarkDistance}

Returns the distance between tiny marks.

> **Note:** Getter function for property [tinyMarkDistance](kruler.md#tinyMarkDistance-prop).

*See also* [setTinyMarkDistance](kruler.md#setTinyMarkDistance)()
