---
title: "SwipeListItem QML Type"
description: "This type is deprecated. We strongly advise against using it in new code."
---

# SwipeListItem QML Type

**This type is deprecated. We strongly advise against using it in new code.** [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [SwipeDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-swipedelegate.html)
- Status: Deprecated

**This type is deprecated. We strongly advise against using it in new code.**

## Detailed Description {#details}

Don't use items of type [SwipeListItem](qml-org-kde-kirigami-swipelistitem.md), it will be removed in the future. Use instead simpler [ItemDelegate](https://doc.qt.io/qt-6/qml-qtquick-controls-itemdelegate.html) instances, with contents from org.kde.kirigami.delegates when needed.

An item delegate intended to support extra actions obtainable by uncovering them by dragging away the item with the handle.

This acts as a container for normal list items.

Example usage:

```cpp
ListView {
    model: myModel
    delegate: SwipeListItem {
        QQC2.Label {
            text: model.text
        }
        actions: [
             Action {
                 icon.name: "document-decrypt"
                 onTriggered: print("Action 1 clicked")
             },
             Action {
                 icon.name: model.action2Icon
                 onTriggered: //do something
             }
        ]
    }

}
```

## Property Documentation {#property-documentation}

### actions : list\<T.Action\> {#actions-prop}

This property holds actions of the list item.

At most 4 actions can be revealed when sliding away the list item; others will be shown in the overflow menu.

### \[read-only\] actionsVisible : bool {#actionsVisible-prop}

This property tells whether actions are visible and interactive.

True if it's possible to see and interact with the item's actions.

Actions become hidden while editing of an item, for example.

### \[default: Kirigami.Theme.highlightColor\] activeBackgroundColor : color {#activeBackgroundColor-prop}

This property holds the color of the background when the item is pressed or selected.

It is advised to use the default value.

### activeTextColor : color {#activeTextColor-prop}

This property holds the color of the text when the item is pressed or selected.

It is advised to use the default value. default: Kirigami.Theme.highlightedTextColor

If custom text elements are inserted in a [SwipeListItem](qml-org-kde-kirigami-swipelistitem.md), their color property will have to be manually bound with this property

### \[default: : Kirigami.Theme.alternateBackgroundColor\] alternateBackgroundColor : color {#alternateBackgroundColor-prop}

This property holds the background color to be used when background alternating is enabled.

It is advised to use the default value.

### \[default: false\] alternatingBackground : bool {#alternatingBackground-prop}

This property sets whether instances of this list item will alternate between two colors, helping readability.

It is suggested to use this only when implementing a view with multiple columns.

### alwaysVisibleActions : bool {#alwaysVisibleActions-prop}

This property sets whether actions behind this [SwipeListItem](qml-org-kde-kirigami-swipelistitem.md) will always be visible.

default: true in desktop and tablet mode

### \[default: Kirigami.Theme.backgroundColor\] backgroundColor : color {#backgroundColor-prop}

This property holds the background color of the list item.

It is advised to use the default value.

### \[read-only\] overlayWidth : real {#overlayWidth-prop}

This property holds the width of the overlay.

The value can represent the width of the handle component or the action layout.

### \[default: false\] sectionDelegate : bool {#sectionDelegate-prop}

This property sets whether this item is a section delegate.

Setting this to true will make the list item look like a "title" for items under it.

*See also* [ListSectionHeader](qml-org-kde-kirigami-listsectionheader.md)

### \[default: false\] separatorVisible : bool {#separatorVisible-prop}

This property sets whether the separator is visible.

The separator is a line between this and the item under it.

### \[default: Theme.textColor\] textColor : color {#textColor-prop}

This property holds the color of the text in the item.

It is advised to use the default value.

If custom text elements are inserted in a [SwipeListItem](qml-org-kde-kirigami-swipelistitem.md), their color will have to be manually set with this property.
