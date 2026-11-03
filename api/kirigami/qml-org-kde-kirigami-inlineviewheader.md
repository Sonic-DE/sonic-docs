---
title: "InlineViewHeader QML Type"
description: "A fancy inline view header showing a title and optional actions."
---

# InlineViewHeader QML Type

A fancy inline view header showing a title and optional actions. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [ToolBar](https://doc.qt.io/qt-6/qml-qtquick-controls-toolbar.html)

## Detailed Description {#details}

Designed to be set as the header: property of a [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html) or [GridView](https://doc.qt.io/qt-6/qml-qtquick-gridview.html), this component provides a fancy inline header suitable for explaining the contents of its view to the user in an attractive and standardized way.

Actions globally relevant to the view can be defined using the [actions](qml-org-kde-kirigami-inlineviewheader.md#actions-prop) property. They will appear on the trailing side of the header as buttons, and collapse into an overflow menu when there isn't room to show them all.

The width property must be manually set to the parent view's width.

Example usage:

```cpp
import org.kde.kirigami as Kirigami

ListView {
    id: listView

    headerPositioning: ListView.OverlayHeader
    header: InlineViewHeader {
        width: listView.width
        text: "My amazing view"
        actions: [
            Kirigami.Action {
                icon.name: "list-add-symbolic"
                text: "Add item"
                onTriggered: {
                    // do stuff
                }
            }
        ]
    }

    model: [...]
    delegate: [...]
}
```

## Property Documentation {#property-documentation}

### actions : list\<Action\> {#actions-prop}

This property holds the list of actions to show on the header. Actions are added from left to right. If more actions are set than can fit, an overflow menu is provided.

### text : string {#text-prop}

This property holds the title text.
