---
title: "ListItemDragHandle QML Type"
description: "A handle to reorder items in a view."
---

# ListItemDragHandle QML Type

A handle to reorder items in a view. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)

## Detailed Description {#details}

Implements a drag handle supposed to be in items in ListViews to reorder items.

The [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html) must visualize a model which supports item reordering, such as ListModel.move() or [QAbstractItemModel](https://doc.qt.io/qt-6/qabstractitemmodel.html) instances with moveRows() correctly implemented.

In order for [ListItemDragHandle](qml-org-kde-kirigami-listitemdraghandle.md) to work correctly, the [listItem](qml-org-kde-kirigami-listitemdraghandle.md#listItem-prop) that is being dragged should not directly be the delegate of the [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html), but a child of it.

```cpp
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami
  ...
  Component {
      id: delegateComponent
      QQC2.ItemDelegate {
          id: listItem
          contentItem: RowLayout {
              Kirigami.ListItemDragHandle {
                  listItem: listItem
                  listView: mainList
                  onMoveRequested: (oldIndex, newIndex) => {
                      listModel.move(oldIndex, newIndex, 1);
                  }
              }
              QQC2.Label {
                  text: model.label
              }
          }
      }
  }
  ListView {
      id: mainList

      model: ListModel {
          id: listModel
          ListElement {
              label: "Item 1"
          }
          ListElement {
              label: "Item 2"
          }
          ListElement {
              label: "Item 3"
          }
      }
      //this is optional to make list items animated when reordered
      moveDisplaced: Transition {
          YAnimator {
              duration: Kirigami.Units.longDuration
              easing.type: Easing.InOutQuad
          }
      }
      delegate: Loader {
          width: mainList.width
          sourceComponent: delegateComponent
      }
  }
  ...
```

## Property Documentation {#property-documentation}

### \[read-only\] dragActive : alias {#dragActive-prop}

This property holds the fact that the handle is being dragged.

### incrementalMoves : bool {#incrementalMoves-prop}

This property holds the fact that we are doing incremental move requests or not.

### listItem : Item {#listItem-prop}

This property holds the delegate that will be dragged around.

> **Note:** This item must be a child of the actual [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html)'s delegate.

### listView : ListView {#listView-prop}

This property holds the [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html) that the delegate belong to.

## Signal Documentation {#signal-documentation}

### dropped(int *oldIndex*, int *newIndex*) {#dropped-signal}

This signal is emitted when the drag operation is complete and the item has been dropped in the new final position.

`oldIndex` The index the item is currently at.

`newIndex` The index we want to drop the item to.

> **Note:** The corresponding handler is `onDropped`.

### moveRequested(int *oldIndex*, int *newIndex*) {#moveRequested-signal}

This signal is emitted when the drag handle wants to move the item in the model.

The following example does the move in the case a ListModel is used:

```cpp
onMoveRequested: (oldIndex, newIndex) => {
    listModel.move(oldIndex, newIndex, 1);
}
```

`oldIndex` The index the item is currently at.

`newIndex` The index we want to move the item to.

> **Note:** The corresponding handler is `onMoveRequested`.
