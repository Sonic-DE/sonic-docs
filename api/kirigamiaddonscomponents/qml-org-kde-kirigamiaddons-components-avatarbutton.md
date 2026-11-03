---
title: "AvatarButton QML Type"
description: "An button that represents a user, either with initials, an icon, or a profile image."
---

# AvatarButton QML Type

An button that represents a user, either with initials, an icon, or a profile image. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.components
- Inherits: [AbstractButton](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### asynchronous : bool {#asynchronous-prop}

Load the image asynchronously.

*See also* [Image.asynchronous](https://doc.qt.io/qt-6/qml-qtquick-image.html#asynchronous-prop)

### cache : bool {#cache-prop}

This property sets whether the provided image should be cached.

*See also* [Image.cache](https://doc.qt.io/qt-6/qml-qtquick-image.html#cache-prop)

### \[read-only\] clippedContent : Item {#clippedContent-prop}

This item holds the parent item on the clipped circle.

Implementations may add custom graphics which will be clipped along with the rest of the avatar content.

### color : color {#color-prop}

This property holds the color to use for this avatar.

### \[read-only\] defaultInitialsColor : color {#defaultInitialsColor-prop}

This property holds the default color of the avatar's initials.

### imageMode : int {#imageMode-prop}

This property holds how the avatar should be shown.

*See also* [Avatar.imageMode](qml-org-kde-kirigamiaddons-components-avatar.md#imageMode-prop)

### initialsColor : color {#initialsColor-prop}

This property holds the color of the avatar's initials.

### initialsMode : int {#initialsMode-prop}

This property holds how the button should represent the user when no user-set image is available.

*See also* [Avatar.initialsMode](qml-org-kde-kirigamiaddons-components-avatar.md#initialsMode-prop)

### name : string {#name-prop}

This property holds the given name of a user.

*See also* [Avatar.name](qml-org-kde-kirigamiaddons-components-avatar.md#name-prop)

### source : url {#source-prop}

This property holds avatar's icon source.

*See also* [Avatar.source](qml-org-kde-kirigamiaddons-components-avatar.md#source-prop)

### sourceSize : int {#sourceSize-prop}

This property holds the source size of the user's profile picture.
