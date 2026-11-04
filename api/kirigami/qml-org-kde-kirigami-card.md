---
title: "Card QML Type"
description: "Card with a standard layout."
---

# Card QML Type

Card with a standard layout. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [AbstractCard](qml-org-kde-kirigami-abstractcard.md)

## Detailed Description {#details}

Card implements a particular standardized layout inside an [AbstractCard](qml-org-kde-kirigami-abstractcard.md), with pre-defined header and footer items.

The header is an image that can contain an optional title and icon, accessible via the [banner](qml-org-kde-kirigami-card.md#banner-prop) grouped property.

The footer will show a series of ToolButtons (and eventually an overflow menu) representing the `action` property's actions.

Override the `contentItem` with the content you want to be displayed in the card between the pre-made header and footer.

Overriding the `header` and `footer` properties is discouraged, as this will result in the `title`, `icon`, and `actions` properties having no effect.

If you want to make your own completely custom layout, use [AbstractCard](qml-org-kde-kirigami-abstractcard.md) instead.

## Property Documentation {#property-documentation}

### actions : list\<T.Action\> {#actions-prop}

This property holds the clickable actions that will be available in the footer.

The actions will be represented by a list of ToolButtons with an overflow menu when not all of them will fit in the available space.

### banner group {#banner-prop}

### \[read-only\] banner.source : url {#banner.source-prop}

### \[read-only\] banner.title : string {#banner.title-prop}

### \[read-only\] banner.titleAlignment : Qt.Alignment {#banner.titleAlignment-prop}

### \[read-only\] banner.titleIcon : string {#banner.titleIcon-prop}

### \[read-only\] banner.titleLevel : int {#banner.titleLevel-prop}

### \[read-only\] banner.titleWrapMode : QtQuick.Text.wrapMode {#banner.titleWrapMode-prop}

This grouped property controls the banner image present in the header.

It also has the full set of properties that [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html).Image has, such as sourceSize and fillMode.

- source: The source for the image. It understands any URL valid for an Image component.
- titleIcon: The optional icon to put in the banner, either a freedesktop-compatible icon name (recommended) or any URL supported by [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html).Image.
- title: The title for the banner, shown as contrasting text over the image.
- titleAlignment: The alignment of the title inside the image. Default: `Qt.AlignTop | Qt.AlignLeft`.
- titleLevel: The Kirigami.Heading level for the title, ranging from 1 (big) to 5 (small). Default: `1`.
- titleWrapMode: Whether the header text should be able to wrap. Default: `Text.NoWrap`.
