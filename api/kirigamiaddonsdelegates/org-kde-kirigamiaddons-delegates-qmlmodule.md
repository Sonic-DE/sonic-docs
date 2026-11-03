---
title: "Kirigami Addons Delegates QML Types"
description: "Delegates for lists and grids in Kirigami applications."
---

# Kirigami Addons Delegates QML Types

Delegates for lists and grids in Kirigami applications.

Import the module with an alias in a QML file that displays a collection:

```qml
import org.kde.kirigamiaddons.delegates as Delegates
```

## Displaying a list {#displaying-a-list}

Use [RoundedItemDelegate](qml-org-kde-kirigamiaddons-delegates-roundeditemdelegate.md) for a list or grid item that opens another page or selects an item. It provides a rounded background for hover, focus, and selection states. When it is the direct delegate of a [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html) or [GridView](https://doc.qt.io/qt-6/qml-qtquick-gridview.html), it uses the view to size itself and highlight the current item.

```qml
import QtQuick
import org.kde.kirigamiaddons.delegates as Delegates

ListView {
    id: foldersView
    model: ["Inbox", "Archive"]

    delegate: Delegates.RoundedItemDelegate {
        required property int index
        required property string modelData

        text: modelData
        icon.name: "folder"
        onClicked: foldersView.currentIndex = index
    }
}
```

In a drag and drop workflow, the view's delegate can be an `Item` that stays in the list or grid while its child [RoundedItemDelegate](qml-org-kde-kirigamiaddons-delegates-roundeditemdelegate.md) is reparented during a drag. The child does not receive the view's attached properties automatically. Bind `listView: wrapper.ListView` or `gridView: wrapper.GridView` to retain the built-in sizing and highlighting, or set those properties on the child explicitly.

## Adding a subtitle or extra content {#adding-a-subtitle-or-extra-content}

The default [DefaultContentItem](qml-org-kde-kirigamiaddons-delegates-defaultcontentitem.md) shows the delegate's icon and text. Replace `contentItem` with [SubtitleContentItem](qml-org-kde-kirigamiaddons-delegates-subtitlecontentitem.md) to add a second line. Pass the containing delegate through `itemDelegate` so the content uses its text, icon, font, and enabled state:

```qml
Delegates.RoundedItemDelegate {
    id: messageDelegate
    text: i18nc("@title", "Project update")
    icon.name: "mail-message"

    contentItem: Delegates.SubtitleContentItem {
        itemDelegate: messageDelegate
        subtitle: i18nc("@info", "Received today")
    }
}
```

For a more specialized layout, place [DefaultContentItem](qml-org-kde-kirigamiaddons-delegates-defaultcontentitem.md) inside a `RowLayout` with other controls and assign the layout to `contentItem`.

## Choices, unread items, and trees {#choices-unread-items-and-trees}

Use [CheckDelegate](qml-org-kde-kirigamiaddons-delegates-checkdelegate.md) for an independent on/off choice and [RadioDelegate](qml-org-kde-kirigamiaddons-delegates-radiodelegate.md) for a choice in a group. Both show an indicator and expose the inherited `checked` and `toggled` members. Put radio delegates in a `ButtonGroup` when only one choice may be selected. Store the checked state in the model when delegates may be recreated as the user scrolls.

[IndicatorItemDelegate](qml-org-kde-kirigamiaddons-delegates-indicatoritemdelegate.md) adds an accent bar for an unread item. It is intended as a direct [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html) delegate; set its required `unread` property. The view supplies `index` from the model. Use [RoundedTreeDelegate](qml-org-kde-kirigamiaddons-delegates-roundedtreedelegate.md) with a `KDescendantsProxyModel` to show expandable tree rows in a [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html). It expects the descendant level and expansion roles from that model.

*See also* [RoundedItemDelegate](qml-org-kde-kirigamiaddons-delegates-roundeditemdelegate.md), [CheckDelegate](qml-org-kde-kirigamiaddons-delegates-checkdelegate.md), [RadioDelegate](qml-org-kde-kirigamiaddons-delegates-radiodelegate.md), [SubtitleContentItem](qml-org-kde-kirigamiaddons-delegates-subtitlecontentitem.md), [IndicatorItemDelegate](qml-org-kde-kirigamiaddons-delegates-indicatoritemdelegate.md), [RoundedTreeDelegate](qml-org-kde-kirigamiaddons-delegates-roundedtreedelegate.md)

## Contents

- [CheckDelegate](qml-org-kde-kirigamiaddons-delegates-checkdelegate.md): An CheckDelegate providing a modern look and feel.
- [DefaultContentItem](qml-org-kde-kirigamiaddons-delegates-defaultcontentitem.md): Content item which is used by default in the RoundedItemDelegate and IndicatorItemDelegate.
- [IndicatorItemDelegate](qml-org-kde-kirigamiaddons-delegates-indicatoritemdelegate.md)
- [RadioDelegate](qml-org-kde-kirigamiaddons-delegates-radiodelegate.md): An CheckDelegate providing a modern look and feel.
- [RoundedItemDelegate](qml-org-kde-kirigamiaddons-delegates-roundeditemdelegate.md): An ItemDelegate providing a modern look and feel.
- [RoundedTreeDelegate](qml-org-kde-kirigamiaddons-delegates-roundedtreedelegate.md): Rounded item delegate meant to be used in combination with a ListView and a KDescendantsProxyModel to create a TreeView.
- [SubtitleContentItem](qml-org-kde-kirigamiaddons-delegates-subtitlecontentitem.md)
