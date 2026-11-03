---
title: "CheckDelegate QML Type"
description: "An CheckDelegate providing a modern look and feel."
---

# CheckDelegate QML Type

An [CheckDelegate](qml-org-kde-kirigamiaddons-delegates-checkdelegate.md) providing a modern look and feel. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.delegates

## Detailed Description {#details}

Use a combination of [SubtitleContentItem](qml-org-kde-kirigamiaddons-delegates-subtitlecontentitem.md), [DefaultContentItem](qml-org-kde-kirigamiaddons-delegates-defaultcontentitem.md) and [RowLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-rowlayout.html) for the contentItem.

## Property Documentation {#property-documentation}

### \[default: false\] dropAreaHovered : bool {#dropAreaHovered-prop}

This property holds whether the drop area is hovered.

This allow to emulate an hover effect which can't be done with the normal hovered property as it is read only.

### gridView : GridView {#gridView-prop}

This property holds a [GridView](https://doc.qt.io/qt-6/qml-qtquick-gridview.html).

It is automatically set if the [RoundedItemDelegate](qml-org-kde-kirigamiaddons-delegates-roundeditemdelegate.md) is the direct delegate of a [GridView](https://doc.qt.io/qt-6/qml-qtquick-gridview.html) and must be set otherwise.

### listView : ListView {#listView-prop}

This property holds a [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html).

It is automatically set if the [RoundedItemDelegate](qml-org-kde-kirigamiaddons-delegates-roundeditemdelegate.md) is the direct delegate of a [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html) and must be set otherwise.
