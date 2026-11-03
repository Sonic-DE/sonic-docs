---
title: "Plasma::Theme Class"
description: "Interface to the Plasma theme."
---

# Plasma::Theme Class

Interface to the Plasma theme. [More...](#details)

- **Header:** `#include <Plasma/Theme>`
- **CMake:** `find_package(Plasma REQUIRED)`  
  `target_link_libraries(mytarget PRIVATE Plasma::Plasma)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](plasma-theme-members.md)

## Public Types

- [enum Theme::ColorRole](#ColorRole-enum)

## Properties

- [\[read-only\] backgroundContrast : qreal](#backgroundContrast-prop)
- [\[read-only\] backgroundIntensity : qreal](#backgroundIntensity-prop)
- [\[read-only\] backgroundSaturation : qreal](#backgroundSaturation-prop)
- [\[read-only\] palette : QPalette](#palette-prop)
- [\[read-only\] themeName : QString](#themeName-prop)
- [\[read-only\] useGlobalSettings : bool](#useGlobalSettings-prop)

## Public Functions

- [Theme(QObject \*parent = nullptr)](#Theme)
- [Theme(const QString &themeName, QObject \*parent = nullptr)](#Theme-1)
- [bool adaptiveTransparencyEnabled() const](#adaptiveTransparencyEnabled)
- [qreal backgroundContrast() const](#backgroundContrast)
- [bool backgroundContrastEnabled() const](#backgroundContrastEnabled)
- [qreal backgroundIntensity() const](#backgroundIntensity)
- [qreal backgroundSaturation() const](#backgroundSaturation)
- [bool blurBehindEnabled() const](#blurBehindEnabled)
- [QColor color(Plasma::Theme::ColorRole role, Kirigami::Platform::PlatformTheme::ColorSet group = Kirigami::Platform::PlatformTheme::ColorSet::Window) const](#color)
- [KSharedConfigPtr colorScheme() const](#colorScheme)
- [QString defaultWallpaperTheme() const](#defaultWallpaperTheme) (since 6.6)
- [KPluginMetaData metadata() const](#metadata)
- [QPalette palette() const](#palette)
- [void setThemeName(const QString &themeName)](#setThemeName)
- [void setUseGlobalSettings(bool useGlobal)](#setUseGlobalSettings)
- [QString themeName() const](#themeName)
- [bool useGlobalSettings() const](#useGlobalSettings)

## Static Public Members

- [KSharedConfigPtr globalColorScheme()](#globalColorScheme)
- [QPalette globalPalette()](#globalPalette)

## Detailed Description {#details}

[Plasma::Theme](plasma-theme.md) provides access to a common and standardized set of graphic elements stored in SVG format. This allows artists to create single packages of SVGs that will affect the look and feel of all workspace components.

[Plasma::Theme](plasma-theme.md) can also be used directly to retrieve file system paths to SVGs by name.

## Member Type Documentation {#member-type-documentation}

### enum Theme::ColorRole {#ColorRole-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `Plasma::Theme::TextColor` | `0` | The text color to be used by items resting on the background |
| `Plasma::Theme::BackgroundColor` | `1` | The default background color |
| `Plasma::Theme::HighlightColor` | `2` | The text highlight color to be used by items resting on the background |
| `Plasma::Theme::HoverColor` | `3` | Color for hover effect on view |
| `Plasma::Theme::FocusColor` | `4` | Color for focus effect on view |
| `Plasma::Theme::LinkColor` | `5` | Color for clickable links |
| `Plasma::Theme::VisitedLinkColor` | `6` | Color visited clickable links |
| `Plasma::Theme::HighlightedTextColor` | `7` | Color contrasting with HighlightColor, to be used for instance with |
| `Plasma::Theme::PositiveTextColor` | `8` | Color of foreground objects with a "positive message" connotation (usually green) |
| `Plasma::Theme::NeutralTextColor` | `9` | Color of foreground objects with a "neutral message" connotation (usually yellow) |
| `Plasma::Theme::NegativeTextColor` | `10` | Color of foreground objects with a "negative message" connotation (usually red) |
| `Plasma::Theme::DisabledTextColor (since Qt 5.64)` | `11` | color of disabled text |

## Property Documentation {#property-documentation}

### \[read-only\] backgroundContrast : qreal {#backgroundContrast-prop}

**Access functions:**

- `qreal` **[backgroundContrast](plasma-theme.md#backgroundContrast)**() const

### \[read-only\] backgroundIntensity : qreal {#backgroundIntensity-prop}

**Access functions:**

- `qreal` **[backgroundIntensity](plasma-theme.md#backgroundIntensity)**() const

### \[read-only\] backgroundSaturation : qreal {#backgroundSaturation-prop}

**Access functions:**

- `qreal` **[backgroundSaturation](plasma-theme.md#backgroundSaturation)**() const

### \[read-only\] palette : QPalette {#palette-prop}

**Access functions:**

- `QPalette` **[palette](plasma-theme.md#palette)**() const

### \[read-only\] themeName : QString {#themeName-prop}

**Access functions:**

- `QString` **[themeName](plasma-theme.md#themeName)**() const

### \[read-only\] useGlobalSettings : bool {#useGlobalSettings-prop}

**Access functions:**

- `bool` **[useGlobalSettings](plasma-theme.md#useGlobalSettings)**() const

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Theme::Theme(QObject \**parent* = nullptr) {#Theme}

Default constructor. It will be the global theme configured in plasmarc

`parent` the parent object

### \[explicit\] Theme::Theme(const QString &*themeName*, QObject \**parent* = nullptr) {#Theme-1}

Construct a theme. It will be a custom theme instance of [themeName](plasma-theme.md#themeName).

`themeName` the name of the theme to create

`parent` the parent object

### bool Theme::adaptiveTransparencyEnabled() const {#adaptiveTransparencyEnabled}

This method allows Plasma to enable and disable the adaptive transparency option of the panel, which allows user to decide whether the panel should be always transparent, always opaque or only opaque when a window is maximized. The configuration in the metadata.desktop file of the theme could look like this (for a lighter background):

```cpp
[AdaptiveTransparency]
enabled=true
```

Returns Whether or not to enable the adaptive transparency

### qreal Theme::backgroundContrast() const {#backgroundContrast}

This method allows Plasma to set a background contrast effect for a given theme, improving readability. The value is read from the "contrast" key in the "ContrastEffect" group in the Theme's metadata file.

Returns The contrast provided to the contrasteffect

> **Note:** Getter function for property [backgroundContrast](plasma-theme.md#backgroundContrast-prop).

*See also* [backgroundContrastEnabled](plasma-theme.md#backgroundContrastEnabled)

### bool Theme::backgroundContrastEnabled() const {#backgroundContrastEnabled}

This method allows Plasma to enable and disable the background contrast effect for a given theme, improving readability. The value is read from the "enabled" key in the "ContrastEffect" group in the Theme's metadata file. The configuration in the metadata.desktop file of the theme could look like this (for a lighter background):

```cpp
[ContrastEffect]
enabled=true
contrast=0.45
intensity=0.45
saturation=1.7
```

Returns Whether or not to enable the contrasteffect

### qreal Theme::backgroundIntensity() const {#backgroundIntensity}

This method allows Plasma to set a background contrast effect for a given theme, improving readability. The value is read from the "intensity" key in the "ContrastEffect" group in the Theme's metadata file.

Returns The intensity provided to the contrasteffect

> **Note:** Getter function for property [backgroundIntensity](plasma-theme.md#backgroundIntensity-prop).

*See also* [backgroundContrastEnabled](plasma-theme.md#backgroundContrastEnabled)

### qreal Theme::backgroundSaturation() const {#backgroundSaturation}

This method allows Plasma to set a background contrast effect for a given theme, improving readability. The value is read from the "saturation" key in the "ContrastEffect" group in the Theme's metadata file.

Returns The saturation provided to the contrasteffect

> **Note:** Getter function for property [backgroundSaturation](plasma-theme.md#backgroundSaturation-prop).

*See also* [backgroundContrastEnabled](plasma-theme.md#backgroundContrastEnabled)

### bool Theme::blurBehindEnabled() const {#blurBehindEnabled}

This method allows Plasma to enable and disable the blurring of what is behind the background for a given theme. The value is read from the "enabled" key in the "BlurBehindEffect" group in the Theme's metadata file. Default is @c true.

The configuration in the metadata.desktop file of the theme could look like this:

```cpp
[BlurBehindEffect]
enabled=false
```

Returns Whether or not to enable blurring of what is behind

### QColor Theme::color(Plasma::Theme::ColorRole *role*, Kirigami::Platform::PlatformTheme::ColorSet *group* = Kirigami::Platform::PlatformTheme::ColorSet::Window) const {#color}

Returns the text color to be used by items resting on the background

`role` which role (usage pattern) to get the color for

`group` which group we want a color of

### KSharedConfigPtr Theme::colorScheme() const {#colorScheme}

Returns the color scheme configurationthat goes along this theme.

This can be used with KStatefulBrush and KColorScheme to determine the proper colours to use along with the visual elements in this theme.

### \[since 6.6\] QString Theme::defaultWallpaperTheme() const {#defaultWallpaperTheme}

Returns the default wallpaper theme associated with this theme.

This function was introduced in Qt 6.6.

### \[static\] KSharedConfigPtr Theme::globalColorScheme() {#globalColorScheme}

### \[static\] QPalette Theme::globalPalette() {#globalPalette}

### KPluginMetaData Theme::metadata() const {#metadata}

Returns plugin metadata for this theme, with information such as name, description, author, website etc

### QPalette Theme::palette() const {#palette}

Returns a [QPalette](https://doc.qt.io/qt-6/qpalette.html) with the colors set as defined by the theme.

> **Note:** Getter function for property [palette](plasma-theme.md#palette-prop).

### void Theme::setThemeName(const QString &*themeName*) {#setThemeName}

Sets the current theme being used.

*See also* [themeName](plasma-theme.md#themeName)()

### void Theme::setUseGlobalSettings(bool *useGlobal*) {#setUseGlobalSettings}

Tells the theme whether to follow the global settings or use application specific settings

`useGlobal` pass in true to follow the global settings

*See also* [useGlobalSettings](plasma-theme.md#useGlobalSettings)()

### QString Theme::themeName() const {#themeName}

Returns the name of the theme.

> **Note:** Getter function for property [themeName](plasma-theme.md#themeName-prop).

*See also* [setThemeName](plasma-theme.md#setThemeName)()

### bool Theme::useGlobalSettings() const {#useGlobalSettings}

Returns true if the global settings are followed, false if application specific settings are used.

> **Note:** Getter function for property [useGlobalSettings](plasma-theme.md#useGlobalSettings-prop).

*See also* [setUseGlobalSettings](plasma-theme.md#setUseGlobalSettings)()
