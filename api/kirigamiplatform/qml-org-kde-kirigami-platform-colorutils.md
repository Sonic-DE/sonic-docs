---
title: "ColorUtils QML Type (Singleton)"
description: "Utilities for processing items to obtain colors and information useful for UIs that need to adjust to variable elements."
---

# ColorUtils QML Type (Singleton)

Utilities for processing items to obtain colors and information useful for UIs that need to adjust to variable elements. [More...](#details)

- Import Statement: import org.kde.kirigami.platform

> **Note:** **Note:** This type is a QML singleton. There is only one instance of this type in the QML engine.

## Detailed Description {#details}

## Method Documentation {#method-documentation}

### color adjustColor(color *color*, var *adjustments*) {#adjustColor-method}

Increases or decreases the properties of color by fixed amounts.

`color` The color to adjust.

`adjustments` The adjustments to apply to the color.

```qml
{
    red: null, // Range: -255 to 255
    green: null, // Range: -255 to 255
    blue: null, // Range: -255 to 255
    hue: null, // Range: -360 to 360
    saturation: null, // Range: -255 to 255
    value: null // Range: -255 to 255
    alpha: null, // Range: -255 to 255
}
```

> **Warning:** It is an error to adjust both RGB and HSV properties.

### color alphaBlend(color *foreground*, color *background*) {#alphaBlend-method}

Returns the result of overlaying the foreground color on the background color.

`foreground` The color to overlay on the background.

`background` The color to overlay the foreground on.

```qml
import QtQuick
import org.kde.kirigami as Kirigami

Rectangle {
    color: Kirigami.ColorUtils.alphaBlend(Qt.rgba(0, 0, 0, 0.5), Qt.rgba(1, 1, 1, 1))
}
```

### enumeration brightnessForColor(color *color*) {#brightnessForColor-method}

Returns whether `color` is bright or dark.

```qml
import QtQuick
import org.kde.kirigami as Kirigami

Kirigami.Heading {
    text: {
        if (Kirigami.ColorUtils.brightnessForColor("pink") == Kirigami.ColorUtils.Light) {
            return "The color is light"
        } else {
            return "The color is dark"
        }
    }
}
```

### real chroma(color *color*) {#chroma-method}

Returns the CIELAB chroma of the given color.

CIELAB chroma may give a better quantification of how vibrant a color is compared to HSV saturation.

*See also* [Colorfulness (Wikipedia)](https://en.wikipedia.org/wiki/Colorfulness), [CIELAB Color Space (Wikipedia)](https://en.wikipedia.org/wiki/CIELAB_color_space)

### real grayForColor(color *color*) {#grayForColor-method}

Same Algorithm as [brightnessForColor](qml-org-kde-kirigami-platform-colorutils.md#brightnessForColor-method) but returns a 0 to 1 value for an estimate of the equivalent gray light value (luma). 0 as full black, 1 as full white and 0.5 equivalent to a 50% gray.

### color linearInterpolation(color *one*, color *two*, real *balance*) {#linearInterpolation-method}

Returns a linearly interpolated color between color one and color two.

`one` The color to linearly interpolate from.

`two` The color to linearly interpolate to.

`balance` The balance between the two colors. 0.0 will return the first color, 1.0 will return the second color. Values beyond these bounds are valid, and will result in extrapolation.

```qml
import QtQuick
import org.kde.kirigami as Kirigami

Rectangle {
    color: Kirigami.ColorUtils.linearInterpolation("black", "white", 0.5)
}
```

### color scaleColor(color *color*, var *adjustments*) {#scaleColor-method}

Smoothly scales colors.

`color` The color to adjust.

`adjustments` The adjustments to apply to the color. Each value must be between \`-100.0\` and \`100.0\`. This indicates how far the property should be scaled from its original to the maximum if positive or to the minimum if negative.

```qml
{
    red: null
    green: null
    blue: null
    saturation: null
    value: null
    alpha: null
}
```

> **Warning:** It is an error to scale both RGB and HSV properties.

### color tintWithAlpha(color *targetColor*, color *tintColor*, real *alpha*) {#tintWithAlpha-method}

Tint a color using a separate alpha value.

This does the same as Qt.tint() except that rather than using the tint color's alpha value, it uses a separate value that gets multiplied with the tint color's alpha. This avoids needing to create a new color just to adjust an alpha value.

`targetColor` The color to tint.

`tintColor` The color to tint with.

`alpha` The amount of tinting to apply.

*See also* Qt.tint()
