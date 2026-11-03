---
title: "ApplicationWindow QML Type"
description: "A window that provides some basic features needed for all apps."
---

# ApplicationWindow QML Type

A window that provides some basic features needed for all apps. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [AbstractApplicationWindow](qml-org-kde-kirigami-abstractapplicationwindow.md)

## Detailed Description {#details}

It's usually used as a root QML component for the application. It's based around the [PageRow](qml-org-kde-kirigami-pagerow.md) component, the application will be about pages adding and removal. For most of the usages, this class should be used instead of [AbstractApplicationWindow](qml-org-kde-kirigami-abstractapplicationwindow.md)

Setting a width and height property on the [ApplicationWindow](qml-org-kde-kirigami-applicationwindow.md) will set its initial size, but it won't set it as an automatically binding. to resize programmatically the [ApplicationWindow](qml-org-kde-kirigami-applicationwindow.md) they need to be assigned again in an imperative fashion

Example usage:

```qml
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
 [...]
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
      [...]
    }
 [...]
}
```

## Property Documentation {#property-documentation}

### \[read-only\] pageStack : PageRow {#pageStack-prop}

This property holds the stack used to allocate the pages and to manage the transitions between them.

It's using a [PageRow](qml-org-kde-kirigami-pagerow.md), while having the same API as [PageStack](qml-org-kde-kirigami-layouts-pagestack.md), it positions the pages as adjacent columns, with as many columns as can fit in the screen. An handheld device would usually have a single fullscreen column, a tablet device would have many tiled columns.
