---
title: "Kirigami::Platform::PlatformTheme Class"
description: "This class is the base for color management in Kirigami, different platforms can reimplement this class to integrate with system platform colors of a given platform."
---

# Kirigami::Platform::PlatformTheme Class

This class is the base for color management in Kirigami, different platforms can reimplement this class to integrate with system platform colors of a given platform. [More...](#details)

- **Header:** `#include <Kirigami/Platform/PlatformTheme>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KirigamiPlatform)`  
  `target_link_libraries(mytarget PRIVATE KF6::KirigamiPlatform)`
- **In QML:** [Theme](qml-org-kde-kirigami-platform-theme.md)
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kirigami-platform-platformtheme-members.md)

## Public Types

- [enum PlatformTheme::ColorGroup](#ColorGroup-enum)
- [enum PlatformTheme::ColorSet](#ColorSet-enum)

## Properties

- [activeBackgroundColor : QColor](#activeBackgroundColor-prop)
- [activeTextColor : QColor](#activeTextColor-prop)
- [alternateBackgroundColor : QColor](#alternateBackgroundColor-prop)
- [backgroundColor : QColor](#backgroundColor-prop)
- [colorGroup : ColorGroup](#colorGroup-prop)
- [colorSet : ColorSet](#colorSet-prop)
- [\[read-only\] defaultFont : QFont](#defaultFont-prop)
- [disabledTextColor : QColor](#disabledTextColor-prop)
- [\[read-only\] fixedWidthFont : QFont](#fixedWidthFont-prop)
- [focusColor : QColor](#focusColor-prop)
- [\[read-only\] frameContrast : const qreal](#frameContrast-prop)
- [highlightColor : QColor](#highlightColor-prop)
- [highlightedTextColor : QColor](#highlightedTextColor-prop)
- [hoverColor : QColor](#hoverColor-prop)
- [inherit : bool](#inherit-prop)
- [\[read-only\] lightFrameContrast : const qreal](#lightFrameContrast-prop)
- [linkBackgroundColor : QColor](#linkBackgroundColor-prop)
- [linkColor : QColor](#linkColor-prop)
- [negativeBackgroundColor : QColor](#negativeBackgroundColor-prop)
- [negativeTextColor : QColor](#negativeTextColor-prop)
- [neutralBackgroundColor : QColor](#neutralBackgroundColor-prop)
- [neutralTextColor : QColor](#neutralTextColor-prop)
- [\[read-only\] palette : QPalette](#palette-prop)
- [positiveBackgroundColor : QColor](#positiveBackgroundColor-prop)
- [positiveTextColor : QColor](#positiveTextColor-prop)
- [\[read-only\] smallFont : QFont](#smallFont-prop)
- [textColor : QColor](#textColor-prop)
- [\[read-only\] toolsArea : Kirigami::Platform::ToolsArea\* const](#toolsArea-prop)
- [useAlternateBackgroundColor : bool](#useAlternateBackgroundColor-prop)
- [visitedLinkBackgroundColor : QColor](#visitedLinkBackgroundColor-prop)
- [visitedLinkColor : QColor](#visitedLinkColor-prop)

## Public Functions

- [QIcon iconFromTheme(const QString &name, const QColor &customColor = Qt::transparent)](#iconFromTheme)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum PlatformTheme::ColorGroup {#ColorGroup-enum}

| Constant |   |
| --- | --- |
| `Kirigami::Platform::PlatformTheme::Disabled` | `QPalette::Disabled` |
| `Kirigami::Platform::PlatformTheme::Active` | `QPalette::Active` |
| `Kirigami::Platform::PlatformTheme::Inactive` | `QPalette::Inactive` |
| `Kirigami::Platform::PlatformTheme::Normal` | `QPalette::Normal` |

### enum PlatformTheme::ColorSet {#ColorSet-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `Kirigami::Platform::PlatformTheme::View` | `0` | Color set for item views, usually the lightest of all |
| `Kirigami::Platform::PlatformTheme::Window` | `1` | Default Color set for windows and "chrome" areas |
| `Kirigami::Platform::PlatformTheme::Button` | `2` | Color set used by buttons |
| `Kirigami::Platform::PlatformTheme::Selection` | `3` | Color set used by selected areas |
| `Kirigami::Platform::PlatformTheme::Tooltip` | `4` | Color set used by tooltips |
| `Kirigami::Platform::PlatformTheme::Complementary` | `5` | Color set meant to be complementary to Window: usually is a dark theme for light themes |
| `Kirigami::Platform::PlatformTheme::Header` | `6` | Color set to be used by heading areas of applications, such as toolbars |

## Property Documentation {#property-documentation}

### activeBackgroundColor : QColor {#activeBackgroundColor-prop}

Background for areas that are active or requesting attention.

**Access functions:**

- `QColor` **activeBackgroundColor**() const
- `void` **setCustomActiveBackgroundColor**(const `QColor` &*color* = QColor())

**Notifier signal:**

- `void` **[colorsChanged](kirigami-platform-platformtheme.md#textColor-prop)**()

### activeTextColor : QColor {#activeTextColor-prop}

Foreground for areas that are active or requesting attention.

**Access functions:**

- `QColor` **activeTextColor**() const
- `void` **setCustomActiveTextColor**(const `QColor` &*color* = QColor())

**Notifier signal:**

- `void` **[colorsChanged](kirigami-platform-platformtheme.md#textColor-prop)**()

### alternateBackgroundColor : QColor {#alternateBackgroundColor-prop}

The generic background color.

Alternate background; for example, for use in lists.

This color may be the same as BackgroundNormal, especially in sets other than View and Window.

**Access functions:**

- `QColor` **alternateBackgroundColor**() const
- `void` **setCustomAlternateBackgroundColor**(const `QColor` &*color* = QColor())

**Notifier signal:**

- `void` **[colorsChanged](kirigami-platform-platformtheme.md#textColor-prop)**()

### backgroundColor : QColor {#backgroundColor-prop}

The generic background color.

**Access functions:**

- `QColor` **backgroundColor**() const
- `void` **setCustomBackgroundColor**(const `QColor` &*color* = QColor())

**Notifier signal:**

- `void` **[colorsChanged](kirigami-platform-platformtheme.md#textColor-prop)**()

### colorGroup : ColorGroup {#colorGroup-prop}

This enumeration describes the color group used to generate the colors. The enum value is based upon [QPalette::ColorGroup](https://doc.qt.io/qt-6/qpalette.html#ColorGroup-enum) and has the same values. It's redefined here in order to make it work with QML.

**Access functions:**

- `Kirigami::Platform::PlatformTheme::ColorGroup` **colorGroup**() const
- `void` **setColorGroup**(*Kirigami::Platform::PlatformTheme::ColorGroup*)

**Notifier signal:**

- `void` **colorGroupChanged**(`Kirigami::Platform::PlatformTheme::ColorGroup` *colorGroup*)

### colorSet : ColorSet {#colorSet-prop}

This enumeration describes the color set for which a color is being selected.

Color sets define a color "environment", suitable for drawing all parts of a given region. Colors from different sets should not be combined.

**Access functions:**

- `Kirigami::Platform::PlatformTheme::ColorSet` **colorSet**() const
- `void` **setColorSet**(*Kirigami::Platform::PlatformTheme::ColorSet*)

**Notifier signal:**

- `void` **colorSetChanged**(`Kirigami::Platform::PlatformTheme::ColorSet` *colorSet*)

### \[read-only\] defaultFont : QFont {#defaultFont-prop}

The default font.

**Access functions:**

- `QFont` **defaultFont**() const

**Notifier signal:**

- `void` **defaultFontChanged**(const `QFont` &*font*)

### disabledTextColor : QColor {#disabledTextColor-prop}

Foreground color for disabled areas, usually a mid-gray.

> **Note:** Depending on the implementation, the color used for this property may not be based on the disabled palette. For example, for the Plasma implementation, "Inactive Text Color" of the active palette is used.

**Access functions:**

- `QColor` **disabledTextColor**() const
- `void` **setCustomDisabledTextColor**(const `QColor` &*color* = QColor())

**Notifier signal:**

- `void` **[colorsChanged](kirigami-platform-platformtheme.md#textColor-prop)**()

### \[read-only\] fixedWidthFont : QFont {#fixedWidthFont-prop}

Fixed width font.

**Access functions:**

- `QFont` **fixedWidthFont**() const

**Notifier signal:**

- `void` **fixedWidthFontChanged**(const `QFont` &*font*)

### focusColor : QColor {#focusColor-prop}

A decoration color that indicates active focus.

**Access functions:**

- `QColor` **focusColor**() const
- `void` **setCustomFocusColor**(const `QColor` &*color* = QColor())

**Notifier signal:**

- `void` **[colorsChanged](kirigami-platform-platformtheme.md#textColor-prop)**()

### \[read-only\] frameContrast : const qreal {#frameContrast-prop}

Frame contrast value, usually used for separators and outlines Value is between 0.0 and 1.0.

**Access functions:**

- `qreal` **frameContrast**() const

### highlightColor : QColor {#highlightColor-prop}

The background color for selected areas.

**Access functions:**

- `QColor` **highlightColor**() const
- `void` **setCustomHighlightColor**(const `QColor` &*color* = QColor())

**Notifier signal:**

- `void` **[colorsChanged](kirigami-platform-platformtheme.md#textColor-prop)**()

### highlightedTextColor : QColor {#highlightedTextColor-prop}

Color for text that has been highlighted, often is a light color while normal text is dark.

**Access functions:**

- `QColor` **highlightedTextColor**() const
- `void` **setCustomHighlightedTextColor**(const `QColor` &*color* = QColor())

**Notifier signal:**

- `void` **[colorsChanged](kirigami-platform-platformtheme.md#textColor-prop)**()

### hoverColor : QColor {#hoverColor-prop}

A decoration color that indicates mouse hovering.

**Access functions:**

- `QColor` **hoverColor**() const
- `void` **setCustomHoverColor**(const `QColor` &*color* = QColor())

**Notifier signal:**

- `void` **[colorsChanged](kirigami-platform-platformtheme.md#textColor-prop)**()

### inherit : bool {#inherit-prop}

If true, the [colorSet](kirigami-platform-platformtheme.md#colorSet-prop) will be inherited from the colorset of a theme of one of the ancestor items.

default: true

**Access functions:**

- `bool` **inherit**() const
- `void` **setInherit**(`bool` *inherit*)

**Notifier signal:**

- `void` **inheritChanged**(`bool` *inherit*)

### \[read-only\] lightFrameContrast : const qreal {#lightFrameContrast-prop}

Returns half of the [frameContrast](kirigami-platform-platformtheme.md#frameContrast-prop) value; used by Separator.Weight.Light Value is between 0.0 and 1.0.

**Access functions:**

- `qreal` **lightFrameContrast**() const

### linkBackgroundColor : QColor {#linkBackgroundColor-prop}

Background color for links.

**Access functions:**

- `QColor` **linkBackgroundColor**() const
- `void` **setCustomLinkBackgroundColor**(const `QColor` &*color* = QColor())

**Notifier signal:**

- `void` **[colorsChanged](kirigami-platform-platformtheme.md#textColor-prop)**()

### linkColor : QColor {#linkColor-prop}

Color for links.

**Access functions:**

- `QColor` **linkColor**() const
- `void` **setCustomLinkColor**(const `QColor` &*color* = QColor())

**Notifier signal:**

- `void` **[colorsChanged](kirigami-platform-platformtheme.md#textColor-prop)**()

### negativeBackgroundColor : QColor {#negativeBackgroundColor-prop}

Background color for negative areas, such as critical errors and destructive actions.

**Access functions:**

- `QColor` **negativeBackgroundColor**() const
- `void` **setCustomNegativeBackgroundColor**(const `QColor` &*color* = QColor())

**Notifier signal:**

- `void` **[colorsChanged](kirigami-platform-platformtheme.md#textColor-prop)**()

### negativeTextColor : QColor {#negativeTextColor-prop}

Foreground color for negative areas, such as critical error text.

**Access functions:**

- `QColor` **negativeTextColor**() const
- `void` **setCustomNegativeTextColor**(const `QColor` &*color* = QColor())

**Notifier signal:**

- `void` **[colorsChanged](kirigami-platform-platformtheme.md#textColor-prop)**()

### neutralBackgroundColor : QColor {#neutralBackgroundColor-prop}

Background color for neutral areas, such as warnings (but not critical).

**Access functions:**

- `QColor` **neutralBackgroundColor**() const
- `void` **setCustomNeutralBackgroundColor**(const `QColor` &*color* = QColor())

**Notifier signal:**

- `void` **[colorsChanged](kirigami-platform-platformtheme.md#textColor-prop)**()

### neutralTextColor : QColor {#neutralTextColor-prop}

Foreground color for neutral areas, such as warning texts (but not critical).

**Access functions:**

- `QColor` **neutralTextColor**() const
- `void` **setCustomNeutralTextColor**(const `QColor` &*color* = QColor())

**Notifier signal:**

- `void` **[colorsChanged](kirigami-platform-platformtheme.md#textColor-prop)**()

### \[read-only\] palette : QPalette {#palette-prop}

Palette.

**Access functions:**

- `QPalette` **palette**() const

**Notifier signal:**

- `void` **paletteChanged**(const `QPalette` &*pal*)

### positiveBackgroundColor : QColor {#positiveBackgroundColor-prop}

Background color for positive areas, such as success messages and trusted content.

**Access functions:**

- `QColor` **positiveBackgroundColor**() const
- `void` **setCustomPositiveBackgroundColor**(const `QColor` &*color* = QColor())

**Notifier signal:**

- `void` **[colorsChanged](kirigami-platform-platformtheme.md#textColor-prop)**()

### positiveTextColor : QColor {#positiveTextColor-prop}

Success messages, trusted content.

**Access functions:**

- `QColor` **positiveTextColor**() const
- `void` **setCustomPositiveTextColor**(const `QColor` &*color* = QColor())

**Notifier signal:**

- `void` **[colorsChanged](kirigami-platform-platformtheme.md#textColor-prop)**()

### \[read-only\] smallFont : QFont {#smallFont-prop}

Small font.

**Access functions:**

- `QFont` **smallFont**() const

**Notifier signal:**

- `void` **smallFontChanged**(const `QFont` &*font*)

### textColor : QColor {#textColor-prop}

Color for normal foregrounds, usually text, but not limited to it, anything that should be painted with a clear contrast should use this color.

**Access functions:**

- `QColor` **textColor**() const
- `void` **setCustomTextColor**(const `QColor` &*color* = QColor())

**Notifier signal:**

- `void` **colorsChanged**()

### \[read-only\] toolsArea : Kirigami::Platform::ToolsArea\* const {#toolsArea-prop}

How the window's tools area is drawn; filled by the platform plugin.

**Access functions:**

- `Kirigami::Platform::ToolsArea` \***toolsArea**() const

### useAlternateBackgroundColor : bool {#useAlternateBackgroundColor-prop}

Hint for item views to actually make use of the alternate background color feature.

**Access functions:**

- `bool` **useAlternateBackgroundColor**() const
- `void` **setUseAlternateBackgroundColor**(`bool` *alternate*)

**Notifier signal:**

- `void` **useAlternateBackgroundColorChanged**(`bool` *alternate*)

### visitedLinkBackgroundColor : QColor {#visitedLinkBackgroundColor-prop}

Background color for visited links, usually a bit darker than [linkBackgroundColor](kirigami-platform-platformtheme.md#linkBackgroundColor-prop).

**Access functions:**

- `QColor` **visitedLinkBackgroundColor**() const
- `void` **setCustomVisitedLinkBackgroundColor**(const `QColor` &*color* = QColor())

**Notifier signal:**

- `void` **[colorsChanged](kirigami-platform-platformtheme.md#textColor-prop)**()

### visitedLinkColor : QColor {#visitedLinkColor-prop}

Color for visited links, usually a bit darker than [linkColor](kirigami-platform-platformtheme.md#linkColor-prop).

**Access functions:**

- `QColor` **visitedLinkColor**() const
- `void` **setCustomVisitedLinkColor**(const `QColor` &*color* = QColor())

**Notifier signal:**

- `void` **[colorsChanged](kirigami-platform-platformtheme.md#textColor-prop)**()

## Member Function Documentation {#member-function-documentation}

### \[virtual invokable\] QIcon PlatformTheme::iconFromTheme(const QString &*name*, const QColor &*customColor* = Qt::transparent) {#iconFromTheme}

This will be used by desktopicon to fetch icons with KIconLoader.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.
