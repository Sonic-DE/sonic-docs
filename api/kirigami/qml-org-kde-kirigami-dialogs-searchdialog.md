---
title: "SearchDialog QML Type"
description: "A dialog to let's you do a global search across your applications documents, chat rooms and more. This type was introduced in Qt 6.3."
---

# SearchDialog QML Type

A dialog to let's you do a global search across your applications documents, chat rooms and more. This type was introduced in Qt 6.3. [More...](#details)

- Import Statement: import org.kde.kirigami.dialogs
- Since: Qt 6.3
- Inherits: [Dialog](https://doc.qt.io/qt-6/qml-qtquick-controls-dialog.html)

## Detailed Description {#details}

Example usage for a chat app where we want to quickly search for a room.

```qml
import QtQuick
import org.kde.kitemmodels as KItemModels
import org.kde.kirigami as Kirigami

Kirigami.SearchDialog {
   id: root

   onTextChanged: {
       sortModel.filterString = text;
   }
   onAccepted: listView.currentItem.clicked()

   emptyText: i18nc("Placeholder message", "No room found.")

   model: KItemModels.KSortFilterProxyModel {
       id: sortModel

       sourceModel: RoomModel { }
   }

   delegate: RoomDelegate {
       onClicked: root.close()
   }

   Shortcut {
       sequence: "Ctrl+K"
       onActivated: root.open()
   }
}
```

> **Note:** This component is unsuitable on mobile. Instead on mobile prefer to use a separate page for the search.

> **Note:** By default, the title and standardButtons property are ignored.

## Property Documentation {#property-documentation}

### count : int {#count-prop}

This property holds the number of search results displayed in the internal [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html).

### currentItem : Item {#currentItem-prop}

This property holds an alias to the currentItem component of the internal [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html).

### delegate : Component {#delegate-prop}

This property holds an alias to the delegate component of the internal [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html).

### \[since 6.10\] emptyHelpfulAction : Action {#emptyHelpfulAction-prop}

Helpful action when the list is empty

This property holds an alias to the helpful action of the placeholder message when the internal list view is empty.

This property was introduced in Qt 6.10.

### emptyIcon group {#emptyIcon-prop}

**emptyIcon.color : color**

**emptyIcon.height : int**

**emptyIcon.name : string**

**emptyIcon.source : string**

**emptyIcon.width : int**

This property holds an alias to the placeholder message icon displayed when the internal list view is empty.

### emptyText : string {#emptyText-prop}

This property holds an alias to the placeholder message text displayed when the internal list view is empty.

### model : model {#model-prop}

This property holds an alias to the model of the internal [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html).

### searchFieldLeftActions : Action {#searchFieldLeftActions-prop}

This property holds an alias to the left actions of the search field.

*See also* [ActionTextField::leftActions](qml-org-kde-kirigami-actiontextfield.md#leftActions-prop)

### searchFieldPlaceholderText : string {#searchFieldPlaceholderText-prop}

The placeholder text shown in the (empty) search field.

### searchFieldRightActions : Action {#searchFieldRightActions-prop}

This property holds an alias to the right actions of the search field.

*See also* [ActionTextField::rightActions](qml-org-kde-kirigami-actiontextfield.md#rightActions-prop)

### section group {#section-prop}

**section.criteria : enumeration**

**section.delegate : Component**

**section.labelPositioning : enumneration**

**section.property : string**

This property holds an alias to the section component of the internal [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html).

### text : string {#text-prop}

This property holds an alias to the content of the search field.
