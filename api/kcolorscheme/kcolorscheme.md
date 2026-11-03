---
title: "KColorScheme Class"
description: "A set of methods used to work with colors."
---

# KColorScheme Class

A set of methods used to work with colors. [More...](#details)

- **Header:** `#include <KColorScheme>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ColorScheme)`  
  `target_link_libraries(mytarget PRIVATE KF6::ColorScheme)`

[List of all members, including inherited members](kcolorscheme-members.md)

## Public Types

- [enum KColorScheme::BackgroundRole](#BackgroundRole-enum)
- [enum KColorScheme::ColorSet](#ColorSet-enum)
- [enum KColorScheme::DecorationRole](#DecorationRole-enum)
- [enum KColorScheme::ForegroundRole](#ForegroundRole-enum)
- [enum KColorScheme::ShadeRole](#ShadeRole-enum)

## Public Functions

- [KColorScheme(QPalette::ColorGroup = QPalette::Normal, KColorScheme::ColorSet = View, KSharedConfigPtr = KSharedConfigPtr())](#KColorScheme)
- [~KColorScheme()](#dtor.KColorScheme)
- [QBrush background(KColorScheme::BackgroundRole = NormalBackground) const](#background)
- [QBrush decoration(KColorScheme::DecorationRole) const](#decoration)
- [QBrush foreground(KColorScheme::ForegroundRole = NormalText) const](#foreground)
- [QColor shade(KColorScheme::ShadeRole) const](#shade)
- [bool KColorScheme::operator==(const KColorScheme &other) const](#operator-eq-eq)

## Static Public Members

- [void adjustBackground(QPalette &, KColorScheme::BackgroundRole newRole = NormalBackground, QPalette::ColorRole color = QPalette::Base, KColorScheme::ColorSet set = View, KSharedConfigPtr = KSharedConfigPtr())](#adjustBackground)
- [void adjustForeground(QPalette &, KColorScheme::ForegroundRole newRole = NormalText, QPalette::ColorRole color = QPalette::Text, KColorScheme::ColorSet set = View, KSharedConfigPtr = KSharedConfigPtr())](#adjustForeground)
- [qreal contrastF(const KSharedConfigPtr &config = KSharedConfigPtr())](#contrastF)
- [QPalette createApplicationPalette(const KSharedConfigPtr &config)](#createApplicationPalette)
- [qreal frameContrast(const KSharedConfigPtr &config = KSharedConfigPtr())](#frameContrast) (since 6.20)
- [bool isColorSetSupported(const KSharedConfigPtr &config, KColorScheme::ColorSet set)](#isColorSetSupported)
- [QColor shade(const QColor &, KColorScheme::ShadeRole)](#shade-1)
- [QColor shade(const QColor &, KColorScheme::ShadeRole, qreal contrast, qreal chromaAdjust = 0.0)](#shade-2)

## Detailed Description {#details}

[KColorScheme](kcolorscheme.md) currently provides access to the system color palette that the user has selected (in the future, it is expected to do more). It greatly expands on [QPalette](https://doc.qt.io/qt-6/qpalette.html) by providing five distinct "sets" with several color choices each, covering background, foreground, and decoration colors.

A [KColorScheme](kcolorscheme.md) instance represents colors corresponding to a "set", where a set consists of those colors used to draw a particular type of element, such as a menu, button, view, selected text, or tooltip. Each set has a distinct set of colors, so you should always use the correct set for drawing and never assume that a particular foreground for one set is the same as the foreground for any other set. Individual colors may be quickly referenced by creating an anonymous instance and invoking a lookup member.

> **Note:** The color palettes for the various states of a widget (active, inactive, disabled) may be wildly different. Therefore, it is important to take the state into account. This is why the [KColorScheme](kcolorscheme.md) constructor requires a [QPalette::ColorGroup](https://doc.qt.io/qt-6/qpalette.html#ColorGroup-enum) as an argument.

To facilitate working with potentially-varying states, two convenience API's are provided. These are [KColorScheme::adjustBackground](kcolorscheme.md#adjustBackground) and its sister [KColorScheme::adjustForeground](kcolorscheme.md#adjustForeground), and the helper class [KStatefulBrush](kstatefulbrush.md).

*See also* [KColorScheme::ColorSet](kcolorscheme-index.md), [KColorScheme::ForegroundRole](kcolorscheme-index.md), [KColorScheme::BackgroundRole](kcolorscheme-index.md), [KColorScheme::DecorationRole](kcolorscheme-index.md), [KColorScheme::ShadeRole](kcolorscheme-index.md)

## Member Type Documentation {#member-type-documentation}

### enum KColorScheme::BackgroundRole {#BackgroundRole-enum}

This enumeration describes the background color being selected from the given set.

Background colors are suitable for drawing under text, and should never be used to draw text. In combination with one of the overloads of [KColorScheme::shade](kcolorscheme.md#shade), they may be used to generate colors for drawing frames, bevels, and similar decorations.

| Constant | Value | Description |
| --- | --- | --- |
| `KColorScheme::NormalBackground` | `0` | Normal background. |
| `KColorScheme::AlternateBackground` | `1` | Alternate background; for example, for use in lists. This color may be the same as `BackgroundNormal`, especially in sets other than `View` and `Window`. |
| `KColorScheme::ActiveBackground` | `2` | Third color; for example, items which are new, active, requesting attention, etc. Alerting the user that a certain field must be filled out would be a good usage (although NegativeBackground could be used to the same effect, depending on what you are trying to achieve). Unlike `ActiveText`, this should not be used for mouseover effects. |
| `KColorScheme::LinkBackground` | `3` | Fourth color; corresponds to (unvisited) links. Exactly what this might be used for is somewhat harder to qualify; it might be used for bookmarks, as a 'you can click here' indicator, or to highlight recent content (i.e. in a most-recently-accessed list). |
| `KColorScheme::VisitedBackground` | `4` | Fifth color; corresponds to visited links. This can also be used to indicate "not recent" content, especially when a color is needed to denote content which is "old" or "archival". |
| `KColorScheme::NegativeBackground` | `5` | Sixth color; for example, errors, untrusted content, etc. |
| `KColorScheme::NeutralBackground` | `6` | Seventh color; for example, warnings, secure/encrypted content. |
| `KColorScheme::PositiveBackground` | `7` | Eighth color; for example, success messages, trusted content. |

### enum KColorScheme::ColorSet {#ColorSet-enum}

This enumeration describes the color set for which a color is being selected.

Color sets define a color "environment", suitable for drawing all parts of a given region. Colors from different sets should not be combined.

| Constant | Value | Description |
| --- | --- | --- |
| `KColorScheme::View` | `0` | Views; for example, frames, input fields, etc. If it contains things that can be selected, it is probably a `View`. |
| `KColorScheme::Window` | `1` | Non-editable window elements; for example, menus. If it isn't a `Button`, `View`, or `Tooltip`, it is probably a `Window`. |
| `KColorScheme::Button` | `2` | Buttons and button-like controls. In addition to buttons, "button-like" controls such as non-editable dropdowns, scrollbar sliders, slider handles, etc. should also use this role. |
| `KColorScheme::Selection` | `3` | Selected items in views. Note that unfocused or disabled selections should use the `Window` role. This makes it more obvious to the user that the view containing the selection does not have input focus. |
| `KColorScheme::Tooltip` | `4` | Tooltips. The tooltip set can often be substituted for the view set when editing is not possible, but the Window set is deemed inappropriate. "What's This" help is an excellent example, another might be pop-up notifications (depending on taste). |
| `KColorScheme::Complementary (since KColorScheme 5.19)` | `5` | Complementary areas. Some applications want some areas to have a different color scheme. Usually dark areas over a light theme. For instance the fullscreen UI of a picture viewer, or the logout/lock screen of the plasma workspace ask for a dark color scheme even on light themes. |
| `KColorScheme::Header` | `6` |   |

### enum KColorScheme::DecorationRole {#DecorationRole-enum}

This enumeration describes the decoration color being selected from the given set.

Decoration colors are used to draw decorations (such as frames) for special purposes. Like color shades, they are neither foreground nor background colors. Text should not be painted over a decoration color, and decoration colors should not be used to draw text.

| Constant | Value | Description |
| --- | --- | --- |
| `KColorScheme::FocusColor` | `0` | Color used to draw decorations for items which have input focus. |
| `KColorScheme::HoverColor` | `1` | Color used to draw decorations for items which will be activated by clicking. |

### enum KColorScheme::ForegroundRole {#ForegroundRole-enum}

This enumeration describes the foreground color being selected from the given set.

Foreground colors are suitable for drawing text or glyphs (such as the symbols on window decoration buttons, assuming a suitable background brush is used), and should never be used to draw backgrounds.

For window decorations, the following is suggested, but not set in stone:

- Maximize - `PositiveText`
- Minimize - `NeutralText`
- Close - `NegativeText`
- WhatsThis - `LinkText`
- Sticky - `ActiveText`

| Constant | Value | Description |
| --- | --- | --- |
| `KColorScheme::NormalText` | `0` | Normal foreground. |
| `KColorScheme::InactiveText` | `1` | Second color; for example, comments, items which are old, inactive or disabled. Generally used for things that are meant to be "less important". `InactiveText` is not the same role as NormalText in the inactive state. |
| `KColorScheme::ActiveText` | `2` | Third color; for example items which are new, active, requesting attention, etc. May be used as a hover color for clickable items. |
| `KColorScheme::LinkText` | `3` | Fourth color; use for (unvisited) links. May also be used for other clickable items or content that indicates relationships, items that indicate somewhere the user can visit, etc. |
| `KColorScheme::VisitedText` | `4` | Fifth color; used for (visited) links. As with `LinkText`, may be used for items that have already been "visited" or accessed. May also be used to indicate "historical" (i.e. "old") items or information, especially if `InactiveText` is being used in the same context to express something different. |
| `KColorScheme::NegativeText` | `5` | Sixth color; for example, errors, untrusted content, deletions, etc. |
| `KColorScheme::NeutralText` | `6` | Seventh color; for example, warnings, secure/encrypted content. |
| `KColorScheme::PositiveText` | `7` | Eighth color; for example, additions, success messages, trusted content. |

### enum KColorScheme::ShadeRole {#ShadeRole-enum}

This enumeration describes the color shade being selected from the given set.

Color shades are used to draw "3d" elements, such as frames and bevels. They are neither foreground nor background colors. Text should not be painted over a shade, and shades should not be used to draw text.

| Constant | Value | Description |
| --- | --- | --- |
| `KColorScheme::LightShade` | `0` | The light color is lighter than [QPalette::dark](https://doc.qt.io/qt-6/qpalette.html#dark)() or [QPalette::shadow](https://doc.qt.io/qt-6/qpalette.html#shadow)() and contrasts with the base color. |
| `KColorScheme::MidlightShade` | `1` | The midlight color is in between base() and [QPalette::light](https://doc.qt.io/qt-6/qpalette.html#light)(). |
| `KColorScheme::MidShade` | `2` | The mid color is in between [QPalette::base](https://doc.qt.io/qt-6/qpalette.html#base)() and [QPalette::dark](https://doc.qt.io/qt-6/qpalette.html#dark)(). |
| `KColorScheme::DarkShade` | `3` | The dark color is in between [QPalette::mid](https://doc.qt.io/qt-6/qpalette.html#mid)() and [QPalette::shadow](https://doc.qt.io/qt-6/qpalette.html#shadow)(). |
| `KColorScheme::ShadowShade` | `4` | The shadow color is darker than [QPalette::light](https://doc.qt.io/qt-6/qpalette.html#light)() or [QPalette::midlight](https://doc.qt.io/qt-6/qpalette.html#midlight)() and contrasts the base color. |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KColorScheme::KColorScheme(*QPalette::ColorGroup* = QPalette::Normal, *KColorScheme::ColorSet* = View, *KSharedConfigPtr* = KSharedConfigPtr()) {#KColorScheme}

Construct a palette from given color set and state. Colors are taken from the given [KConfig](../kconfigcore/kconfig.md). If null, the application's color scheme is used (either the system default or one set by [KColorSchemeManager](kcolorschememanager.md)).

> **Note:** [KColorScheme](kcolorscheme.md) provides direct access to the color scheme for users that deal directly with widget states. Unless you are a low-level user or have a legitimate reason to only care about a fixed, limited number of states (e.g. windows that cannot be inactive), consider using a [KStatefulBrush](kstatefulbrush.md) instead.

### \[virtual noexcept\] KColorScheme::~KColorScheme() {#dtor.KColorScheme}

Destructor

### \[static\] void KColorScheme::adjustBackground(*QPalette &*, KColorScheme::BackgroundRole *newRole* = NormalBackground, QPalette::ColorRole *color* = QPalette::Base, KColorScheme::ColorSet *set* = View, *KSharedConfigPtr* = KSharedConfigPtr()) {#adjustBackground}

Adjust a [QPalette](https://doc.qt.io/qt-6/qpalette.html) by replacing the specified [QPalette::ColorRole](https://doc.qt.io/qt-6/qpalette.html#ColorRole-enum) with the requested background color for all states. Using this method is safer than replacing individual states, as it insulates you against changes in [QPalette::ColorGroup](https://doc.qt.io/qt-6/qpalette.html#ColorGroup-enum).

> **Note:** Although it is possible to replace a foreground color using this method, it's bad usability to do so. Just say "no".

### \[static\] void KColorScheme::adjustForeground(*QPalette &*, KColorScheme::ForegroundRole *newRole* = NormalText, QPalette::ColorRole *color* = QPalette::Text, KColorScheme::ColorSet *set* = View, *KSharedConfigPtr* = KSharedConfigPtr()) {#adjustForeground}

Adjust a [QPalette](https://doc.qt.io/qt-6/qpalette.html) by replacing the specified [QPalette::ColorRole](https://doc.qt.io/qt-6/qpalette.html#ColorRole-enum) with the requested foreground color for all states. Using this method is safer than replacing individual states, as it insulates you against changes in [QPalette::ColorGroup](https://doc.qt.io/qt-6/qpalette.html#ColorGroup-enum).

> **Note:** Although it is possible to replace a background color using this method, it's bad usability to do so. Just say "no".

### QBrush KColorScheme::background(*KColorScheme::BackgroundRole* = NormalBackground) const {#background}

Retrieve the requested background brush.

### \[static\] qreal KColorScheme::contrastF(const KSharedConfigPtr &*config* = KSharedConfigPtr()) {#contrastF}

Returns the contrast for borders as a floating point value.

`config` pointer to the config from which to read the contrast setting. If null, the application's color scheme will be used (either the system default or one set by [KColorSchemeManager](kcolorschememanager.md)).

Returns the contrast (between 0.0 for minimum and 1.0 for maximum contrast)

### \[static\] QPalette KColorScheme::createApplicationPalette(const KSharedConfigPtr &*config*) {#createApplicationPalette}

Used to obtain the [QPalette](https://doc.qt.io/qt-6/qpalette.html) that will be used to set the application palette from KDE Platform theme.

`config` [KConfig](../kconfigcore/kconfig.md) from which to load the colors

Returns the [QPalette](https://doc.qt.io/qt-6/qpalette.html)

### QBrush KColorScheme::decoration(*KColorScheme::DecorationRole*) const {#decoration}

Retrieve the requested decoration brush.

### QBrush KColorScheme::foreground(*KColorScheme::ForegroundRole* = NormalText) const {#foreground}

Retrieve the requested foreground brush.

### \[static, since 6.20\] qreal KColorScheme::frameContrast(const KSharedConfigPtr &*config* = KSharedConfigPtr()) {#frameContrast}

Customizable frameContrast value that will override the contrast of frames in using styles (Breeze).

`config` pointer to the config from which to read the contrast setting. If null, the application's color scheme will be used (either the system default or one set by [KColorSchemeManager](kcolorschememanager.md)).

Returns the contrast (between 0.00 and 1.00)

This function was introduced in Qt 6.20.

### \[static\] bool KColorScheme::isColorSetSupported(const KSharedConfigPtr &*config*, KColorScheme::ColorSet *set*) {#isColorSetSupported}

Used to check if the color scheme has a given set.

`config` [KConfig](../kconfigcore/kconfig.md) from which to load the colors

`set` The color set to check for.

Returns whether the color scheme has a given color set

### QColor KColorScheme::shade(*KColorScheme::ShadeRole*) const {#shade}

Retrieve the requested shade color, using [KColorScheme::background](kcolorscheme.md#background)([KColorScheme::NormalBackground](kcolorscheme.md#BackgroundRole-enum)) as the base color and the contrast setting from the [KConfig](../kconfigcore/kconfig.md) used to create this [KColorScheme](kcolorscheme.md) instance.

> **Note:** Shades are chosen such that all shades would contrast with the base color. This means that if base is very dark, the 'dark' shades will be lighter than the base color, with [QPalette::midlight](https://doc.qt.io/qt-6/qpalette.html#midlight)() == [QPalette::shadow](https://doc.qt.io/qt-6/qpalette.html#shadow)(). Conversely, if the base color is very light, the 'light' shades will be darker than the base color, with [QPalette::light](https://doc.qt.io/qt-6/qpalette.html#light)() == [QPalette::mid](https://doc.qt.io/qt-6/qpalette.html#mid)().

### \[static\] QColor KColorScheme::shade(*const QColor &*, *KColorScheme::ShadeRole*) {#shade-1}

Retrieve the requested shade color, using the specified color as the base color and the application's contrast setting.

> **Note:** Shades are chosen such that all shades would contrast with the base color. This means that if base is very dark, the 'dark' shades will be lighter than the base color, with [QPalette::midlight](https://doc.qt.io/qt-6/qpalette.html#midlight)() == [QPalette::shadow](https://doc.qt.io/qt-6/qpalette.html#shadow)(). Conversely, if the base color is very light, the 'light' shades will be darker than the base color, with [QPalette::light](https://doc.qt.io/qt-6/qpalette.html#light)() == [QPalette::mid](https://doc.qt.io/qt-6/qpalette.html#mid)().

### \[static\] QColor KColorScheme::shade(*const QColor &*, *KColorScheme::ShadeRole*, qreal *contrast*, qreal *chromaAdjust* = 0.0) {#shade-2}

Retrieve the requested shade color, using the specified color as the base color and the specified contrast.

`contrast` Amount roughly specifying the contrast by which to adjust the base color, between -1.0 and 1.0 (values between 0.0 and 1.0 correspond to the value from [KColorScheme::contrastF](kcolorscheme.md#contrastF))

`chromaAdjust` (optional) Amount by which to adjust the chroma of the shade (1.0 means no adjustment)

> **Note:** Shades are chosen such that all shades would contrast with the base color. This means that if base is very dark, the 'dark' shades will be lighter than the base color, with [QPalette::midlight](https://doc.qt.io/qt-6/qpalette.html#midlight)() == [QPalette::shadow](https://doc.qt.io/qt-6/qpalette.html#shadow)(). Conversely, if the base color is very light, the 'light' shades will be darker than the base color, with [QPalette::light](https://doc.qt.io/qt-6/qpalette.html#light)() == [QPalette::mid](https://doc.qt.io/qt-6/qpalette.html#mid)().

*See also* [KColorUtils::shade](../kguiaddons/kcolorutils.md#shade)

### bool KColorScheme::operator==(const KColorScheme &*other*) const {#operator-eq-eq}
