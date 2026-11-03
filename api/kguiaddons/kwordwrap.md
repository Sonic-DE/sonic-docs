---
title: "KWordWrap Class"
description: "Word-wrap algorithm that takes into account beautifulness."
---

# KWordWrap Class

Word-wrap algorithm that takes into account beautifulness. [More...](#details)

- **Header:** `#include <KWordWrap>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS GuiAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::GuiAddons)`

[List of all members, including inherited members](kwordwrap-members.md)

## Public Types

- [\[anonymous\] enum](#anonymous-kwordwrap-h-52-enum)

## Public Functions

- [QRect boundingRect() const](#boundingRect)
- [void drawText(QPainter \*painter, int x, int y, int flags = Qt::AlignLeft) const](#drawText)
- [QString truncatedString(bool dots = true) const](#truncatedString)
- [QString wrappedString() const](#wrappedString)

## Static Public Members

- [void drawFadeoutText(QPainter \*p, int x, int y, int maxW, const QString &t)](#drawFadeoutText)
- [void drawTruncateText(QPainter \*p, int x, int y, int maxW, const QString &t)](#drawTruncateText)
- [KWordWrap formatText(QFontMetrics &fm, const QRect &r, int flags, const QString &str, int len = -1)](#formatText)

## Detailed Description {#details}

That means:

- not letting a letter alone on the last line,
- breaking at punctuation signs (not only at spaces)
- improved handling of (), \[\] and {}
- improved handling of '/' (e.g. for paths)

Usage: call the static method, [formatText](kwordwrap.md#formatText), with the text to wrap and the constraining rectangle etc., it will return an instance of [KWordWrap](kwordwrap.md) containing internal data, result of the word-wrapping. From that instance you can retrieve the [boundingRect](kwordwrap.md#boundingRect), and invoke drawing.

This design allows to call the word-wrap algorithm only when the text changes and not every time we want to know the bounding rect or draw the text. \*

## Member Type Documentation {#member-type-documentation}

### \[anonymous\] enum {#anonymous-kwordwrap-h-52-enum}

Use this flag in [drawText](kwordwrap.md#drawText)() if you want to fade out the text if it does not fit into the constraining rectangle.

| Constant |   |
| --- | --- |
| `KWordWrap::FadeOut` | `0x10000000` |
| `KWordWrap::Truncate` | `0x20000000` |

## Member Function Documentation {#member-function-documentation}

### QRect KWordWrap::boundingRect() const {#boundingRect}

Returns the bounding rect, calculated by [formatText](kwordwrap.md#formatText). The width is the width of the widest text line, and never wider than the rectangle given to [formatText](kwordwrap.md#formatText). The height is the text block. X and Y are always 0.

### \[static\] void KWordWrap::drawFadeoutText(QPainter \**p*, int *x*, int *y*, int *maxW*, const QString &*t*) {#drawFadeoutText}

Draws the string `t` at the given coordinates, if it does not fit into @p maxW the text will be faded out.

`p` the painter to use. Must have set the pen for the text color and the background for the color to fade out

`x` the horizontal position of the text

`y` the vertical position of the text

`maxW` the maximum width of the text (including the fade-out effect)

`t` the text to draw

### void KWordWrap::drawText(QPainter \**painter*, int *x*, int *y*, int *flags* = Qt::AlignLeft) const {#drawText}

Draw the text that has been previously wrapped, at position x,y. Flags are for alignment, e.g. [Qt::AlignHCenter](https://doc.qt.io/qt-6/qt.html#AlignmentFlag-enum). Default is Qt::AlignAuto.

`painter` the [QPainter](https://doc.qt.io/qt-6/qpainter.html) to use.

`x` the horizontal position of the text

`y` the vertical position of the text

`flags` the ORed text alignment flags from the Qt namespace, ORed with [FadeOut](kwordwrap.md#anonymous-kwordwrap-h-52-enum) if you want the text to fade out if it does not fit (the `painter`'s background must be set accordingly)

### \[static\] void KWordWrap::drawTruncateText(QPainter \**p*, int *x*, int *y*, int *maxW*, const QString &*t*) {#drawTruncateText}

Draws the string `t` at the given coordinates, if it does not fit into `maxW` the text will be truncated.

`p` the painter to use

`x` the horizontal position of the text

`y` the vertical position of the text

`maxW` the maximum width of the text (including the '...')

`t` the text to draw

### \[static\] KWordWrap KWordWrap::formatText(QFontMetrics &*fm*, const QRect &*r*, int *flags*, const QString &*str*, int *len* = -1) {#formatText}

Main method for wrapping text.

`fm` Font metrics, for the chosen font. Better cache it, creating a [QFontMetrics](https://doc.qt.io/qt-6/qfontmetrics.html) is expensive.

`r` Constraining rectangle. Only the width and height matter. With negative height the complete text will be rendered

`flags` currently unused

`str` The text to be wrapped.

`len` Length of text to wrap (default is -1 for all).

Returns a [KWordWrap](kwordwrap.md) instance. The caller is responsible for storing and deleting the result.

### QString KWordWrap::truncatedString(bool *dots* = true) const {#truncatedString}

Returns the original string, truncated to the first line. If `dots` was set, '...' is appended in case the string was truncated. Bug: Note that the '...' come out of the bounding rect.

### QString KWordWrap::wrappedString() const {#wrappedString}

Returns the original string, with '\\n' inserted where the text is broken by the wordwrap algorithm.
