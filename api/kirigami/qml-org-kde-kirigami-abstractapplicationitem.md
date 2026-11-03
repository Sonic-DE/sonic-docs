---
title: "AbstractApplicationItem QML Type"
description: "An item that provides the features of AbstractApplicationWindow without the window itself."
---

# AbstractApplicationItem QML Type

An item that provides the features of [AbstractApplicationWindow](qml-org-kde-kirigami-abstractapplicationwindow.md) without the window itself. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html)
- Inherited By: [ApplicationItem](qml-org-kde-kirigami-applicationitem.md)

## Detailed Description {#details}

This allows embedding into a larger application. Unless you need extra flexibility it is recommended to use [ApplicationItem](qml-org-kde-kirigami-applicationitem.md) instead.

Example usage:

```cpp
import org.kde.kirigami as Kirigami

Kirigami.AbstractApplicationItem {
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

    pageStack: Kirigami.PageRow {
        ...
    }
 [...]
}
```

## Property Documentation {#property-documentation}

### background : Item {#background-prop}

This property holds the background of the Application UI.

### color : color {#color-prop}

This property holds the color for the background.

default: Kirigami.Theme.backgroundColor

### \[read-only\] contentItem : Item {#contentItem-prop}

This property holds the Item of the main part of the Application UI.

### contextDrawer : OverlayDrawer {#contextDrawer-prop}

This property holds the drawer for context-dependent actions.

The drawer that will be opened by sliding from the right screen edge or by dragging the ActionButton to the left.

> **Note:** It is recommended to use the [ContextDrawer](qml-org-kde-kirigami-contextdrawer.md) type here.

The contents of the context drawer should depend from what page is loaded in the main [pageStack](qml-org-kde-kirigami-abstractapplicationitem.md#pageStack-prop).

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

### controlsVisible : bool {#controlsVisible-prop}

This property sets whether the standard chrome of the app is visible.

These are the action button, the drawer handles and the application header.

default: true

### font : font {#font-prop}

This property holds the font for this item.

default: Kirigami.Theme.defaultFont

### footer : Item {#footer-prop}

This property holds an item that can be used as a footer for the application.

### globalDrawer : OverlayDrawer {#globalDrawer-prop}

This property holds the drawer for global actions.

This drawer can be opened by sliding from the left screen edge or by dragging the ActionButton to the right.

> **Note:** It is recommended to use the [GlobalDrawer](qml-org-kde-kirigami-globaldrawer.md) here.

### header : AbstractApplicationHeader {#header-prop}

This property holds an item that can be used as a title for the application.

Scrolling the main page will make it taller or shorter (through the point of going away).

It's a behavior similar to the typical mobile web browser addressbar.

The minimum, preferred and maximum heights of the item can be controlled with:

- Layout.minimumHeight: default is 0, i.e. hidden
- Layout.preferredHeight: default is Kirigami.Units.gridUnit \* 1.6
- Layout.maximumHeight: default is Kirigami.Units.gridUnit \* 3

To achieve a titlebar that stays completely fixed, just set the 3 sizes as the same.

### locale : Locale {#locale-prop}

This property holds the locale for this item.

### menuBar : T.MenuBar {#menuBar-prop}

This property holds an item that can be used as a menuBar for the application.

### pageStack : Item {#pageStack-prop}

This property holds the stack used to allocate the pages and to manage the transitions between them.

Put a container here, such as [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html).Controls.[StackView](https://doc.qt.io/qt-6/qml-qtquick-controls-stackview.html).

### wideScreen : bool {#wideScreen-prop}

This property tells us whether the application is in "widescreen" mode.

This is enabled on desktops or horizontal tablets.

> **Note:** Different styles can have their own logic for deciding this.

## Method Documentation {#method-documentation}

### applicationWindow() {#applicationWindow-method}

This property gets application windows object anywhere in the application. Returns a pointer to this item.

### hidePassiveNotification(*index* = 0) {#hidePassiveNotification-method}

This function hides the passive notification at specified index, if any is shown.

`index` Index of the notification to hide. Default is 0 (oldest notification).

### showPassiveNotification(*message*, *timeout*, *actionText*, *callBack*) {#showPassiveNotification-method}

This function shows a little passive notification at the bottom of the app window lasting for few seconds, with an optional action button.

`message` The text message to be shown to the user.

`timeout` How long to show the message: possible values: "short", "long", or the number of milliseconds.

`actionText` Text in the action button, if any.

`callBack` A JavaScript function that will be executed when the user clicks the button.
