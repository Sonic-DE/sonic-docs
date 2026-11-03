---
title: "SvgItem QML Type"
description: "Displays an SVG or an element from an SVG file."
---

# SvgItem QML Type

Displays an SVG or an element from an SVG file. [More...](#details)

- Import Statement: import org.kde.ksvg

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### elementId : string {#elementId-prop}

This property specifies the sub-element of the SVG to be rendered.

If this is empty, the whole SVG document will be rendered.

### elementRect : rect {#elementRect-prop}

This property holds the rectangle of the selected [elementId](qml-org-kde-ksvg-svgitem.md#elementId-prop) relative to the unscaled size of the SVG document.

Note that this property will holds the entire SVG if element id is not selected.

### imagePath : string {#imagePath-prop}

This property specifies the relative path of the Svg in the theme.

Example: "widgets/background"

### naturalSize : size {#naturalSize-prop}

This property holds the SVG's natural, unscaled size.

This is useful if a pixel-perfect rendering of outlines is needed.

### svg : KSvg::Svg {#svg-prop}

This property holds the internal SVG instance.

Usually, specifying just the [imagePath](qml-org-kde-ksvg-svgitem.md#imagePath-prop) is enough. Use this if you have many items taking the same SVG as source, and you want to share the internal SVG object.
