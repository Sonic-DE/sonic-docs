---
title: "ShadowedImage QML Type"
description: "An image with a shadow."
---

# ShadowedImage QML Type

An image with a shadow. [More...](#details)

- Import Statement: import org.kde.kirigami.primitives
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

This item will render a image, with a shadow below it. The rendering is done using distance fields, which provide greatly improved performance. The shadow is rendered outside of the item's bounds, so the item's width and height are the don't include the shadow.

Example usage:

```qml
import org.kde.kirigami

ShadowedImage {
    source: 'qrc:/myKoolGearPicture.png'

    radius: 20

    shadow.size: 20
    shadow.xOffset: 5
    shadow.yOffset: 5

    border.width: 2
    border.color: Kirigami.Theme.textColor

    corners.topLeftRadius: 4
    corners.topRightRadius: 5
    corners.bottomLeftRadius: 2
    corners.bottomRightRadius: 10
}
```

## Property Documentation {#property-documentation}

### asynchronous : bool {#asynchronous-prop}

This property sets whether this image should be loaded asynchronously.

Set this to false if you want the main thread to load the image, which blocks it until the image is loaded. Setting this to true loads the image in a separate thread which is useful when maintaining a responsive user interface is more desirable than having images immediately visible.

*See also* [Image::asynchronous](https://doc.qt.io/qt-6/qml-qtquick-image.html#asynchronous-prop)

### border group {#border-prop}

**border.color : real**

**border.width : real**

This property holds the border's properties of the image.

*See also* [ShadowedRectangle::border](qml-org-kde-kirigami-primitives-shadowedrectangle.md#border-prop)

### color : color {#color-prop}

This property holds the color that will be underneath the image.

This will be visible if the image has transparency.

*See also* [ShadowedRectangle::radius](qml-org-kde-kirigami-primitives-shadowedrectangle.md#radius-prop)

### corners group {#corners-prop}

**corners.bottomLeftRadius : real**

**corners.bottomRightRadius : real**

**corners.topLeftRadius : real**

**corners.topRightRadius : real**

This property holds the corner radius properties of the image.

*See also* [ShadowedRectangle::corners](qml-org-kde-kirigami-primitives-shadowedrectangle.md#corners-prop)

### fillMode : int {#fillMode-prop}

This property defines what happens when the source image has a different size than the item.

*See also* [Image::fillMode](https://doc.qt.io/qt-6/qml-qtquick-image.html#fillMode-prop)

### mipmap : bool {#mipmap-prop}

This property holds whether the image uses mipmap filtering when scaled or transformed.

*See also* [Image::mipmap](https://doc.qt.io/qt-6/qml-qtquick-image.html#mipmap-prop)

### radius : real {#radius-prop}

This property holds the corner radius of the image.

*See also* [ShadowedRectangle::radius](qml-org-kde-kirigami-primitives-shadowedrectangle.md#radius-prop)

### shadow group {#shadow-prop}

**shadow.color : real**

**shadow.size : real**

**shadow.xOffset : real**

**shadow.yOffset : real**

This property holds shadow's properties group.

*See also* [ShadowedRectangle::shadow](qml-org-kde-kirigami-primitives-shadowedrectangle.md#shadow-prop)

### source : var {#source-prop}

This property holds the source of the image.

*See also* [Image::source](https://doc.qt.io/qt-6/qml-qtquick-image.html#source-prop)

### sourceSize : alias {#sourceSize-prop}

This property holds the scaled width and height of the full-frame image.

*See also* [Image::sourceSize](https://doc.qt.io/qt-6/qml-qtquick-image.html#sourceSize-prop)

### \[read-only, since 6.5\] status : alias {#status-prop}

This property holds the status of image loading.

This property was introduced in Qt 6.5.

*See also* [Image::status](https://doc.qt.io/qt-6/qml-qtquick-image.html#status-prop)
