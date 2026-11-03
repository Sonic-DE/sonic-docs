---
title: "IconTitleSubtitle QML Type"
description: "A simple item containing an icon, title and subtitle."
---

# IconTitleSubtitle QML Type

A simple item containing an icon, title and subtitle. [More...](#details)

- Import Statement: import org.kde.kirigami.delegates
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

This is an extension of [TitleSubtitle](qml-org-kde-kirigami-delegates-titlesubtitle.md) that adds an icon to the side. It is intended as a contentItem for [ItemDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-itemdelegate.html) and related controls.

When using it as a contentItem, make sure to bind the appropriate properties to those of the Control. Prefer binding to the Control's properties over setting the properties directly, as the Control's properties may affect other things like setting accessible names.

This (and [TitleSubtitle](qml-org-kde-kirigami-delegates-titlesubtitle.md)) can be combined with other controls in a layout to create complex content items for controls.

Example usage creating a [CheckDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-checkdelegate.html) with an extra button on the side:

```qml
CheckDelegate {
    id: delegate

    text: "Example"
    icon.name: "document-new"

    contentItem: RowLayout {
        spacing: Kirigami.Units.smallSpacing

        Kirigami.IconTitleSubtitle {
            Layout.fillWidth: true

            icon: icon.fromControlsIcon(delegate.icon)
            title: delegate.text
            selected: delegate.highlighted || delegate.down
            font: delegate.font
        }

        Button {
            icon.name: "document-open"
            text: "Extra Action"
        }
    }
}
```

*See also* [TitleSubtitle](qml-org-kde-kirigami-delegates-titlesubtitle.md), [ItemDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-itemdelegate.html)

## Property Documentation {#property-documentation}

### color : color {#color-prop}

The color to use for the title.

By default this is \`Kirigami.Theme.textColor\` unless \`selected\` is true in which case this is \`Kirigami.Theme.highlightedTextColor\`.

### elide : int {#elide-prop}

The text elision mode used for both the title and subtitle.

### font : font {#font-prop}

The font used to display the title.

### icon group {#icon-prop}

**icon.color : color**

**icon.fromControlsIcon : function**

**icon.height : real**

**icon.name : string**

**icon.source : var**

**icon.width : real**

Grouped property for icon properties.

> **Note:** By default, [IconTitleSubtitle](qml-org-kde-kirigami-delegates-icontitlesubtitle.md) will reserve the space for the icon, even if it is not set. To remove that space, set \`icon.width\` to 0.

| Name | Description |
| --- | --- |
| name | This property holds icon name. The icon will be loaded from the platform theme. If the icon is found in the theme, it will always be used; even if icon.source is also set. If the icon is not found, icon.source will be used instead. |
| source | This property holds the icon source. The icon will be loaded as a regular image. |
| width | This property holds the width of the icon. |
| height | This property holds the height of the icon. |
| color | This property holds the icon tint color. The icon is tinted with the specified color, unless the color is set to "transparent". |
| fromControlsIcon | Bind this icon to all matching properties of a Controls icon group. This function automatically binds all properties to matching properties of a controls icon group, since we cannot just reuse the Controls icon group. To use it, you can assign the result to an [IconPropertiesGroup](qml-org-kde-kirigami-primitives-iconpropertiesgroup.md), like so: ```qml icon: icon.fromControlsIcon(control.icon). ``` |

### reserveSpaceForSubtitle : bool {#reserveSpaceForSubtitle-prop}

Make the implicit height use the subtitle's height even if no subtitle is set.

### selected : bool {#selected-prop}

Should this item be displayed in a selected style?

### subtitle : string {#subtitle-prop}

The subtitle to display.

### subtitleColor : color {#subtitleColor-prop}

The color to use for the subtitle.

By default this is color mixed with the background color.

### subtitleFont : font {#subtitleFont-prop}

The font used to display the subtitle.

### \[since 6.31\] textFormat : alias {#textFormat-prop}

\* The way the text property for the title and subtitle should be displayed. \*

This property was introduced in Qt 6.31.

### \[required\] title : string {#title-prop}

The title to display.

### truncated : bool {#truncated-prop}

Is the title or subtitle truncated?

### wrapMode : int {#wrapMode-prop}

The text wrap mode used for both the title and subtitle.

## Signal Documentation {#signal-documentation}

### linkActivated(string *link*) {#linkActivated-signal}

Emitted when the user clicks on a `link` embedded in the text of the title or subtitle.

> **Note:** The corresponding handler is `onLinkActivated`.

### linkHovered(string *link*) {#linkHovered-signal}

Emitted when the user hovers on a `link` embedded in the text of the title or subtitle.

> **Note:** The corresponding handler is `onLinkHovered`.
