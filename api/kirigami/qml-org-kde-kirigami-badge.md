---
title: "Badge QML Type"
description: "A badge with a colored background. This type was introduced in Qt 6.25."
---

# Badge QML Type

A badge with a colored background. This type was introduced in Qt 6.25. [More...](#details)

- Import Statement: import org.kde.kirigami
- Since: Qt 6.25
- Inherits: [Control](https://doc.qt.io/qt-6/qml-qtquick-controls-control.html)

## Detailed Description {#details}

Useful for badging something in an attention-getting way to indicate a non-default status. Supports both text and an icon, both optional.

If the badge has no text or has single-line text, it will have a highly rounded, pill-shaped appearance. Otherwise it will be a rounded rectangle.

```qml
import QtQuick
import org.kde.kirigami as Kirigami

Row {
    spacing: Kirigami.Units.smallSpacing

    // Typical usage:
    Kirigami.Badge {
        text: i18nc("@info badge text", "New!")
        type: Kirigami.Badge.Type.Positive
    }

    // Using as a number badge:
    Kirigami.Badge {
        text: "25"
    }

    // Using as a warning with a re-colored icon:
    Kirigami.Badge {
        icon.name: "edit-bomb-symbolic"
        text: i18nc("@info badge text", "The computer is about to explode")
        type: Kirigami.Badge.Type.Warning
    }

    // Using with a custom color and non-recolored icon:
    Kirigami.Badge {
        icon.name: "applications-science"
        text: i18nc("@info badge text", "Science")
        customColor: Kirigami.Theme.visitedLinkColor
    }
}
```

## Property Documentation {#property-documentation}

### \[since 6.25\] customColor : color {#customColor-prop}

When set, this property overrides the default background color that was chosen by the implementation based on the `type` property.

The implementation should set a legible text color for whatever color is chosen here. For maximum control over the text color, also set `customTextColor`.

This property was introduced in Qt 6.25.

### \[since 6.25\] customTextColor : color {#customTextColor-prop}

When set, this property overrides the default text color that was chosen by the implementation based on the `type` or `customTextColor` properties.

This property was introduced in Qt 6.25.

### icon group {#icon-prop}

### icon.color : color {#icon.color-prop}

### icon.fromControlsIcon : function {#icon.fromControlsIcon-prop}

### icon.height : real {#icon.height-prop}

### icon.name : string {#icon.name-prop}

### icon.source : var {#icon.source-prop}

### icon.width : real {#icon.width-prop}

This grouped property determines the appearance of the optional icon.

If you set the `color` property or pass an icon name ending in "-symbolic", the icon will be masked and re-colored to match the text color.

The default is to display no icon.

| Name | Description |
| --- | --- |
| name | This property holds icon name. The icon will be loaded from the platform theme. If the icon is found in the theme, it will always be used; even if icon.source is also set. If the icon is not found, icon.source will be used instead. |
| source | This property holds the icon source. The icon will be loaded as a regular image. |
| width | This property holds the width of the icon. |
| height | This property holds the height of the icon. |
| color | This property holds the icon tint color. The icon is tinted with the specified color, unless the color is set to "transparent". |
| fromControlsIcon | Bind this icon to all matching properties of a Controls icon group. This function automatically binds all properties to matching properties of a controls icon group, since we cannot just reuse the Controls icon group. To use it, you can assign the result to an [IconPropertiesGroup](qml-org-kde-kirigami-primitives-iconpropertiesgroup.md), like so: ```qml icon: icon.fromControlsIcon(control.icon). ``` |

### \[since 6.25\] text : string {#text-prop}

This property determines the label text in the badge. Long text will wrap, but try to minimize text length anyway. The label is limited to plain text.

The default value is an empty string, i.e. no text.

This property was introduced in Qt 6.25.

### type : enumeration {#type-prop}

This property holds the badge type, which affects the badge's default background color.

One of

- Information
- Positive
- Warning
- Error

The default is Kirigami.Badge.Type.Information, which the implementation should use to produce a soft blue background with the Breeze color scheme.
