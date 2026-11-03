---
title: "KFontUtils Namespace"
description: "Provides utility functions for font data."
---

# KFontUtils Namespace

Provides utility functions for font data. [More...](#details)

- Header: KFontUtils
- CMake: find\_package(KF6 REQUIRED COMPONENTS GuiAddons) target\_link\_libraries(mytarget PRIVATE KF6::GuiAddons)

## Detailed Description {#details}

## Type Documentation {#type-documentation}

### enum KFontUtils::AdaptFontSizeOption {#AdaptFontSizeOption-enum}

**flags KFontUtils::AdaptFontSizeOptions**

Modifiers for the [adaptFontSize](kfontutils.md#adaptFontSize) function

| Constant | Value | Description |
| --- | --- | --- |
| `KFontUtils::NoFlags` | `0x01` | No modifier |
| `KFontUtils::DoNotAllowWordWrap` | `0x02` | Do not use word wrapping |

The `AdaptFontSizeOptions` type is a typedef for `QFlags<AdaptFontSizeOption>. `It stores an OR combination of `AdaptFontSizeOption` values.

## Function Documentation {#function-documentation}

### qreal KFontUtils::adaptFontSize(QPainter &*painter*, const QString &*text*, const QSizeF &*availableSize*, qreal *maxFontSize* = 28.0, qreal *minFontSize* = 1.0, KFontUtils::AdaptFontSizeOptions *flags* = NoFlags) {#adaptFontSize}

Convenience function for adaptFontSize that accepts a [QSizeF](https://doc.qt.io/qt-6/qsizef.html) instead two qreals

### qreal KFontUtils::adaptFontSize(QPainter &*painter*, const QString &*text*, qreal *width*, qreal *height*, qreal *maxFontSize* = 28.0, qreal *minFontSize* = 1.0, KFontUtils::AdaptFontSizeOptions *flags* = NoFlags) {#adaptFontSize-1}

Helper function that calculates the biggest font size (in points) used drawing a centered text using word wrapping.

`painter` The painter where the text will be painted. The font set in the painter is used for the calculation. Note the painter font size is modified by this call

`text` The text you want to draw

`width` The available width for drawing

`height` The available height for drawing

`maxFontSize` The maximum font size (in points) to consider

`minFontSize` The minimum font size (in points) to consider

`flags` The modifiers for how the text is painted

Returns the calculated biggest font size (in points) that draws the text in the given dimensions. Can return smaller than minFontSize, that means the text doesn't fit in the given rectangle. Can return -1 on error
