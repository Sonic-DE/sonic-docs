---
title: "KSqueezedTextLabel Class"
description: "A replacement for QLabel that squeezes its text into the label."
---

# KSqueezedTextLabel Class

A replacement for [QLabel](https://doc.qt.io/qt-6/qlabel.html) that squeezes its text into the label. [More...](#details)

- **Header:** `#include <KSqueezedTextLabel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QLabel](https://doc.qt.io/qt-6/qlabel.html)

[List of all members, including inherited members](ksqueezedtextlabel-members.md)

## Properties

- [indent : int](#indent-prop)
- [margin : int](#margin-prop)
- [textElideMode : Qt::TextElideMode](#textElideMode-prop)

## Public Functions

- [KSqueezedTextLabel(QWidget \*parent = nullptr)](#KSqueezedTextLabel)
- [KSqueezedTextLabel(const QString &text, QWidget \*parent = nullptr)](#KSqueezedTextLabel-1)
- [QRect contentsRect() const](#contentsRect)
- [QString fullText() const](#fullText)
- [bool isSqueezed() const](#isSqueezed)
- [QSize minimumSizeHint() const](#minimumSizeHint)
- [void setIndent(int indent)](#setIndent)
- [void setMargin(int margin)](#setMargin)
- [void setTextElideMode(Qt::TextElideMode mode)](#setTextElideMode)
- [QSize sizeHint() const](#sizeHint)
- [Qt::TextElideMode textElideMode() const](#textElideMode)

## Public Slots

- [void clear()](#clear)
- [void setText(const QString &text)](#setText)

## Detailed Description {#details}

If the text is too long to fit into the label it is divided into remaining left and right parts which are separated by three dots. Hovering the mouse over the label shows the full text in a tooltip.

Example: http://www.kde.org/documentation/index.html could be squeezed to http://www.kde...ion/index.html

To change the position of the elision mark to the left or right end of the text, use [setTextElideMode](ksqueezedtextlabel.md#setTextElideMode)().

> **Note:** Several functions of [KSqueezedTextLabel](ksqueezedtextlabel.md) (indicated by a warning in their description) reimplement non-virtual functions of [QLabel](https://doc.qt.io/qt-6/qlabel.html). Therefore, you may need to cast the object to [KSqueezedTextLabel](ksqueezedtextlabel.md) in some situations:

```cpp
KSqueezedTextLabel* squeezed = new KSqueezedTextLabel("text", parent);
QLabel* label = squeezed;
label->setText("new text");    // this will not work
squeezed->setText("new text"); // works as expected
static_cast<KSqueezedTextLabel*>(label)->setText("new text");  // works as expected
```

## Property Documentation {#property-documentation}

### indent : int {#indent-prop}

**Access functions:**

- `void` **[setIndent](ksqueezedtextlabel.md#setIndent)**(`int` *indent*)

### margin : int {#margin-prop}

**Access functions:**

- `void` **[setMargin](ksqueezedtextlabel.md#setMargin)**(`int` *margin*)

### textElideMode : Qt::TextElideMode {#textElideMode-prop}

**Access functions:**

- `Qt::TextElideMode` **[textElideMode](ksqueezedtextlabel.md#textElideMode)**() const
- `void` **[setTextElideMode](ksqueezedtextlabel.md#setTextElideMode)**(`Qt::TextElideMode` *mode*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KSqueezedTextLabel::KSqueezedTextLabel(QWidget \**parent* = nullptr) {#KSqueezedTextLabel}

Default constructor.

`parent` the label's parent object

### \[explicit\] KSqueezedTextLabel::KSqueezedTextLabel(const QString &*text*, QWidget \**parent* = nullptr) {#KSqueezedTextLabel-1}

`text` the text that will be displayed

`parent` the label's parent object

### \[slot\] void KSqueezedTextLabel::clear() {#clear}

Clears the text.

Reimplementation of [QLabel::clear](https://doc.qt.io/qt-6/qlabel.html#clear)().

> **Warning:** The corresponding function in the base class is not virtual. Therefore make sure to call this function on objects of type [KSqueezedTextLabel](ksqueezedtextlabel.md), as shown in the example in the class description.

### QRect KSqueezedTextLabel::contentsRect() const {#contentsRect}

Returns the rectangle to squeeze the text into

Reimplementation of [QLabel::contentsRect](https://doc.qt.io/qt-6/qwidget.html#contentsRect)().

> **Warning:** The corresponding function in the base class is not virtual. Therefore make sure to call this function on objects of type [KSqueezedTextLabel](ksqueezedtextlabel.md), as shown in the example in the class description.

### QString KSqueezedTextLabel::fullText() const {#fullText}

Returns the full text set via [setText](ksqueezedtextlabel.md#setText)()

### bool KSqueezedTextLabel::isSqueezed() const {#isSqueezed}

Returns `true` if the text displayed is currently squeezed, i.e. the original text does not fit inside the space available and elide mode is set to a value other than [Qt::ElideNone](https://doc.qt.io/qt-6/qt.html#TextElideMode-enum).

### \[override virtual\] QSize KSqueezedTextLabel::minimumSizeHint() const {#minimumSizeHint}

Reimplements: [QLabel::minimumSizeHint() const](https://doc.qt.io/qt-6/qlabel.html#minimumSizeHint).

Returnss the label's minimum size, where the horizontal component will be -1 to indicate the label's ability to shrink its width by squeezing the text

### void KSqueezedTextLabel::setIndent(int *indent*) {#setIndent}

Sets the indentation of the label.

`indent` the amount of indentation in pixels

Reimplementation of [QLabel::setIndent](https://doc.qt.io/qt-6/qlabel.html#indent-prop)().

> **Warning:** The corresponding function in the base class is not virtual. Therefore make sure to call this function on objects of type [KSqueezedTextLabel](ksqueezedtextlabel.md), as shown in the example in the class description.

> **Note:** Setter function for property [indent](ksqueezedtextlabel.md#indent-prop).

### void KSqueezedTextLabel::setMargin(int *margin*) {#setMargin}

Sets the margin of the label.

`margin` the margin size in pixels

Reimplementation of [QLabel::setMargin](https://doc.qt.io/qt-6/qlabel.html#margin-prop)().

> **Warning:** The corresponding function in the base class is not virtual. Therefore make sure to call this function on objects of type [KSqueezedTextLabel](ksqueezedtextlabel.md), as shown in the example in the class description.

> **Note:** Setter function for property [margin](ksqueezedtextlabel.md#margin-prop).

### \[slot\] void KSqueezedTextLabel::setText(const QString &*text*) {#setText}

Sets the text.

`text` The new text.

Reimplementation of [QLabel::setText](https://doc.qt.io/qt-6/qlabel.html#text-prop)().

> **Warning:** The corresponding function in the base class is not virtual. Therefore make sure to call this function on objects of type [KSqueezedTextLabel](ksqueezedtextlabel.md), as shown in the example in the class description.

### void KSqueezedTextLabel::setTextElideMode(Qt::TextElideMode *mode*) {#setTextElideMode}

Sets the text elide mode.

`mode` The text elide mode.

> **Note:** Setter function for property [textElideMode](ksqueezedtextlabel.md#textElideMode-prop).

*See also* [textElideMode](ksqueezedtextlabel.md#textElideMode)()

### \[override virtual\] QSize KSqueezedTextLabel::sizeHint() const {#sizeHint}

Reimplements: [QLabel::sizeHint() const](https://doc.qt.io/qt-6/qlabel.html#sizeHint).

Returns the label's preferred size, which is wide enough to display the text without squeezing it

### Qt::TextElideMode KSqueezedTextLabel::textElideMode() const {#textElideMode}

Returns the text elide mode

> **Note:** Getter function for property [textElideMode](ksqueezedtextlabel.md#textElideMode-prop).

*See also* [setTextElideMode](ksqueezedtextlabel.md#setTextElideMode)()
