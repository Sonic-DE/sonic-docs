---
title: "CardsListView QML Type"
description: "A ListView that can have AbstractCard as its delegate."
---

# CardsListView QML Type

A [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html) that can have [AbstractCard](qml-org-kde-kirigami-abstractcard.md) as its delegate. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html)

## Detailed Description {#details}

This control will automatically assign the proper spacings and margins around the cards adhering to the design guidelines.

[CardsListView](qml-org-kde-kirigami-cardslistview.md) should be used only with cards which can look good at any horizontal size, so it is recommended to directly use [AbstractCard](qml-org-kde-kirigami-abstractcard.md) with an appropriate layout inside, because they are stretching for the whole list width.

Therefore, it is discouraged to use it with the Card type.

The choice between using this view with [AbstractCard](qml-org-kde-kirigami-abstractcard.md) or a normal [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html) is purely a choice based on aesthetics alone.

It is recommended to use default values.
