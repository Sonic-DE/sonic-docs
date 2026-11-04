---
title: "ShadowedRectangle QML Type"
description: "A rectangle with a shadow behind it."
---

# ShadowedRectangle QML Type

A rectangle with a shadow behind it. [More...](#details)

- Import Statement: import org.kde.kirigami.primitives
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)
- Inherited By: [ShadowedTexture](qml-org-kde-kirigami-primitives-shadowedtexture.md)

## Detailed Description {#details}

This item will render a rectangle, with a shadow below it. The rendering is done using distance fields, which provide greatly improved performance. The shadow is rendered outside of the item's bounds, so the item's width and height are the rectangle's width and height.

## Property Documentation {#property-documentation}

### border group {#border-prop}

### border.color : color {#border.color-prop}

### border.width : real {#border.width-prop}

This property holds the border's grouped property.

width: The border's width in pixels. Default: 0

color: The border's color. Full RGBA colors are supported. Default: Qt.black

Example usage:

```cpp
Kirigami.ShadowedRectangle {
    border.width: 2
    border.color: Kirigami.Theme.textColor
}
```

### color : color {#color-prop}

This property holds the rectangle's color.

Full RGBA colors are supported.

default: Qt.white

### corners group {#corners-prop}

### corners.bottomLeftRadius : real {#corners.bottomLeftRadius-prop}

### corners.bottomRightRadius : real {#corners.bottomRightRadius-prop}

### corners.topLeftRadius : real {#corners.topLeftRadius-prop}

### corners.topRightRadius : real {#corners.topRightRadius-prop}

This property holds the corners grouped property

Note that the values from this group override the radius property for the corner they affect.

Setting any value to -1 indicates that the value should be ignored.

The default value is -1

Example usage:

```cpp
Kirigami.ShadowedRectangle {
    corners.topLeftRadius: 4
    corners.topRightRadius: 5
    corners.bottomLeftRadius: 2
    corners.bottomRightRadius: 10
```

### radius : real {#radius-prop}

This property holds the radii of the rectangle's corners.

This is the amount of rounding to apply to all of the rectangle's corners, in pixels. Each corner can have a different radius.

default: 0

### renderType : enumeration {#renderType-prop}

This property holds the rectangle's render mode.

default: RenderType.Auto

| Constant | Description |
| --- | --- |
| ShadowedRectangle.Auto | Automatically determine the optimal rendering type. This will use the highest rendering quality possible, falling back to lower quality if the hardware doesn't support it. It will use software rendering if the [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) scene graph is set to use software rendering. |
| ShadowedRectangle.HighQuality | Use the highest rendering quality possible, even if the hardware might not be able to handle it normally. |
| ShadowedRectangle.LowQuality | Use the lowest rendering quality, even if the hardware could handle higher quality rendering. This might result in certain effects being omitted, like shadows. |
| ShadowedRectangle.Software | Always use software rendering for this rectangle. Software rendering is intended as a fallback when the [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) scene graph is configured to use software rendering. It will result in a number of missing features, like shadows and multiple corner radii. |

### shadow group {#shadow-prop}

### shadow.color : color {#shadow.color-prop}

### shadow.size : real {#shadow.size-prop}

### shadow.xOffset : real {#shadow.xOffset-prop}

### shadow.yOffset : real {#shadow.yOffset-prop}

This property group holds the shadow's properties.

size: The shadow's approximate size in pixels. Note: The actual shadow size can be less than this value due to falloff. Default: 0px

xOffset: The shadow's offset in pixels on the X axis. Default: 0px

yOffset: The shadow's offset in pixels on the Y axis. Default: 0px

color: The shadow's color. Full RGBA colors are supported. Default: Qt.black

Example usage:

```cpp
Kirigami.ShadowedRectangle {
    shadow.size: 20
    shadow.xOffset: 5
    shadow.yOffset: 5
}
```

### softwareRendering : bool {#softwareRendering-prop}

This property tells whether software rendering is being used.

default: false
