---
title: "KIconColors Class"
description: "Sepecifies which colors will be used when recoloring icons as its stylesheet."
---

# KIconColors Class

Sepecifies which colors will be used when recoloring icons as its stylesheet. [More...](#details)

- **Header:** `#include <KIconColors>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS IconThemes)`  
  `target_link_libraries(mytarget PRIVATE KF6::IconThemes)`

[List of all members, including inherited members](kiconcolors-members.md)  
[Deprecated members](kiconcolors-obsolete.md)

## Public Functions

- [KIconColors()](#KIconColors)
- [KIconColors(const QColor &color)](#KIconColors-1)
- [KIconColors(const QPalette &palette)](#KIconColors-2)
- [QColor accent() const](#accent)
- [QColor background() const](#background)
- [QColor highlight() const](#highlight)
- [QColor highlightedText() const](#highlightedText)
- [QColor negativeText() const](#negativeText)
- [QColor neutralText() const](#neutralText)
- [QColor positiveText() const](#positiveText)
- [void setAccent(const QColor &color)](#setAccent)
- [void setBackground(const QColor &color)](#setBackground)
- [void setHighlight(const QColor &color)](#setHighlight)
- [void setHighlightedText(const QColor &color)](#setHighlightedText)
- [void setNegativeText(const QColor &color)](#setNegativeText)
- [void setNeutralText(const QColor &color)](#setNeutralText)
- [void setPositiveText(const QColor &color)](#setPositiveText)
- [void setText(const QColor &color)](#setText)
- [QColor text() const](#text)

## Protected Functions

- [QString stylesheet(KIconLoader::States state) const](#stylesheet)

## Detailed Description {#details}

[KIconLoader](kiconloader.md) supports re-coloring svg icons based on a set of colors. This class will define them.

*See also* [KIconEngine](kiconengine.md), [KDE::icon](kiconloader.md#icon)

## Member Function Documentation {#member-function-documentation}

### KIconColors::KIconColors() {#KIconColors}

Will fill the colors based on the default QPalette() constructor.

### \[explicit\] KIconColors::KIconColors(const QColor &*color*) {#KIconColors-1}

Makes all the color properties be `color`.

### \[explicit\] KIconColors::KIconColors(const QPalette &*palette*) {#KIconColors-2}

Uses `palette` to define text, highlight, [highlightedText](kiconcolors.md#highlightedText), accent and background.

The rest being [positiveText](kiconcolors.md#positiveText), [negativeText](kiconcolors.md#negativeText) and [neutralText](kiconcolors.md#neutralText) are filled from KColorScheme([QPalette::Active](https://doc.qt.io/qt-6/qpalette.html#ColorGroup-enum), KColorScheme::Window);

### QColor KIconColors::accent() const {#accent}

*See also* [setAccent](kiconcolors.md#setAccent)()

### QColor KIconColors::background() const {#background}

*See also* [setBackground](kiconcolors.md#setBackground)()

### QColor KIconColors::highlight() const {#highlight}

*See also* [setHighlight](kiconcolors.md#setHighlight)()

### QColor KIconColors::highlightedText() const {#highlightedText}

*See also* [setHighlightedText](kiconcolors.md#setHighlightedText)()

### QColor KIconColors::negativeText() const {#negativeText}

*See also* [setNegativeText](kiconcolors.md#setNegativeText)()

### QColor KIconColors::neutralText() const {#neutralText}

*See also* [setNeutralText](kiconcolors.md#setNeutralText)()

### QColor KIconColors::positiveText() const {#positiveText}

*See also* [setPositiveText](kiconcolors.md#setPositiveText)()

### void KIconColors::setAccent(const QColor &*color*) {#setAccent}

*See also* [accent](kiconcolors.md#accent)()

### void KIconColors::setBackground(const QColor &*color*) {#setBackground}

*See also* [background](kiconcolors.md#background)()

### void KIconColors::setHighlight(const QColor &*color*) {#setHighlight}

*See also* [highlight](kiconcolors.md#highlight)()

### void KIconColors::setHighlightedText(const QColor &*color*) {#setHighlightedText}

*See also* [highlightedText](kiconcolors.md#highlightedText)()

### void KIconColors::setNegativeText(const QColor &*color*) {#setNegativeText}

*See also* [negativeText](kiconcolors.md#negativeText)()

### void KIconColors::setNeutralText(const QColor &*color*) {#setNeutralText}

*See also* [neutralText](kiconcolors.md#neutralText)()

### void KIconColors::setPositiveText(const QColor &*color*) {#setPositiveText}

*See also* [positiveText](kiconcolors.md#positiveText)()

### void KIconColors::setText(const QColor &*color*) {#setText}

*See also* [text](kiconcolors.md#text)()

### \[protected\] QString KIconColors::stylesheet(KIconLoader::States *state*) const {#stylesheet}

Returns a CSS stylesheet to be used SVG icon files. `state` defines the state we are rendering the stylesheet for

Specifies: `.ColorScheme-Text`, `.ColorScheme-Background`, `.ColorScheme-Highlight`, `.ColorScheme-HighlightedText`, `.ColorScheme-PositiveText`, `.ColorScheme-NeutralText` `.ColorScheme-NegativeText`, `.ColorScheme-Accent`

### QColor KIconColors::text() const {#text}

*See also* [setText](kiconcolors.md#setText)()
