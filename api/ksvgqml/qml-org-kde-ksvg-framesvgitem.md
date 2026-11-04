---
title: "FrameSvgItem QML Type"
description: "An SVG Item with borders."
---

# FrameSvgItem QML Type

An SVG Item with borders. [More...](#details)

- Import Statement: import org.kde.ksvg

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### enabledBorders : flags\<KSvg::FrameSvg::EnabledBorder\> {#enabledBorders-prop}

This property specifies which borders are shown.

*See also* [KSvg::FrameSvg::EnabledBorder](../ksvg/ksvg-framesvg.md#EnabledBorder-enum)

### fixedMargins group {#fixedMargins-prop}

### fixedMargins.bottom : qreal {#fixedMargins.bottom-prop}

### fixedMargins.horizontal : qreal {#fixedMargins.horizontal-prop}

### fixedMargins.left : qreal {#fixedMargins.left-prop}

### fixedMargins.right : qreal {#fixedMargins.right-prop}

### fixedMargins.top : qreal {#fixedMargins.top-prop}

### fixedMargins.vertical : qreal {#fixedMargins.vertical-prop}

This property holds the fixed margins of the frame which are used regardless of any margins being enabled or not.

### fromCurrentImageSet : bool {#fromCurrentImageSet-prop}

This property holds whether the current SVG is present in the currently-used theme and no fallback is involved.

### imagePath : string {#imagePath-prop}

This property specifies the relative path of the SVG in the theme.

Example: "widgets/background"

### inset group {#inset-prop}

### inset.bottom : qreal {#inset.bottom-prop}

### inset.horizontal : qreal {#inset.horizontal-prop}

### inset.left : qreal {#inset.left-prop}

### inset.right : qreal {#inset.right-prop}

### inset.top : qreal {#inset.top-prop}

### inset.vertical : qreal {#inset.vertical-prop}

This property holds the frame's inset.

### margins group {#margins-prop}

### margins.bottom : qreal {#margins.bottom-prop}

### margins.horizontal : qreal {#margins.horizontal-prop}

### margins.left : qreal {#margins.left-prop}

### margins.right : qreal {#margins.right-prop}

### margins.top : qreal {#margins.top-prop}

### margins.vertical : qreal {#margins.vertical-prop}

This property holds the frame's margins.

### mask : QRegion {#mask-prop}

This property holds the mask that contains the SVG's painted areas.

### minimumDrawingHeight : int {#minimumDrawingHeight-prop}

This property holds the minimum height required to correctly draw this SVG.

### minimumDrawingWidth : int {#minimumDrawingWidth-prop}

This property holds the minimum width required to correctly draw this SVG.

### prefix : variant {#prefix-prop}

This property holds the prefix for the SVG. prefix for the 9-piece SVG, like "pushed" or "normal" for a button. see https://techbase.kde.org/Development/Tutorials/Plasma5/ThemeDetails for a list of paths and prefixes It can also be an array of strings, specifying a fallback chain in case the first element isn't found in the theme, eg \["toolbutton-normal", "normal"\] so it's easy to keep backwards compatibility with old themes (Note: fallback chain is supported only

### status : enum\<KSvg::Svg::Status\> {#status-prop}

This property specifies the SVG's status.

Depending on the specified status, the SVG will use different colors: \* Normal: text's color is textColor, and background color is backgroundColor. \* Selected: text color becomes highlightedText and background color is changed to highlightColor.

*See also* Kirigami::PlatformTheme, [KSvg::Svg::status](../ksvg/ksvg-svg.md#status)

### usedPrefix : string {#usedPrefix-prop}

This property holds the actual prefix that was used, if a fallback chain array was set as "prefix".

## Method Documentation {#method-documentation}

### bool hasElement(string *elementName*) {#hasElement-method}

Returns whether the SVG includes the given element.

This is a convenience function that forwards to hasElement().

*See also* KSvg::Svg::hasElement()

### bool hasElementPrefix(string *prefix*) {#hasElementPrefix-method}

Returns whether the svg has the necessary elements with the given prefix to draw a frame.

`prefix` the given prefix we want to check if drawable
