---
title: "KCharSelect Class"
description: "Character selection widget."
---

# KCharSelect Class

Character selection widget. [More...](#details)

- **Header:** `#include <KCharSelect>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kcharselect-members.md)

## Public Types

- [enum KCharSelect::Control](#Control-enum)

## Properties

- [allPlanesEnabled : bool](#allPlanesEnabled-prop)
- [currentChar : QChar](#currentChar-prop)
- [currentCodePoint : uint](#currentCodePoint-prop)
- [currentFont : QFont](#currentFont-prop)
- [\[read-only\] displayedChars : QList\<QChar\>](#displayedChars-prop)
- [\[read-only\] displayedCodePoints : QList\<uint\>](#displayedCodePoints-prop)

## Public Functions

- [KCharSelect(QWidget \*parent, const KCharSelect::Controls controls = AllGuiElements)](#KCharSelect)
- [KCharSelect(QWidget \*parent, QObject \*actionParent, const KCharSelect::Controls controls = AllGuiElements)](#KCharSelect-1)
- [bool allPlanesEnabled() const](#allPlanesEnabled)
- [QChar currentChar() const](#currentChar)
- [uint currentCodePoint() const](#currentCodePoint)
- [QFont currentFont() const](#currentFont)
- [QList\<QChar\> displayedChars() const](#displayedChars)
- [QList\<uint\> displayedCodePoints() const](#displayedCodePoints)
- [void setAllPlanesEnabled(bool all)](#setAllPlanesEnabled)

## Public Slots

- [void setCurrentChar(const QChar &c)](#setCurrentChar)
- [void setCurrentCodePoint(uint codePoint)](#setCurrentCodePoint)
- [void setCurrentFont(const QFont &font)](#setCurrentFont)

## Signals

- [void charSelected(const QChar &c)](#charSelected)
- [void codePointSelected(uint codePoint)](#codePointSelected)
- [void currentCharChanged(const QChar &c)](#currentCharChanged)
- [void currentCodePointChanged(uint codePoint)](#currentCodePointChanged)
- [void currentFontChanged(const QFont &font)](#currentFontChanged)
- [void displayedCharsChanged()](#displayedCharsChanged)

## Detailed Description {#details}

This widget allows the user to select a character of a specified font and to browse Unicode information

You can specify the font whose characters should be displayed via [setCurrentFont](kcharselect.md#setCurrentFont)(). Using the Controls argument in the constructor you can create a compact version of [KCharSelect](kcharselect.md) if there is not enough space and if you don't need all features.

[KCharSelect](kcharselect.md) displays one Unicode block at a time and provides categorized access to them. Unicode character names and further details, including cross references, are displayed. Additionally, there is a search to find characters.

By default, [KCharSelect](kcharselect.md) is restricted to Basic Multilingual Plane (BMP) characters that [QChar](https://doc.qt.io/qt-6/qchar.html) supports, i.e. characters with code points that fit into a quint16 (U+0000..U+FFFF). API methods that have a [QChar](https://doc.qt.io/qt-6/qchar.html) argument can only be used for this default mode:

To get the current selected character, use the [currentChar](kcharselect.md#currentChar)() method. You can set the character which should be displayed with [setCurrentChar](kcharselect.md#setCurrentChar)().

If you want the user to select and search characters from all planes, i.e. characters U+0000..U+10FFFF, use [setAllPlanesEnabled](kcharselect.md#setAllPlanesEnabled)(true) and use the `uint` based methods [currentCodePoint](kcharselect.md#currentCodePoint)() and [setCurrentCodePoint](kcharselect.md#setCurrentCodePoint)() instead.

Since [QString](https://doc.qt.io/qt-6/qstring.html) does not allow `uint` code points, you either must use [QString::fromUcs4](https://doc.qt.io/qt-6/qstring.html#fromUcs4)() and QString::ToUcs4() to convert between strings and code points, or manually do the surrogate pair handling using [QChar::requiresSurrogates](https://doc.qt.io/qt-6/qchar.html#requiresSurrogates)() and friends.

## Member Type Documentation {#member-type-documentation}

### enum KCharSelect::Control {#Control-enum}

**flags KCharSelect::Controls**

Flags to set the shown widgets

| Constant | Value | Description |
| --- | --- | --- |
| `KCharSelect::SearchLine` | `0x01` | Shows the search widgets |
| `KCharSelect::FontCombo` | `0x02` | Shows the font combo box |
| `KCharSelect::FontSize` | `0x04` | Shows the font size spin box |
| `KCharSelect::BlockCombos` | `0x08` | Shows the category/block selection combo boxes |
| `KCharSelect::CharacterTable` | `0x10` | Shows the actual table |
| `KCharSelect::DetailBrowser` | `0x20` | Shows the detail browser |
| `KCharSelect::HistoryButtons` | `0x40` | Shows the Back/Forward buttons |
| `KCharSelect::AllGuiElements` | `65535` | Shows everything |

The `Controls` type is a typedef for `QFlags<Control>. `It stores an OR combination of `Control` values.

## Property Documentation {#property-documentation}

### allPlanesEnabled : bool {#allPlanesEnabled-prop}

**Access functions:**

- `bool` **[allPlanesEnabled](kcharselect.md#allPlanesEnabled)**() const
- `void` **[setAllPlanesEnabled](kcharselect.md#setAllPlanesEnabled)**(`bool` *all*)

### currentChar : QChar {#currentChar-prop}

**Access functions:**

- `QChar` **[currentChar](kcharselect.md#currentChar)**() const
- `void` **[setCurrentChar](kcharselect.md#setCurrentChar)**(const `QChar` &*c*)

### currentCodePoint : uint {#currentCodePoint-prop}

**Access functions:**

- `uint` **[currentCodePoint](kcharselect.md#currentCodePoint)**() const
- `void` **[setCurrentCodePoint](kcharselect.md#setCurrentCodePoint)**(`uint` *codePoint*)

**Notifier signal:**

- `void` **[currentCodePointChanged](kcharselect.md#currentCodePointChanged)**(`uint` *codePoint*)

### currentFont : QFont {#currentFont-prop}

**Access functions:**

- `QFont` **[currentFont](kcharselect.md#currentFont)**() const
- `void` **[setCurrentFont](kcharselect.md#setCurrentFont)**(const `QFont` &*font*)

### \[read-only\] displayedChars : QList\<QChar\> {#displayedChars-prop}

**Access functions:**

- `QList`\<`QChar`\> **[displayedChars](kcharselect.md#displayedChars)**() const

### \[read-only\] displayedCodePoints : QList\<uint\> {#displayedCodePoints-prop}

**Access functions:**

- `QList`\<`uint`\> **[displayedCodePoints](kcharselect.md#displayedCodePoints)**() const

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KCharSelect::KCharSelect(QWidget \**parent*, const KCharSelect::Controls *controls* = AllGuiElements) {#KCharSelect}

Constructor. `controls` can be used to show a custom set of widgets.

`parent` the parent widget for this [KCharSelect](kcharselect.md) (see [QWidget](https://doc.qt.io/qt-6/qwidget.html) documentation)

`controls` selects the visible controls on the [KCharSelect](kcharselect.md) widget

### \[explicit\] KCharSelect::KCharSelect(QWidget \**parent*, QObject \**actionParent*, const KCharSelect::Controls *controls* = AllGuiElements) {#KCharSelect-1}

Constructor. `controls` can be used to show a custom set of widgets.

The widget uses the following actions:

- KStandardActions::find() (edit\_find)
- KStandardActions::back() (go\_back)
- KStandardActions::forward() (go\_forward)

If you provide a KActionCollection, this will be populated with the above actions, which you can then manually trigger or place in menus and toolbars.

`parent` the parent widget for this [KCharSelect](kcharselect.md) (see [QWidget](https://doc.qt.io/qt-6/qwidget.html) documentation)

`actionParent` if this is not `null`, [KCharSelect](kcharselect.md) will place its actions into this collection

`controls` selects the visible controls on the [KCharSelect](kcharselect.md) widget

### bool KCharSelect::allPlanesEnabled() const {#allPlanesEnabled}

Returns `true`, if characters from all Unicode code planes can be selected.

> **Note:** Getter function for property [allPlanesEnabled](kcharselect.md#allPlanesEnabled-prop).

*See also* [setAllPlanesEnabled](kcharselect.md#setAllPlanesEnabled)()

### \[signal\] void KCharSelect::charSelected(const QChar &*c*) {#charSelected}

A character is selected to be inserted somewhere.

`c` the selected character

### \[signal\] void KCharSelect::codePointSelected(uint *codePoint*) {#codePointSelected}

A character is selected to be inserted somewhere.

`codePoint` the Unicode code point of the selected character

### QChar KCharSelect::currentChar() const {#currentChar}

Returns the currently selected character. If characters outside the Basic Multilingual Plane (BMP) can be selected, use [currentCodePoint](kcharselect.md#currentCodePoint) instead.

> **Note:** Getter function for property [currentChar](kcharselect.md#currentChar-prop).

*See also* [setCurrentChar](kcharselect.md#setCurrentChar)(), [currentCodePoint](kcharselect.md#currentCodePoint)

### \[signal\] void KCharSelect::currentCharChanged(const QChar &*c*) {#currentCharChanged}

The current character is changed.

`c` the new character

### uint KCharSelect::currentCodePoint() const {#currentCodePoint}

Returns the Unicode code point of the currently selected character.

> **Warning:** If you enabled support for all Unicode planes, you must use [QChar::requiresSurrogates](https://doc.qt.io/qt-6/qchar.html#requiresSurrogates)() to check if the code point requires conversion to a UTF-16 surrogate pair before converting it to [QString](https://doc.qt.io/qt-6/qstring.html). You cannot convert a code point to a [QChar](https://doc.qt.io/qt-6/qchar.html).

> **Note:** Getter function for property [currentCodePoint](kcharselect.md#currentCodePoint-prop).

*See also* [setCurrentCodePoint](kcharselect.md#setCurrentCodePoint)()

### \[signal\] void KCharSelect::currentCodePointChanged(uint *codePoint*) {#currentCodePointChanged}

The current character is changed.

`codePoint` the Unicode code point of the new character

> **Note:** Notifier signal for property [currentCodePoint](kcharselect.md#currentCodePoint-prop).

### QFont KCharSelect::currentFont() const {#currentFont}

Returns the currently displayed font.

> **Note:** Getter function for property [currentFont](kcharselect.md#currentFont-prop).

*See also* [setCurrentFont](kcharselect.md#setCurrentFont)()

### \[signal\] void KCharSelect::currentFontChanged(const QFont &*font*) {#currentFontChanged}

A new font is selected or the font size changed.

`font` the new font

### QList\<QChar\> KCharSelect::displayedChars() const {#displayedChars}

Returns a list of currently displayed characters. If characters outside the Basic Multilingual Plane (BMP) can be selected, use [displayedCodePoints](kcharselect.md#displayedCodePoints) instead.

Warning: this method can be a bit slow

> **Note:** Getter function for property [displayedChars](kcharselect.md#displayedChars-prop).

*See also* [displayedCodePoints](kcharselect.md#displayedCodePoints)

### \[signal\] void KCharSelect::displayedCharsChanged() {#displayedCharsChanged}

The currently displayed characters are changed (search results or block).

### QList\<uint\> KCharSelect::displayedCodePoints() const {#displayedCodePoints}

Returns a list of Unicode code points of the currently displayed characters.

> **Note:** Getter function for property [displayedCodePoints](kcharselect.md#displayedCodePoints-prop).

### void KCharSelect::setAllPlanesEnabled(bool *all*) {#setAllPlanesEnabled}

Sets the allowed Unicode code planes. If `all` is `false`, then only characters from the Basic Multilingual Plane (BMP) can be selected, otherwise characters from all planes are allowed.

For compatibility reasons, the default is `false`.

If you enable support for all planes, you must use the functions handling `uint` code points instead of [QChar](https://doc.qt.io/qt-6/qchar.html) characters.

> **Note:** Setter function for property [allPlanesEnabled](kcharselect.md#allPlanesEnabled-prop).

*See also* [allPlanesEnabled](kcharselect.md#allPlanesEnabled)()

### \[slot\] void KCharSelect::setCurrentChar(const QChar &*c*) {#setCurrentChar}

Highlights the character `c`. If the character is not displayed, the block is changed.

`c` the character to highlight

> **Note:** Setter function for property [currentChar](kcharselect.md#currentChar-prop).

*See also* [currentChar](kcharselect.md#currentChar)()

### \[slot\] void KCharSelect::setCurrentCodePoint(uint *codePoint*) {#setCurrentCodePoint}

Highlights the character with the specified `codePoint`. If the character is outside the Basic Multilingual Plane (BMP), then you must enable support for all planes for this to work.

`codePoint` the Unicode code point of the character to highlight

> **Note:** Setter function for property [currentCodePoint](kcharselect.md#currentCodePoint-prop).

*See also* [currentCodePoint](kcharselect.md#currentCodePoint)(), [allPlanesEnabled](kcharselect.md#allPlanesEnabled)

### \[slot\] void KCharSelect::setCurrentFont(const QFont &*font*) {#setCurrentFont}

Sets the font which is displayed to `font`

`font` the display font for the widget

> **Note:** Setter function for property [currentFont](kcharselect.md#currentFont-prop).

*See also* [currentFont](kcharselect.md#currentFont)()
