---
title: "AbstractApplicationWindow QML Type"
description: "A window that provides some basic features needed for all apps."
---

# AbstractApplicationWindow QML Type

A window that provides some basic features needed for all apps. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [ApplicationWindow](https://doc.qt.io/qt-6/qml-qtquick-controls-applicationwindow.html) (QtQuick.Controls)
- Inherited By: [ApplicationWindow](qml-org-kde-kirigami-applicationwindow.md) (org.kde.kirigami)

## Detailed Description {#details}

Use this class only if you are implementing a custom content item and don’t need any of the standard semantics and features of [ApplicationWindow](qml-org-kde-kirigami-applicationwindow.md).

Otherwise, use [ApplicationWindow](qml-org-kde-kirigami-applicationwindow.md).

It's usually used as a root QML component for the application. It provides support for a central page stack, side drawers, and basic support for the Android back button.

Setting a width and height property on the [ApplicationWindow](qml-org-kde-kirigami-applicationwindow.md) will set its initial size, but it won't set it as an automatically binding. to resize programmatically the [ApplicationWindow](qml-org-kde-kirigami-applicationwindow.md) they need to be assigned again in an imperative fashion

Example usage:

```cpp
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

    pageStack: PageStack {
        ...
    }
 [...]
}
```

## Property Documentation {#property-documentation}

### contextDrawer : OverlayDrawer {#contextDrawer-prop}

This property holds the drawer for context-dependent actions.

The drawer that will be opened by sliding from the right screen edge or by dragging the ActionButton to the left.

> **Note:** It is recommended to use the [ContextDrawer](qml-org-kde-kirigami-contextdrawer.md) type here.

The contents of the context drawer should depend from what page is loaded in the main [pageStack](qml-org-kde-kirigami-abstractapplicationwindow.md#pageStack-prop).

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

### \[default: true\] controlsVisible : bool {#controlsVisible-prop}

This property sets whether the standard chrome of the app is visible.

These are the action button, the drawer handles, and the application header.

### globalDrawer : OverlayDrawer {#globalDrawer-prop}

This property holds the drawer for global actions.

This drawer can be opened by sliding from the left screen edge or by dragging the ActionButton to the right.

> **Note:** It is recommended to use the [GlobalDrawer](qml-org-kde-kirigami-globaldrawer.md) here.

### \[read-only\] overlay : Item {#overlay-prop}

The same as Overlay.overlay.

### pageStack : Item {#pageStack-prop}

This property holds the stack used to allocate the pages and to manage the transitions between them.

Put a container here, such as [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html).Controls.[StackView](https://doc.qt.io/qt-6/qml-qtquick-controls-stackview.html).

### \[read-only\] quitAction : Controls.Action {#quitAction-prop}

This property holds a standard action that will quit the application when triggered. Its properties have the following values:

```cpp
Action {
    text: "Quit"
    icon.name: "application-exit-symbolic"
    shortcut: StandardKey.Quit
    // ...
}
```

### wideScreen : bool {#wideScreen-prop}

This property tells whether the application is in "widescreen" mode.

This is enabled on desktops or horizontal tablets.

> **Note:** Different styles can have their own logic for deciding this.

## Method Documentation {#method-documentation}

### applicationWindow() {#applicationWindow-method}

This function returns application window's object anywhere in the application. Returns a pointer to this application window can be used anywhere in the application.

### hidePassiveNotification(*index* = 0) {#hidePassiveNotification-method}

This function hides the passive notification at specified index, if any is shown.

`index` Index of the notification to hide. Default is 0 (oldest notification).

### void showPassiveNotification(string *message*, int *timeout*, string *actionText*, var *callBack*) {#showPassiveNotification-method}

This function shows a little passive notification at the bottom of the app window lasting for few seconds, with an optional action button.

`message` The text message to be shown to the user.

`timeout` How long to show the message: possible values: "short", "long", or the number of milliseconds.

`actionText` Text in the action button, if any.

`callBack` A JavaScript function that will be executed when the user clicks the button.
