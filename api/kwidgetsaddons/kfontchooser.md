---
title: "KFontChooser Class"
description: "A font selection widget."
---

# KFontChooser Class

A font selection widget. [More...](#details)

- **Header:** `#include <KFontChooser>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS WidgetsAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::WidgetsAddons)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kfontchooser-members.md)

## Public Types

- [enum KFontChooser::DisplayFlag](#DisplayFlag-enum)
- [enum KFontChooser::FontColumn](#FontColumn-enum)
- [enum KFontChooser::FontDiff](#FontDiff-enum)
- [enum KFontChooser::FontListCriteria](#FontListCriteria-enum)

## Properties

- [backgroundColor : QColor](#backgroundColor-prop)
- [color : QColor](#color-prop)
- [font : QFont](#font-prop)
- [sampleText : QString](#sampleText-prop)

## Public Functions

- [KFontChooser(QWidget \*parent = nullptr)](#KFontChooser)
- [KFontChooser(KFontChooser::DisplayFlags flags, QWidget \*parent = nullptr)](#KFontChooser-1)
- [QColor backgroundColor() const](#backgroundColor)
- [QColor color() const](#color)
- [void enableColumn(int column, bool state)](#enableColumn)
- [QFont font() const](#font)
- [KFontChooser::FontDiffFlags fontDiffFlags() const](#fontDiffFlags)
- [QString sampleText() const](#sampleText)
- [void setBackgroundColor(const QColor &col)](#setBackgroundColor)
- [void setColor(const QColor &col)](#setColor)
- [void setFont(const QFont &font, bool onlyFixed = false)](#setFont)
- [void setFontListItems(const QStringList &fontList)](#setFontListItems)
- [void setMinVisibleItems(int visibleItems)](#setMinVisibleItems)
- [void setSampleBoxVisible(bool visible)](#setSampleBoxVisible)
- [void setSampleText(const QString &text)](#setSampleText)

## Signals

- [void fontSelected(const QFont &font)](#fontSelected)

## Static Public Members

- [QStringList createFontList(uint fontListCriteria)](#createFontList)

## Detailed Description {#details}

While [KFontChooser](kfontchooser.md) as an ordinary widget can be embedded in custom dialogs and therefore is very flexible, in most cases it is preferable to use the convenience functions in [QFontDialog](https://doc.qt.io/qt-6/qfontdialog.html).

*See also* [KFontRequester](kfontrequester.md)

## Member Type Documentation {#member-type-documentation}

### enum KFontChooser::DisplayFlag {#DisplayFlag-enum}

**flags KFontChooser::DisplayFlags**

Flags for selecting what is displayed in the widget.

| Constant | Value | Description |
| --- | --- | --- |
| `KFontChooser::NoDisplayFlags` | `0` | No flags set |
| `KFontChooser::FixedFontsOnly` | `1` | Only show monospaced/fixed-width fonts, \*excluding proportional fonts, (the checkbox to toggle showing only monospaced fonts is not shown in this case) |
| `KFontChooser::DisplayFrame` | `2` | = Show a visual frame around the chooser |
| `KFontChooser::ShowDifferences` | `4` | Display the font differences interfaces |

The `DisplayFlags` type is a typedef for `QFlags<DisplayFlag>. `It stores an OR combination of `DisplayFlag` values.

### enum KFontChooser::FontColumn {#FontColumn-enum}

Displayed columns.

| Constant | Value | Description |
| --- | --- | --- |
| `KFontChooser::FamilyList` | `0x01` | Identifies the family (leftmost) list. |
| `KFontChooser::StyleList` | `0x02` | Identifies the style (center) list. |
| `KFontChooser::SizeList` | `0x04` | Identifies the size (rightmost) list. |

### enum KFontChooser::FontDiff {#FontDiff-enum}

**flags KFontChooser::FontDiffFlags**

Flags for selecting which font attributes to change

| Constant | Value | Description |
| --- | --- | --- |
| `KFontChooser::NoFontDiffFlags` | `0` | No flags set |
| `KFontChooser::FontDiffFamily` | `1` | Identifies a requested change in the font family. |
| `KFontChooser::FontDiffStyle` | `2` | Identifies a requested change in the font style. |
| `KFontChooser::FontDiffSize` | `4` | Identifies a requested change in the font size. |
| `KFontChooser::AllFontDiffs` | `FontDiffFamily | FontDiffStyle | FontDiffSize` |   |

The `FontDiffFlags` type is a typedef for `QFlags<FontDiff>. `It stores an OR combination of `FontDiff` values.

### enum KFontChooser::FontListCriteria {#FontListCriteria-enum}

The selection criteria for the font families shown in the dialog.

| Constant | Value | Description |
| --- | --- | --- |
| `KFontChooser::FixedWidthFonts` | `0x01` | If set, only show fixed fixed-width (monospace) fonts. |
| `KFontChooser::ScalableFonts` | `0x02` | If set, only show scalable fonts. Certain configurations allow bitmap fonts to remain unscaled and thus these fonts have limited number of sizes. |
| `KFontChooser::SmoothScalableFonts` | `0x04` | If set, only show smooth scalable fonts. This will return only non-bitmap fonts which are scalable to any size requested. Setting this option means the `ScalableFonts` flag is ignored. |

## Property Documentation {#property-documentation}

### backgroundColor : QColor {#backgroundColor-prop}

**Access functions:**

- `QColor` **[backgroundColor](kfontchooser.md#backgroundColor)**() const
- `void` **[setBackgroundColor](kfontchooser.md#setBackgroundColor)**(const `QColor` &*col*)

### color : QColor {#color-prop}

**Access functions:**

- `QColor` **[color](kfontchooser.md#color)**() const
- `void` **[setColor](kfontchooser.md#setColor)**(const `QColor` &*col*)

### font : QFont {#font-prop}

**Access functions:**

- `QFont` **[font](kfontchooser.md#font)**() const
- `void` **[setFont](kfontchooser.md#setFont)**(const `QFont` &*font*, `bool` *onlyFixed* = false)

**Notifier signal:**

- `void` **[fontSelected](kfontchooser.md#fontSelected)**(const `QFont` &*font*)

### sampleText : QString {#sampleText-prop}

**Access functions:**

- `QString` **[sampleText](kfontchooser.md#sampleText)**() const
- `void` **[setSampleText](kfontchooser.md#setSampleText)**(const `QString` &*text*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KFontChooser::KFontChooser(QWidget \**parent* = nullptr) {#KFontChooser}

Constructs a font picker widget.

`parent` the parent widget

### \[explicit\] KFontChooser::KFontChooser(KFontChooser::DisplayFlags *flags*, QWidget \**parent* = nullptr) {#KFontChooser-1}

Create a font picker widget.

`flags` a combination of OR-ed values from the `KFontChooser::DisplayFlags` enum, the default is `DisplayFonts::NoDisplayFlags`

`parent` the parent widget, if not nullptr the windowing system will use it to position the chooser widget relative to it

### QColor KFontChooser::backgroundColor() const {#backgroundColor}

Returns the background color currently used in the preview area (default: the base color of the active colorgroup)

> **Note:** Getter function for property [backgroundColor](kfontchooser.md#backgroundColor-prop).

*See also* [setBackgroundColor](kfontchooser.md#setBackgroundColor)()

### QColor KFontChooser::color() const {#color}

Returns the color currently used for the font in the preview area (default: the text color of the active color group).

> **Note:** Getter function for property [color](kfontchooser.md#color-prop).

*See also* [setColor](kfontchooser.md#setColor)()

### \[static\] QStringList KFontChooser::createFontList(uint *fontListCriteria*) {#createFontList}

Returns a list of font faimly name strings filtered based on `fontListCriteria`.

`fontListCriteria` specifies the criteria used to select fonts to add to the list, a combination of OR-ed values from [KFontChooser::FontListCriteria](kfontchooser.md#FontListCriteria-enum)

### void KFontChooser::enableColumn(int *column*, bool *state*) {#enableColumn}

Enables or disables a column (family, style, size) in the widget.

Use this function if your application does not need or support all font properties.

`column` specify the column(s) to enable/disable, an OR-ed combination of [KFontChooser::FontColumn](kfontchooser.md#FontColumn-enum) enum values

`state` if `false` the columns are disabled, and vice-versa

### QFont KFontChooser::font() const {#font}

Returns the currently selected font in the chooser.

> **Note:** Getter function for property [font](kfontchooser.md#font-prop).

*See also* [setFont](kfontchooser.md#setFont)()

### KFontChooser::FontDiffFlags KFontChooser::fontDiffFlags() const {#fontDiffFlags}

Returns the bitmask corresponding to the attributes the user wishes to change.

### \[signal\] void KFontChooser::fontSelected(const QFont &*font*) {#fontSelected}

Emitted when the selected font changes.

> **Note:** Notifier signal for property [font](kfontchooser.md#font-prop).

### QString KFontChooser::sampleText() const {#sampleText}

Returns the current text in the sample text input area.

> **Note:** Getter function for property [sampleText](kfontchooser.md#sampleText-prop).

*See also* [setSampleText](kfontchooser.md#setSampleText)()

### void KFontChooser::setBackgroundColor(const QColor &*col*) {#setBackgroundColor}

Sets the background color to use in the preview area.

> **Note:** Setter function for property [backgroundColor](kfontchooser.md#backgroundColor-prop).

*See also* [backgroundColor](kfontchooser.md#backgroundColor)()

### void KFontChooser::setColor(const QColor &*col*) {#setColor}

Sets the color to use for the font in the preview area.

> **Note:** Setter function for property [color](kfontchooser.md#color-prop).

*See also* [color](kfontchooser.md#color)()

### void KFontChooser::setFont(const QFont &*font*, bool *onlyFixed* = false) {#setFont}

Sets the currently selected font in the widget.

`font` the font to select

`onlyFixed` if `true`, the font list will only display fixed-width fonts, otherwise all fonts are displayed. The default is `false`.

> **Note:** Setter function for property [font](kfontchooser.md#font-prop).

*See also* [font](kfontchooser.md#font)()

### void KFontChooser::setFontListItems(const QStringList &*fontList*) {#setFontListItems}

Uses `fontList` to fill the font family list in the widget.

You can create a custom list of fonts using the static [createFontList](kfontchooser.md#createFontList)(uint criteria) to only include fonts that meet certain criteria (e.g. only smooth-scalable fonts).

Note that if `fontList` is empty, the font list in the chooser will show all the available fonts on the system.

*See also* [KFontChooser::createFontList](kfontchooser.md#createFontList)(uint), [KFontChooser::FontListCriteria](kfontchooser.md#FontListCriteria-enum)

### void KFontChooser::setMinVisibleItems(int *visibleItems*) {#setMinVisibleItems}

Sets the minimum number of items that should be visible in the child list widgets; this number will be used to compute and set the minimum heights for those widgets.

### void KFontChooser::setSampleBoxVisible(bool *visible*) {#setSampleBoxVisible}

If `visible` is `true` the preview area will be shown, and vice-versa is it's `false`.

### void KFontChooser::setSampleText(const QString &*text*) {#setSampleText}

Sets the sample text in the preview area; this is useful if you want to use text in your native language.

`text` the new sample text (it will replace the current text)

> **Note:** Setter function for property [sampleText](kfontchooser.md#sampleText-prop).

*See also* [sampleText](kfontchooser.md#sampleText)()
