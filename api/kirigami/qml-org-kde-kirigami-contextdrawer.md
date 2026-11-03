---
title: "ContextDrawer QML Type"
description: "A specialized type of drawer that will show a list of actions relevant to the application's current page."
---

# ContextDrawer QML Type

A specialized type of drawer that will show a list of actions relevant to the application's current page. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [OverlayDrawer](qml-org-kde-kirigami-overlaydrawer.md)

## Detailed Description {#details}

Example usage:

```cpp
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    contextDrawer: Kirigami.ContextDrawer {
        enabled: true
        actions: [
            Kirigami.Action {
                icon.name: "edit"
                text: "Action text"
                onTriggered: {
                    // do stuff
                }
            },
            Kirigami.Action {
                icon.name: "edit"
                text: "Action text"
                onTriggered: {
                    // do stuff
                }
            }
        ]
    }
}
```

## Property Documentation {#property-documentation}

### actions : list\<Action\> {#actions-prop}

List of contextual actions to be displayed in a [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html).

### footer : Component {#footer-prop}

Arbitrary content to show below the list view.

### header : Component {#header-prop}

Arbitrary content to show above the list view.

default: an Item containing a Kirigami.Heading that displays a title whose text is controlled by the title property.

### title : string {#title-prop}

A title for the action list that will be shown to the user when opens the drawer

default: qsTr("Actions")
