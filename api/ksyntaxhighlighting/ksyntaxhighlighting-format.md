---
title: "KSyntaxHighlighting::Format Class"
description: "Describes the format to be used for a specific text fragment. The actual format used for displaying is merged from the format information in the syntax definition file, and a theme."
---

# KSyntaxHighlighting::Format Class

Describes the format to be used for a specific text fragment. The actual format used for displaying is merged from the format information in the syntax definition file, and a theme. [More...](#details)

- **Header:** `#include <Format>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KSyntaxHighlighting)`  
  `target_link_libraries(mytarget PRIVATE KF6::KSyntaxHighlighting)`

[List of all members, including inherited members](ksyntaxhighlighting-format-members.md)

## Public Functions

- [Format()](#Format)
- [Format(const KSyntaxHighlighting::Format &other)](#Format-1)
- [QColor backgroundColor(const KSyntaxHighlighting::Theme &theme) const](#backgroundColor)
- [bool hasBackgroundColor(const KSyntaxHighlighting::Theme &theme) const](#hasBackgroundColor)
- [bool hasBackgroundColorOverride() const](#hasBackgroundColorOverride)
- [bool hasBoldOverride() const](#hasBoldOverride)
- [bool hasItalicOverride() const](#hasItalicOverride)
- [bool hasSelectedBackgroundColorOverride() const](#hasSelectedBackgroundColorOverride)
- [bool hasSelectedTextColorOverride() const](#hasSelectedTextColorOverride)
- [bool hasStrikeThroughOverride() const](#hasStrikeThroughOverride)
- [bool hasTextColor(const KSyntaxHighlighting::Theme &theme) const](#hasTextColor)
- [bool hasTextColorOverride() const](#hasTextColorOverride)
- [bool hasUnderlineOverride() const](#hasUnderlineOverride)
- [int id() const](#id)
- [bool isBold(const KSyntaxHighlighting::Theme &theme) const](#isBold)
- [bool isDefaultTextStyle(const KSyntaxHighlighting::Theme &theme) const](#isDefaultTextStyle)
- [bool isItalic(const KSyntaxHighlighting::Theme &theme) const](#isItalic)
- [bool isStrikeThrough(const KSyntaxHighlighting::Theme &theme) const](#isStrikeThrough)
- [bool isUnderline(const KSyntaxHighlighting::Theme &theme) const](#isUnderline)
- [bool isValid() const](#isValid)
- [QString name() const](#name)
- [QColor selectedBackgroundColor(const KSyntaxHighlighting::Theme &theme) const](#selectedBackgroundColor)
- [QColor selectedTextColor(const KSyntaxHighlighting::Theme &theme) const](#selectedTextColor)
- [bool spellCheck() const](#spellCheck)
- [QColor textColor(const KSyntaxHighlighting::Theme &theme) const](#textColor)
- [KSyntaxHighlighting::Theme::TextStyle textStyle() const](#textStyle)

## Detailed Description {#details}

*See also* [Theme](ksyntaxhighlighting-theme.md)

## Member Function Documentation {#member-function-documentation}

### Format::Format() {#Format}

Creates an empty/invalid format.

### Format::Format(const KSyntaxHighlighting::Format &*other*) {#Format-1}

### QColor Format::backgroundColor(const KSyntaxHighlighting::Theme &*theme*) const {#backgroundColor}

Returns the background color of the combination of this format and the given theme.

### bool Format::hasBackgroundColor(const KSyntaxHighlighting::Theme &*theme*) const {#hasBackgroundColor}

Returns `true` if the combination of this format and the theme `theme` change the background color compared to the default format.

### bool Format::hasBackgroundColorOverride() const {#hasBackgroundColorOverride}

Returns `true` if the syntax definition file sets a value for the background color attribute and, therefore, overrides the theme and the default formatting style. If the return is `true`, this value is obtained by [backgroundColor](ksyntaxhighlighting-format.md#backgroundColor)().

*See also* [backgroundColor](ksyntaxhighlighting-format.md#backgroundColor)(), [hasBackgroundColor](ksyntaxhighlighting-format.md#hasBackgroundColor)()

### bool Format::hasBoldOverride() const {#hasBoldOverride}

Returns `true` if the syntax definition file sets a value for the bold text attribute and, therefore, overrides the theme and the default formatting style. If the return is `true`, this value is obtained by [isBold](ksyntaxhighlighting-format.md#isBold)().

*See also* [isBold](ksyntaxhighlighting-format.md#isBold)()

### bool Format::hasItalicOverride() const {#hasItalicOverride}

Returns `true` if the syntax definition file sets a value for the italic text attribute and, therefore, overrides the theme and the default formatting style. If the return is `true`, this value is obtained by [isItalic](ksyntaxhighlighting-format.md#isItalic)().

*See also* [isItalic](ksyntaxhighlighting-format.md#isItalic)()

### bool Format::hasSelectedBackgroundColorOverride() const {#hasSelectedBackgroundColorOverride}

Returns `true` if the syntax definition file specifies a value for the selected background color attribute. If the return is `true`, this value is obtained by [selectedBackgroundColor](ksyntaxhighlighting-format.md#selectedBackgroundColor)().

*See also* [selectedBackgroundColor](ksyntaxhighlighting-format.md#selectedBackgroundColor)()

### bool Format::hasSelectedTextColorOverride() const {#hasSelectedTextColorOverride}

Returns `true` if the syntax definition file specifies a value for the selected text color attribute. If the return is `true`, this value is obtained by [selectedTextColor](ksyntaxhighlighting-format.md#selectedTextColor)().

*See also* [selectedTextColor](ksyntaxhighlighting-format.md#selectedTextColor)()

### bool Format::hasStrikeThroughOverride() const {#hasStrikeThroughOverride}

Returns `true` if the syntax definition file specifies a value for the struck through text attribute. If the return is `true`, this value is obtained by [isStrikeThrough](ksyntaxhighlighting-format.md#isStrikeThrough)().

*See also* [isStrikeThrough](ksyntaxhighlighting-format.md#isStrikeThrough)()

### bool Format::hasTextColor(const KSyntaxHighlighting::Theme &*theme*) const {#hasTextColor}

Returns `true` if the combination of this format and the theme `theme` change the foreground color compared to the default format.

### bool Format::hasTextColorOverride() const {#hasTextColorOverride}

Returns `true` if the syntax definition file sets a value for the foreground text color attribute and, therefore, overrides the theme and the default formatting style. If the return is `true`, this value is obtained by [textColor](ksyntaxhighlighting-format.md#textColor)().

*See also* [textColor](ksyntaxhighlighting-format.md#textColor)(), [hasTextColor](ksyntaxhighlighting-format.md#hasTextColor)()

### bool Format::hasUnderlineOverride() const {#hasUnderlineOverride}

Returns `true` if the syntax definition file sets a value for the underlined text attribute and, therefore, overrides the theme and the default formatting style. If the return is `true`, this value is obtained by [isUnderline](ksyntaxhighlighting-format.md#isUnderline)().

*See also* [isUnderline](ksyntaxhighlighting-format.md#isUnderline)()

### int Format::id() const {#id}

Returns a unique identifier of this format.

This is useful for efficient storing of formats in a text line. The identifier is unique per Repository instance, but will change when the repository is reloaded (which also invalidatess the corresponding Definition anyway).

### bool Format::isBold(const KSyntaxHighlighting::Theme &*theme*) const {#isBold}

Returns `true` if the combination of this format and the given theme results in bold text formatting.

### bool Format::isDefaultTextStyle(const KSyntaxHighlighting::Theme &*theme*) const {#isDefaultTextStyle}

Returns `true` if the combination of this format and the theme `theme` do not change the default text format in any way.

This is useful for output formats where changing formatting implies cost, and thus benefit from optimizing the default case of not having any format applied. If you make use of this, make sure to set the default text style to what the corresponding theme sets for [Theme::Normal](ksyntaxhighlighting-theme.md#TextStyle-enum).

### bool Format::isItalic(const KSyntaxHighlighting::Theme &*theme*) const {#isItalic}

Returns `true` if the combination of this format and the given theme results in italic text formatting.

### bool Format::isStrikeThrough(const KSyntaxHighlighting::Theme &*theme*) const {#isStrikeThrough}

Returns `true` if the combination of this format and the given theme results in struck through text.

### bool Format::isUnderline(const KSyntaxHighlighting::Theme &*theme*) const {#isUnderline}

Returns `true` if the combination of this format and the given theme results in underlined text.

### bool Format::isValid() const {#isValid}

Returns `true` if this is a valid format, ie. one that was read from a syntax definition file.

### QString Format::name() const {#name}

The name of this format as used in the syntax definition file.

### QColor Format::selectedBackgroundColor(const KSyntaxHighlighting::Theme &*theme*) const {#selectedBackgroundColor}

Returns the background color of selected text of the combination of this format and the given theme.

### QColor Format::selectedTextColor(const KSyntaxHighlighting::Theme &*theme*) const {#selectedTextColor}

Returns the foreground color for selected text of the combination of this format and the given theme.

### bool Format::spellCheck() const {#spellCheck}

Returns whether characters with this format should be spell checked.

### QColor Format::textColor(const KSyntaxHighlighting::Theme &*theme*) const {#textColor}

Returns the foreground color of the combination of this format and the given theme.

### KSyntaxHighlighting::Theme::TextStyle Format::textStyle() const {#textStyle}

Returns the underlying TextStyle of this Format.

Every [Theme::TextStyle](ksyntaxhighlighting-theme.md#TextStyle-enum) is visually defined by a Theme. A Format uses one of the [Theme::TextStyle](ksyntaxhighlighting-theme.md#TextStyle-enum)%s and on top allows modifications such as setting a different foreground color etc.

*See also* [Theme::TextStyle](ksyntaxhighlighting-theme.md#TextStyle-enum)
