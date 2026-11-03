---
title: "TitleSubtitle QML Type"
description: "A simple item containing a title and subtitle label."
---

# TitleSubtitle QML Type

A simple item containing a title and subtitle label. [More...](#details)

- Import Statement: import org.kde.kirigami.delegates
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

This is mainly intended as a replacement for a list delegate content item, but can be used as a replacement for other content items as well.

When using it as a contentItem, make sure to bind the appropriate properties to those of the Control. Prefer binding to the Control's properties over setting the properties directly, as the Control's properties may affect other things like setting accessible names.

Example usage as contentItem of an [ItemDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-itemdelegate.html):

```qml
ItemDelegate {
    id: delegate

    text: "Example"

    contentItem: Kirigami.TitleSubtitle {
        title: delegate.text
        subtitle: "This is an example."
        font: delegate.font
        selected: delegate.highlighted || delegate.down
    }
}
```

*See also* [IconTitleSubtitle](qml-org-kde-kirigami-delegates-icontitlesubtitle.md), [ItemDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-itemdelegate.html)

## Property Documentation {#property-documentation}

### color : color {#color-prop}

The color to use for the title.

By default this is Kirigami.Theme.textColor unless selected is true in which case this is Kirigami.Theme.highlightedTextColor.

### elide : int {#elide-prop}

The text elision mode used for both the title and subtitle.

### font : font {#font-prop}

The font used to display the title.

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

### \[read-only\] subtitleVisible : bool {#subtitleVisible-prop}

Is the subtitle visible?

### textFormat : int {#textFormat-prop}

The way the text property for the title and subtitle should be displayed.

### \[required\] title : string {#title-prop}

The title to display.

### \[read-only\] truncated : bool {#truncated-prop}

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
