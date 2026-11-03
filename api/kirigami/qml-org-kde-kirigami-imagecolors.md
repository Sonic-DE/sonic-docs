---
title: "ImageColors QML Type"
description: "Extracts the dominant colors from an element or an image and exports it to a color palette."
---

# ImageColors QML Type

Extracts the dominant colors from an element or an image and exports it to a color palette. [More...](#details)

- Import Statement: import org.kde.kirigami

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### average : color {#average-prop}

The average color of the source image.

### background : color {#background-prop}

A color suitable for rendering a background behind the source image.

On dark items, this will be the color closest to black in the image if it's dark enough, or a dark gray otherwise. On light items, this will be the color closest to white in the image if it's light enough, or a bright gray otherwise.

### closestToBlack : color {#closestToBlack-prop}

The darkest color of the source image.

### closestToWhite : color {#closestToWhite-prop}

The lightest color of the source image.

### dominant : color {#dominant-prop}

The dominant color of the source image.

The dominant color of the image is the color of the largest cluster in the image.

See [K-Means Clustering (Wikipedia)](https://en.wikipedia.org/wiki/K-means_clustering)

### dominantContrast : color {#dominantContrast-prop}

Suggested "contrasting" color to the dominant one. It's the color in the palette nearest to the negative of the dominant

### fallbackAverage : color {#fallbackAverage-prop}

The value to return when average is not available, e.g. when [ImageColors](qml-org-kde-kirigami-imagecolors.md) is still computing it or the source is invalid.

### fallbackBackground : color {#fallbackBackground-prop}

The value to return when background is not available, e.g. when [ImageColors](qml-org-kde-kirigami-imagecolors.md) is still computing it or the source is invalid.

### fallbackDominant : color {#fallbackDominant-prop}

The value to return when dominant is not available, e.g. when [ImageColors](qml-org-kde-kirigami-imagecolors.md) is still computing it or the source is invalid.

### fallbackDominantContrasting : color {#fallbackDominantContrasting-prop}

The value to return when dominantContrasting is not available, e.g. when [ImageColors](qml-org-kde-kirigami-imagecolors.md) is still computing it or the source is invalid.

### fallbackForeground : color {#fallbackForeground-prop}

The value to return when foreground is not available, e.g. when [ImageColors](qml-org-kde-kirigami-imagecolors.md) is still computing it or the source is invalid.

### fallbackHighlight : color {#fallbackHighlight-prop}

The value to return when highlight is not available, e.g. when [ImageColors](qml-org-kde-kirigami-imagecolors.md) is still computing it or the source is invalid.

### fallbackPalette : list\<imageColorsPaletteSwatch\> {#fallbackPalette-prop}

The value to return when palette is not available, e.g. when [ImageColors](qml-org-kde-kirigami-imagecolors.md) is still computing it or the source is invalid.

### fallbackPaletteBrightness : int {#fallbackPaletteBrightness-prop}

The value to return when [paletteBrightness](qml-org-kde-kirigami-imagecolors.md#paletteBrightness-prop) is not available, e.g. when [ImageColors](qml-org-kde-kirigami-imagecolors.md) is still computing it or the source is invalid.

### foreground : color {#foreground-prop}

A color suitable for rendering text and other foreground over the source image.

On dark items, this will be the color closest to white in the image if it's light enough, or a bright gray otherwise. On light items, this will be the color closest to black in the image if it's dark enough, or a dark gray otherwise.

### highlight : color {#highlight-prop}

An accent color extracted from the source image.

The accent color is the color cluster with the highest CIELAB chroma in the source image.

See [Chroma (Wikipedia)](https://en.wikipedia.org/wiki/Colorfulness#Chroma)

### palette : list\<imageColorsPaletteSwatch\> {#palette-prop}

A list of colors and related information about then.

Each list item has the following properties:

- color: The color of the list item.
- ratio: How dominant the color is in the source image.
- contrastingColor: The color from the source image that's closest to the inverse of color.

The list is sorted by `ratio`; the first element is the most dominant color in the source image and the last element is the least dominant color of the image.

> **Note:** K-means clustering is used to extract these colors; see [K-Means Clustering (Wikipedia)](https://en.wikipedia.org/wiki/K-means_clustering).

### paletteBrightness : int {#paletteBrightness-prop}

Information whether the palette is towards a light or dark color scheme, possible values are:

- [ColorUtils](../kirigamiplatform/qml-org-kde-kirigami-platform-colorutils.md).Light
- [ColorUtils](../kirigamiplatform/qml-org-kde-kirigami-platform-colorutils.md).Dark

### source : var {#source-prop}

The source from which colors should be extracted from.

source can be one of the following:

- Item
- QImage
- QIcon
- Icon name

Note that an Item's color palette will only be extracted once unless you call [update](qml-org-kde-kirigami-imagecolors.md#update-method)(), regardless of how the item hanges.

## Method Documentation {#method-documentation}

### void update() {#update-method}

Updates the colors
