---
title: "Avatar QML Type"
description: "An element that represents a user, either with initials, an icon, or a profile image."
---

# Avatar QML Type

An element that represents a user, either with initials, an icon, or a profile image. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.components
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

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

If not explicitly set, this defaults to generating a color from the name.

### \[read-only\] defaultInitialsColor : color {#defaultInitialsColor-prop}

This property holds the default color of the avatar's initials.

It depends on the avatar's color.

### iconSource : var {#iconSource-prop}

This property holds avatar's icon source.

This icon is displayed when using an icon with Avatar.InitialsMode.UseIcon and Avatar.ImageNode.AlwaysShowInitials enabled.

*See also* [Kirigami.Icon.source](../kirigami/qml-org-kde-kirigami-primitives-icon.md#source-prop)

### imageMode : int {#imageMode-prop}

This property holds how the avatar should be shown.

This property holds whether the button should always show the image; show the image if one is available and show initials when it is not; or always show initials.

Possible values are:

| Constant | Description |
| --- | --- |
| Avatar.ImageMode.AlwaysShowImage | Always try to show the image even if it hasn't loaded yet or is undefined. |
| Avatar.ImageMode.AdaptiveImageOrInitals | Show the image if it is valid or initials if it is not. |
| Avatar.ImageMode.AlwaysShowInitials | Always show initials. |

### initialsColor : color {#initialsColor-prop}

This property holds the color of the avatar's initials.

If not explicitly set, this defaults to [defaultInitialsColor](qml-org-kde-kirigamiaddons-components-avatar.md#defaultInitialsColor-prop).

*See also* [defaultInitialsColor](qml-org-kde-kirigamiaddons-components-avatar.md#defaultInitialsColor-prop)

### initialsMode : int {#initialsMode-prop}

This property holds how the button should represent the user when no user-set image is available.

Possible values are:

| Constant | Description |
| --- | --- |
| Avatar.InitialsMode.UseInitials | Show the user's initials. |
| Avatar.InitialsMode.UseIcon | Show a generic icon. |

### name : string {#name-prop}

This property holds the given name of a user.

The user's name will be used for generating initials and to provide the accessible name for assistive technology.

### source : url {#source-prop}

This property holds the source of the user's profile picture; an image.

*See also* [Image.source](https://doc.qt.io/qt-6/qml-qtquick-image.html#source-prop)

### sourceSize : int {#sourceSize-prop}

This property holds the source size of the user's profile picture.

*See also* [Image.sourceSize](https://doc.qt.io/qt-6/qml-qtquick-image.html#sourceSize-prop)
