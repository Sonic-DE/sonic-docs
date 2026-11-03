---
title: "Theme QML Type"
description: "This class is the base for color management in Kirigami, different platforms can reimplement this class to integrate with system platform colors of a given platform."
---

# Theme QML Type

This class is the base for color management in Kirigami, different platforms can reimplement this class to integrate with system platform colors of a given platform. [More...](#details)

- Import Statement: import org.kde.kirigami.platform
- In C++: [PlatformTheme](kirigami-platform-platformtheme.md)

## Detailed Description {#details}

## Attached Property Documentation {#attached-property-documentation}

### Theme.activeBackgroundColor : color {#activeBackgroundColor-attached-prop}

Background for areas that are active or requesting attention.

### Theme.activeTextColor : color {#activeTextColor-attached-prop}

Foreground for areas that are active or requesting attention.

### Theme.alternateBackgroundColor : color {#alternateBackgroundColor-attached-prop}

The generic background color.

Alternate background; for example, for use in lists.

This color may be the same as BackgroundNormal, especially in sets other than View and Window.

### Theme.backgroundColor : color {#backgroundColor-attached-prop}

The generic background color.

### Theme.colorGroup : enumeration {#colorGroup-attached-prop}

This enumeration describes the color group used to generate the colors. The enum value is based upon [QPalette::ColorGroup](https://doc.qt.io/qt-6/qpalette.html#ColorGroup-enum) and has the same values. It's redefined here in order to make it work with QML.

### Theme.colorSet : enumeration {#colorSet-attached-prop}

This enumeration describes the color set for which a color is being selected.

Color sets define a color "environment", suitable for drawing all parts of a given region. Colors from different sets should not be combined.

### \[read-only\] Theme.defaultFont : font {#defaultFont-attached-prop}

The default font.

### Theme.disabledTextColor : color {#disabledTextColor-attached-prop}

Foreground color for disabled areas, usually a mid-gray.

> **Note:** Depending on the implementation, the color used for this property may not be based on the disabled palette. For example, for the Plasma implementation, "Inactive Text Color" of the active palette is used.

### \[read-only\] Theme.fixedWidthFont : font {#fixedWidthFont-attached-prop}

Fixed width font.

### Theme.focusColor : color {#focusColor-attached-prop}

A decoration color that indicates active focus.

### \[read-only\] Theme.frameContrast : real {#frameContrast-attached-prop}

Frame contrast value, usually used for separators and outlines Value is between 0.0 and 1.0.

### Theme.highlightColor : color {#highlightColor-attached-prop}

The background color for selected areas.

### Theme.highlightedTextColor : color {#highlightedTextColor-attached-prop}

Color for text that has been highlighted, often is a light color while normal text is dark.

### Theme.hoverColor : color {#hoverColor-attached-prop}

A decoration color that indicates mouse hovering.

### Theme.inherit : bool {#inherit-attached-prop}

If true, the [colorSet](qml-org-kde-kirigami-platform-theme.md#colorSet-attached-prop) will be inherited from the colorset of a theme of one of the ancestor items.

default: true

### \[read-only\] Theme.lightFrameContrast : real {#lightFrameContrast-attached-prop}

Returns half of the [frameContrast](qml-org-kde-kirigami-platform-theme.md#frameContrast-attached-prop) value; used by Separator.Weight.Light Value is between 0.0 and 1.0.

### Theme.linkBackgroundColor : color {#linkBackgroundColor-attached-prop}

Background color for links.

### Theme.linkColor : color {#linkColor-attached-prop}

Color for links.

### Theme.negativeBackgroundColor : color {#negativeBackgroundColor-attached-prop}

Background color for negative areas, such as critical errors and destructive actions.

### Theme.negativeTextColor : color {#negativeTextColor-attached-prop}

Foreground color for negative areas, such as critical error text.

### Theme.neutralBackgroundColor : color {#neutralBackgroundColor-attached-prop}

Background color for neutral areas, such as warnings (but not critical).

### Theme.neutralTextColor : color {#neutralTextColor-attached-prop}

Foreground color for neutral areas, such as warning texts (but not critical).

### \[read-only\] Theme.palette : QPalette {#palette-attached-prop}

Palette.

### Theme.positiveBackgroundColor : color {#positiveBackgroundColor-attached-prop}

Background color for positive areas, such as success messages and trusted content.

### Theme.positiveTextColor : color {#positiveTextColor-attached-prop}

Success messages, trusted content.

### \[read-only\] Theme.smallFont : font {#smallFont-attached-prop}

Small font.

### Theme.textColor : color {#textColor-attached-prop}

Color for normal foregrounds, usually text, but not limited to it, anything that should be painted with a clear contrast should use this color.

### \[read-only\] Theme.toolsArea : ToolsArea {#toolsArea-attached-prop}

How the window's tools area (toolbars and main menu bar under the title bar) is drawn, as the platform gives it. The same object for every item.

### Theme.useAlternateBackgroundColor : bool {#useAlternateBackgroundColor-attached-prop}

Hint for item views to actually make use of the alternate background color feature.

### Theme.visitedLinkBackgroundColor : color {#visitedLinkBackgroundColor-attached-prop}

Background color for visited links, usually a bit darker than [linkBackgroundColor](qml-org-kde-kirigami-platform-theme.md#linkBackgroundColor-attached-prop).

### Theme.visitedLinkColor : color {#visitedLinkColor-attached-prop}

Color for visited links, usually a bit darker than [linkColor](qml-org-kde-kirigami-platform-theme.md#linkColor-attached-prop).
