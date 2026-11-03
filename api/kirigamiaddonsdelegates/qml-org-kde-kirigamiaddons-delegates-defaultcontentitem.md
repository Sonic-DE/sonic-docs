---
title: "DefaultContentItem QML Type"
description: "Content item which is used by default in the RoundedItemDelegate and IndicatorItemDelegate."
---

# DefaultContentItem QML Type

Content item which is used by default in the [RoundedItemDelegate](qml-org-kde-kirigamiaddons-delegates-roundeditemdelegate.md) and [IndicatorItemDelegate](qml-org-kde-kirigamiaddons-delegates-indicatoritemdelegate.md). [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.delegates
- Inherits: [RowLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-rowlayout.html)

## Detailed Description {#details}

Provides a label and an icon.

This can be used directly as contentItem or inside a [RowLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-rowlayout.html) if you need to put some content before or after this item.

## Property Documentation {#property-documentation}

### \[read-only\] iconItem : Kirigami.Icon {#iconItem-prop}

This property holds the [Kirigami.Icon](../kirigami/qml-org-kde-kirigami-primitives-icon.md) containing the icon of the item delegate.

### \[required\] itemDelegate : AbstractButton {#itemDelegate-prop}

This required property holds the item delegate corresponding to this content item.

### \[read-only\] labelItem : Label {#labelItem-prop}

This property holds the Label containing the text of the item delegate.
