---
title: "AbstractCard QML Type"
description: "The base item for all kinds of cards."
---

# AbstractCard QML Type

The base item for all kinds of cards. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [ItemDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-itemdelegate.html)
- Inherited By: [Card](qml-org-kde-kirigami-card.md)

## Detailed Description {#details}

A card is a visual object that groups its contents into a logical unit, connecting them all together visually. Cards can be interactive and clickable, or visual only, purely used for grouping.

[AbstractCard](qml-org-kde-kirigami-abstractcard.md) is an empty card, providing just the styling and basic properties. Use an [AbstractCard](qml-org-kde-kirigami-abstractcard.md) when you want the visual styling and grouping of a card, but plan to fill it with your own custom content layout. Content is organized into three properties: `header`, `contentItem`, and `footer`.

The [Card](qml-org-kde-kirigami-card.md) component provides a standard layout if your needs are less custom.

## Property Documentation {#property-documentation}

### \[default: null\] footer : Item {#footer-prop}

This property holds an item that serves as a footer.

This item will be positioned at the bottom if [headerOrientation](qml-org-kde-kirigami-abstractcard.md#headerOrientation-prop) is Qt.Vertical or on the right if it is Qt.Horizontal.

### \[default: null\] header : Item {#header-prop}

This property holds an item that serves as a header.

This item will be positioned on top if [headerOrientation](qml-org-kde-kirigami-abstractcard.md#headerOrientation-prop) is Qt.Vertical or on the left if it is Qt.Horizontal.

### \[default: Qt.Vertical\] headerOrientation : int {#headerOrientation-prop}

This property sets the card's orientation.

- Qt.Vertical: the header will be positioned on top
- Qt.Horizontal: the header will be positioned on the leading side

### \[default: false\] showClickFeedback : bool {#showClickFeedback-prop}

This property sets whether clicking or tapping on the card shows visual click feedback.

Use this if you want the card to perform an action in its `onClicked` signal handler.
