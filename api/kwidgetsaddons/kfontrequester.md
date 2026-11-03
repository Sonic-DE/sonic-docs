---
title: "KFontRequester Class"
description: "This class provides a widget with a lineedit and a button, which invokes a font dialog (KFontChooserDialog)."
---

# KFontRequester Class

This class provides a widget with a lineedit and a button, which invokes a font dialog ([KFontChooserDialog](kfontchooserdialog.md)). [More...](#details)

- **Header:** `#include <KFontRequester>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kfontrequester-members.md)

## Properties

- [font : QFont](#font-prop)
- [sampleText : QString](#sampleText-prop)
- [title : QString](#title-prop)

## Public Functions

- [KFontRequester(QWidget \*parent = nullptr, bool onlyFixed = false)](#KFontRequester)
- [QPushButton \*button() const](#button)
- [QFont font() const](#font)
- [bool isFixedOnly() const](#isFixedOnly)
- [QLabel \*label() const](#label)
- [QString sampleText() const](#sampleText)
- [void setFont(const QFont &font, bool onlyFixed = false)](#setFont)
- [void setSampleText(const QString &text)](#setSampleText)
- [void setTitle(const QString &title)](#setTitle)
- [QString title() const](#title)

## Signals

- [void fontSelected(const QFont &font)](#fontSelected)

## Detailed Description {#details}

The lineedit provides a preview of the selected font. The preview text can be customized. You can also have the font dialog show only the fixed fonts.

## Property Documentation {#property-documentation}

### font : QFont {#font-prop}

**Access functions:**

- `QFont` **[font](kfontrequester.md#font)**() const
- virtual `void` **[setFont](kfontrequester.md#setFont)**(const `QFont` &*font*, `bool` *onlyFixed* = false)

**Notifier signal:**

- `void` **[fontSelected](kfontrequester.md#fontSelected)**(const `QFont` &*font*)

### sampleText : QString {#sampleText-prop}

**Access functions:**

- `QString` **[sampleText](kfontrequester.md#sampleText)**() const
- virtual `void` **[setSampleText](kfontrequester.md#setSampleText)**(const `QString` &*text*)

### title : QString {#title-prop}

**Access functions:**

- `QString` **[title](kfontrequester.md#title)**() const
- virtual `void` **[setTitle](kfontrequester.md#setTitle)**(const `QString` &*title*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KFontRequester::KFontRequester(QWidget \**parent* = nullptr, bool *onlyFixed* = false) {#KFontRequester}

Constructs a font requester widget.

`parent` The parent widget.

`onlyFixed` Only display fonts which have fixed-width character sizes.

### QPushButton \*KFontRequester::button() const {#button}

Returns pointer to the pushbutton in the widget.

### QFont KFontRequester::font() const {#font}

Returns the currently selected font in the requester.

> **Note:** Getter function for property [font](kfontrequester.md#font-prop).

*See also* [setFont](kfontrequester.md#setFont)()

### \[signal\] void KFontRequester::fontSelected(const QFont &*font*) {#fontSelected}

Emitted when a new `font` has been selected in the underlying dialog

> **Note:** Notifier signal for property [font](kfontrequester.md#font-prop).

### bool KFontRequester::isFixedOnly() const {#isFixedOnly}

Returns `true` if only fixed fonts are displayed.

### QLabel \*KFontRequester::label() const {#label}

Returns pointer to the label used for preview.

### QString KFontRequester::sampleText() const {#sampleText}

Returns the current text in the sample text input area.

> **Note:** Getter function for property [sampleText](kfontrequester.md#sampleText-prop).

*See also* [setSampleText](kfontrequester.md#setSampleText)()

### \[virtual\] void KFontRequester::setFont(const QFont &*font*, bool *onlyFixed* = false) {#setFont}

Sets the currently selected font in the requester.

`font` The font to select.

`onlyFixed` Display only fixed-width fonts in the font dialog if `true`, or vice-versa.

> **Note:** Setter function for property [font](kfontrequester.md#font-prop).

*See also* [font](kfontrequester.md#font)()

### \[virtual\] void KFontRequester::setSampleText(const QString &*text*) {#setSampleText}

Sets the sample text.

Normally you should not change this text, but it can be better to do this if the default text is too large for the edit area when using the default font of your application. Default text is current font name and size. Setting the text to QString() will restore the default.

`text` The new sample text. The current will be removed.

> **Note:** Setter function for property [sampleText](kfontrequester.md#sampleText-prop).

*See also* [sampleText](kfontrequester.md#sampleText)()

### \[virtual\] void KFontRequester::setTitle(const QString &*title*) {#setTitle}

Set the title for the widget that will be used in the tooltip and what's this text.

`title` The title to be set.

> **Note:** Setter function for property [title](kfontrequester.md#title-prop).

*See also* [title](kfontrequester.md#title)()

### QString KFontRequester::title() const {#title}

Returns the current title of the widget.

> **Note:** Getter function for property [title](kfontrequester.md#title-prop).

*See also* [setTitle](kfontrequester.md#setTitle)()
