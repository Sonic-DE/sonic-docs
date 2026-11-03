---
title: "ScrollablePage QML Type"
description: "ScrollablePage is a Page that holds scrollable content, such as a ListView."
---

# ScrollablePage QML Type

[ScrollablePage](qml-org-kde-kirigami-scrollablepage.md) is a Page that holds scrollable content, such as a [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html). [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [Page](qml-org-kde-kirigami-page.md)
- Inherited By: [AboutPage](qml-org-kde-kirigami-aboutpage.md)

## Detailed Description {#details}

Scrolling and scrolling indicators will be automatically managed.

Example usage:

```cpp
ScrollablePage {
    id: root
    // The page will automatically be scrollable
    Rectangle {
        width: root.width
        height: 99999
    }
}
```

> **Warning:** Do not put a [ScrollView](https://doc.qt.io/qt-6/qml-qtquick-controls-scrollview.html) inside of a [ScrollablePage](qml-org-kde-kirigami-scrollablepage.md); children of a [ScrollablePage](qml-org-kde-kirigami-scrollablepage.md) are already inside a [ScrollView](https://doc.qt.io/qt-6/qml-qtquick-controls-scrollview.html).

Another behavior added by this class is a "scroll down to refresh" behavior It also can give the contents of the flickable to have more top margins in order to make possible to scroll down the list to reach it with the thumb while using the phone with a single hand.

Implementations should handle the refresh themselves as follows.

Example usage:

```cpp
Kirigami.ScrollablePage {
    id: view
    supportsRefreshing: true
    onRefreshingChanged: {
        if (refreshing) {
            myModel.refresh();
        }
    }
    ListView {
        // NOTE: MyModel doesn't come from the components,
        // it's purely an example on how it can be used together
        // some application logic that can update the list model
        // and signals when it's done.
        model: MyModel {
            onRefreshDone: view.refreshing = false;
        }
        delegate: ItemDelegate {}
    }
}
[...]
```

## Property Documentation {#property-documentation}

### horizontalScrollBarInteractive : bool {#horizontalScrollBarInteractive-prop}

Set if the horizontal scrollbar should be interactable.

### horizontalScrollBarPolicy : int {#horizontalScrollBarPolicy-prop}

This property sets the horizontal scrollbar policy.

Possible values:

| Constant | Description |
| --- | --- |
| QQC2.ScrollBar.AsNeeded | The scroll bar is only shown when the content is too large to fit. |
| QQC2.ScrollBar.AlwaysOff | The scroll bar is never shown. |
| QQC2.ScrollBar.AlwaysOn | The scroll bar is always shown. |

The default value is [ScrollBar](https://doc.qt.io/qt-6/qml-qtquick-controls-scrollbar.html).AlwaysOff

*See also* [Qt::ScrollBarPolicy](https://doc.qt.io/qt-6/qt.html#ScrollBarPolicy-enum)

### keyboardNavigationEnabled : bool {#keyboardNavigationEnabled-prop}

This property sets whether it is possible to navigate the items in a view that support it.

If true, and if flickable is an item view (e.g. [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html), [GridView](https://doc.qt.io/qt-6/qml-qtquick-gridview.html)), it will be possible to navigate the view current items with keyboard up/down arrow buttons. Also, any key event will be forwarded to the current list item.

default: `true`

### refreshing : bool {#refreshing-prop}

This property tells whether the list is asking for a refresh.

This property will automatically be set to true when the user pulls the list down enough, which in return, shows a loading spinner. When this is set to true, it signals the application logic to start its refresh procedure.

default: `false`

> **Note:** The application itself will have to set back this property to false when done.

### supportsRefreshing : bool {#supportsRefreshing-prop}

This property sets whether scrollable page supports "pull down to refresh" behaviour.

default: `false`

### verticalScrollBarInteractive : bool {#verticalScrollBarInteractive-prop}

Set if the vertical scrollbar should be interactable.

### verticalScrollBarPolicy : int {#verticalScrollBarPolicy-prop}

This property sets the vertical scrollbar policy.

Possible values:

| Constant | Description |
| --- | --- |
| QQC2.ScrollBar.AsNeeded | The scroll bar is only shown when the content is too large to fit. |
| QQC2.ScrollBar.AlwaysOff | The scroll bar is never shown. |
| QQC2.ScrollBar.AlwaysOn | The scroll bar is always shown. |

*See also* Qt.ScrollBarPolicy

## Method Documentation {#method-documentation}

### ensureVisible(*item*, *xOffset*, *yOffset*) {#ensureVisible-method}

This method checks whether a particular child item is in view, and scrolls the page to center the item if it is not.

If the page is a View, the view should handle this by itself, but if the page is a manually handled layout, this needs to be done manually. Otherwise, if the user passes focus to an item with e.g. keyboard navigation, this may be outside the visible area.

When called, this method will place the visible area such that the item at the center if any part of it is currently outside. If the item is larger than the viewable area in either direction, the area will be scrolled such that the top left corner is visible.

```qml
Kirigami.ScrollablePage {
    id: page
    ColumnLayout {
        Repeater {
            model: 100
            delegate: QQC2.Button {
                text: modelData
                onFocusChanged: if (focus) page.ensureVisible(this)
            }
        }
    }
}
```

`item` The item that should be in the visible area of the flickable. Item coordinates need to be in the flickable's coordinate system.

`xOffset` (optional) Offsets to align the item's and the flickable's coordinate system

`yOffset` (optional) Offsets to align the item's and the flickable's coordinate system
