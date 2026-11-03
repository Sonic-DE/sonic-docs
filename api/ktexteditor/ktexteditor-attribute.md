---
title: "KTextEditor::Attribute Class"
description: "A class which provides customized text decorations."
---

# KTextEditor::Attribute Class

A class which provides customized text decorations. [More...](#details)

- **Header:** `#include <KTextEditor/Attribute>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS TextEditor)`  
  `target_link_libraries(mytarget PRIVATE KF6::TextEditor)`
- **Inherits:** [QSharedData](https://doc.qt.io/qt-6/qshareddata.html) and

[List of all members, including inherited members](ktexteditor-attribute-members.md)

## Public Types

- [enum Attribute::ActivationType](#ActivationType-enum)
- [Attribute::Ptr](#Ptr-typedef)

## Public Functions

- [Attribute()](#Attribute)
- [Attribute(const QString &name, KSyntaxHighlighting::Theme::TextStyle style)](#Attribute-1)
- [bool backgroundFillWhitespace() const](#backgroundFillWhitespace)
- [void clear()](#clear)
- [KSyntaxHighlighting::Theme::TextStyle defaultStyle() const](#defaultStyle)
- [Attribute::Ptr dynamicAttribute(KTextEditor::Attribute::ActivationType type) const](#dynamicAttribute)
- [bool fontBold() const](#fontBold)
- [bool hasAnyProperty() const](#hasAnyProperty)
- [QString name() const](#name)
- [QBrush outline() const](#outline)
- [QBrush selectedBackground() const](#selectedBackground)
- [QBrush selectedForeground() const](#selectedForeground)
- [void setBackgroundFillWhitespace(bool fillWhitespace)](#setBackgroundFillWhitespace)
- [void setDefaultStyle(KSyntaxHighlighting::Theme::TextStyle style)](#setDefaultStyle)
- [void setDynamicAttribute(KTextEditor::Attribute::ActivationType type, Attribute::Ptr attribute)](#setDynamicAttribute)
- [void setFontBold(bool bold = true)](#setFontBold)
- [void setName(const QString &name)](#setName)
- [void setOutline(const QBrush &brush)](#setOutline)
- [void setSelectedBackground(const QBrush &brush)](#setSelectedBackground)
- [void setSelectedForeground(const QBrush &foreground)](#setSelectedForeground)
- [void setSkipSpellChecking(bool skipspellchecking)](#setSkipSpellChecking)
- [bool skipSpellChecking() const](#skipSpellChecking)
- [KTextEditor::Attribute &Attribute::operator+=(const KTextEditor::Attribute &a)](#operator-2b-eq)
- [KTextEditor::Attribute &Attribute::operator=(const KTextEditor::Attribute &a)](#operator-eq)

## Detailed Description {#details}

The Attribute class extends QTextCharFormat, the class which Qt uses internally to provide formatting information to characters in a text document.

In addition to its inherited properties, it provides support for:

- several customized text formatting properties
- dynamic highlighting of associated ranges of text
- binding of actions with associated ranges of text (note: not currently implemented)

Implementations are not required to support all properties. In particular, several properties are not supported for dynamic highlighting (notably: font() and [fontBold](ktexteditor-attribute.md#fontBold)()).

Unfortunately, as QTextFormat's setProperty() is not virtual, changes that are made to this attribute cannot automatically be redrawn. Once you have finished changing properties, you should call changed() to force redrawing of affected ranges of text.

*See also* [MovingRange](ktexteditor-movingrange.md)

## Member Type Documentation {#member-type-documentation}

### enum Attribute::ActivationType {#ActivationType-enum}

Several automatic activation mechanisms exist for associated attributes. Using this you can conveniently have your ranges highlighted when either the mouse or cursor enter the range.

| Constant | Value | Description |
| --- | --- | --- |
| `KTextEditor::Attribute::ActivateMouseIn` | `0` | Activate attribute on mouse in |
| `KTextEditor::Attribute::ActivateCaretIn` | `1` | Activate attribute on caret in |

### Attribute::Ptr {#Ptr-typedef}

Shared data pointer for Attribute

## Member Function Documentation {#member-function-documentation}

### Attribute::Attribute() {#Attribute}

Default constructor.

The resulting Attribute has no properties set to begin with.

### Attribute::Attribute(const QString &*name*, KSyntaxHighlighting::Theme::TextStyle *style*) {#Attribute-1}

Construct attribute with given name & default style properties.

`name` is the attribute name

`style` is the attribute default style

### bool Attribute::backgroundFillWhitespace() const {#backgroundFillWhitespace}

Determine whether background color is drawn over whitespace. Defaults to true if not set.

Returns whether the background color should be drawn over whitespace

*See also* [setBackgroundFillWhitespace](ktexteditor-attribute.md#setBackgroundFillWhitespace)()

### void Attribute::clear() {#clear}

Clear all set properties.

### KSyntaxHighlighting::Theme::TextStyle Attribute::defaultStyle() const {#defaultStyle}

Default style of this attribute

Returns default style

*See also* [setDefaultStyle](ktexteditor-attribute.md#setDefaultStyle)()

### Attribute::Ptr Attribute::dynamicAttribute(KTextEditor::Attribute::ActivationType *type*) const {#dynamicAttribute}

Returns the attribute to use when the event referred to by `type` occurs.

`type` the activation type for which to return the Attribute.

*See also* [setDynamicAttribute](ktexteditor-attribute.md#setDynamicAttribute)()

### bool Attribute::fontBold() const {#fontBold}

Find out if the font weight is set to QFont::Bold.

Returns `true` if the font weight is exactly QFont::Bold, otherwise `false`

*See also* [setFontBold](ktexteditor-attribute.md#setFontBold)(), QTextCharFormat::fontWeight()

### bool Attribute::hasAnyProperty() const {#hasAnyProperty}

Determine if any properties are set.

Returns *true* if any properties are set, otherwise *false*

### QString Attribute::name() const {#name}

Returns the attribute name.

*See also* [setName](ktexteditor-attribute.md#setName)()

### QBrush Attribute::outline() const {#outline}

Get the brush used to draw an outline around text, if any.

Returns brush to be used to draw an outline, or [Qt::NoBrush](https://doc.qt.io/qt-6/qt.html#BrushStyle-enum) if no outline is set.

*See also* [setOutline](ktexteditor-attribute.md#setOutline)()

### QBrush Attribute::selectedBackground() const {#selectedBackground}

Get the brush used to draw the background of selected text, if any.

Returns brush to be used to draw the background of selected text, or [Qt::NoBrush](https://doc.qt.io/qt-6/qt.html#BrushStyle-enum) if not set

*See also* [setSelectedBackground](ktexteditor-attribute.md#setSelectedBackground)()

### QBrush Attribute::selectedForeground() const {#selectedForeground}

Get the brush used to draw text when it is selected, if any.

Returns brush to be used to draw selected text, or [Qt::NoBrush](https://doc.qt.io/qt-6/qt.html#BrushStyle-enum) if not set

*See also* [setSelectedForeground](ktexteditor-attribute.md#setSelectedForeground)()

### void Attribute::setBackgroundFillWhitespace(bool *fillWhitespace*) {#setBackgroundFillWhitespace}

Set whether background color is drawn over whitespace. Defaults to true if not set.

Use clearProperty(BackgroundFillWhitespace) to clear.

`fillWhitespace` specifies whether the background should be drawn over whitespace.

*See also* [backgroundFillWhitespace](ktexteditor-attribute.md#backgroundFillWhitespace)()

### void Attribute::setDefaultStyle(KSyntaxHighlighting::Theme::TextStyle *style*) {#setDefaultStyle}

Sets the default text style of this attribute.

`style` is the new default text style

*See also* [defaultStyle](ktexteditor-attribute.md#defaultStyle)()

### void Attribute::setDynamicAttribute(KTextEditor::Attribute::ActivationType *type*, Attribute::Ptr *attribute*) {#setDynamicAttribute}

Sets the attribute to use when the event referred to by type occurs.

> **Note:** Nested dynamic attributes are ignored.

`type` is the activation type to set the attribute for

`attribute` is the attribute to assign. As attribute is refcounted, ownership is not an issue.

*See also* [dynamicAttribute](ktexteditor-attribute.md#dynamicAttribute)()

### void Attribute::setFontBold(bool *bold* = true) {#setFontBold}

Set the font weight to QFont::Bold. If bold is false, the weight will be set to 0 (normal).

`bold` specifies whether the font weight should be bold or not.

*See also* [fontBold](ktexteditor-attribute.md#fontBold)(), QTextCharFormat::setFontWeight()

### void Attribute::setName(const QString &*name*) {#setName}

Sets the attribute name

`name` is the new attribute name

*See also* [name](ktexteditor-attribute.md#name)()

### void Attribute::setOutline(const QBrush &*brush*) {#setOutline}

Set a brush to be used to draw an outline around text.

Use clearProperty(Outline) to clear.

`brush` is the brush to be used to draw an outline.

*See also* [outline](ktexteditor-attribute.md#outline)()

### void Attribute::setSelectedBackground(const QBrush &*brush*) {#setSelectedBackground}

Set a brush to be used to draw the background of selected text, if any.

Use clearProperty(SelectedBackground) to clear.

`brush` is the brush to be used to draw the background of selected text

*See also* [selectedBackground](ktexteditor-attribute.md#selectedBackground)()

### void Attribute::setSelectedForeground(const QBrush &*foreground*) {#setSelectedForeground}

Set a brush to be used to draw selected text.

`foreground` is the brush to be used to draw selected text.

*See also* [selectedForeground](ktexteditor-attribute.md#selectedForeground)(), clearProperty()

### void Attribute::setSkipSpellChecking(bool *skipspellchecking*) {#setSkipSpellChecking}

Set if we should spellchecking be skipped?

`skipspellchecking` if true then spellchecking should be skipped

*See also* [skipSpellChecking](ktexteditor-attribute.md#skipSpellChecking)()

### bool Attribute::skipSpellChecking() const {#skipSpellChecking}

Should spellchecking be skipped?

Returns true if spellchecking should be skipped

*See also* [setSkipSpellChecking](ktexteditor-attribute.md#setSkipSpellChecking)()

### KTextEditor::Attribute &Attribute::operator+=(const KTextEditor::Attribute &*a*) {#operator-2b-eq}

Addition assignment operator. Use this to merge another Attribute with this Attribute. Where both attributes have a particular property set, the property in `a` will be used.

`a` is the attribute to merge into this attribute.

### KTextEditor::Attribute &Attribute::operator=(const KTextEditor::Attribute &*a*) {#operator-eq}

Replacement assignment operator. Use this to overwrite this Attribute with another Attribute.

`a` is the attribute to assign to this attribute.
