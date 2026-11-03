---
title: "ApplicationItem QML Type"
description: "An item that provides the features of ApplicationWindow without the window itself."
---

# ApplicationItem QML Type

An item that provides the features of [ApplicationWindow](qml-org-kde-kirigami-applicationwindow.md) without the window itself. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [AbstractApplicationItem](qml-org-kde-kirigami-abstractapplicationitem.md)

## Detailed Description {#details}

This allows embedding into a larger application. It's based around the [PageRow](qml-org-kde-kirigami-pagerow.md) component that allows adding/removing of pages.

Example usage:

```cpp
import org.kde.kirigami as Kirigami

Kirigami.ApplicationItem {
    globalDrawer: Kirigami.GlobalDrawer {
        actions: [
           Kirigami.Action {
               text: "View"
               icon.name: "view-list-icons"
               Kirigami.Action {
                       text: "action 1"
               }
               Kirigami.Action {
                       text: "action 2"
               }
               Kirigami.Action {
                       text: "action 3"
               }
           },
           Kirigami.Action {
               text: "Sync"
               icon.name: "folder-sync"
           }
        ]
    }

    contextDrawer: Kirigami.ContextDrawer {
        id: contextDrawer
    }

    pageStack.initialPage: Kirigami.Page {
        mainAction: Kirigami.Action {
            icon.name: "edit"
            onTriggered: {
                // do stuff
            }
        }
        contextualActions: [
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
        // ...
    }
}
```

## Property Documentation {#property-documentation}

### \[read-only\] pageStack : PageRow {#pageStack-prop}

This property holds the [PageRow](qml-org-kde-kirigami-pagerow.md) used to allocate the pages and manage the transitions between them.

It's using a [PageRow](qml-org-kde-kirigami-pagerow.md), while having the same API as [PageStack](qml-org-kde-kirigami-layouts-pagestack.md), it positions the pages as adjacent columns, with as many columns as can fit in the screen. An handheld device would usually have a single fullscreen column, a tablet device would have many tiled columns.
