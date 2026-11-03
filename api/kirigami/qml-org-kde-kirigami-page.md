---
title: "Page QML Type"
description: "A container for all the app pages."
---

# Page QML Type

A container for all the app pages. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [Page](https://doc.qt.io/qt-6/qml-qtquick-controls-page.html)
- Inherited By: [ScrollablePage](qml-org-kde-kirigami-scrollablepage.md)

## Detailed Description {#details}

Everything pushed to the [ApplicationWindow](qml-org-kde-kirigami-applicationwindow.md)'s pageStack should be a Page.

For content that should be scrollable, such as ListViews, use [ScrollablePage](qml-org-kde-kirigami-scrollablepage.md) instead.

*See also* [ScrollablePage](qml-org-kde-kirigami-scrollablepage.md)

## Property Documentation {#property-documentation}

### actions : list\<Action\> {#actions-prop}

This property holds the actions for the page.

These actions will be displayed in the toolbar on the desktop and inside the [ContextDrawer](qml-org-kde-kirigami-contextdrawer.md) on mobile.

```cpp
import org.kde.kirigami as Kirigami

Kirigami.Page {
    actions: [
        Kirigami.Action {...},
        Kirigami.Action {...}
    }
}
```

### flickable : Flickable {#flickable-prop}

If the central element of the page is a Flickable ([ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html) and Gridview as well) you can set it there.

Normally, you wouldn't need to do that, but just use the [ScrollablePage](qml-org-kde-kirigami-scrollablepage.md) element instead.

Use this if your flickable has some non standard properties, such as not covering the whole Page.

*See also* [ScrollablePage](qml-org-kde-kirigami-scrollablepage.md)

### \[read-only\] globalToolBarItem : Item {#globalToolBarItem-prop}

The item used as global toolbar for the page present only if we are in a [PageRow](qml-org-kde-kirigami-pagerow.md) as a page or as a layer, and the style is either Titles or [ToolBar](https://doc.qt.io/qt-6/qml-qtquick-controls-toolbar.html).

### globalToolBarStyle : int {#globalToolBarStyle-prop}

The style for the automatically generated global toolbar.

By default the Page toolbar is the one set globally in the [PageRow](qml-org-kde-kirigami-pagerow.md) in its globalToolBar.style property.

A single page can override the application toolbar style for itself. It is discouraged to use this, except very specific exceptions, like a chat application which can't have controls on the bottom except the text field.

If the Page is not in a [PageRow](qml-org-kde-kirigami-pagerow.md), by default the toolbar will be invisible, so has to be explicitly set to Kirigami.ApplicationHeaderStyle.[ToolBar](https://doc.qt.io/qt-6/qml-qtquick-controls-toolbar.html) if desired to be used in that case.

### icon group {#icon-prop}

**icon.color : color**

**icon.height : int**

**icon.name : string**

**icon.source : string**

**icon.width : int**

This holds the icon that represents this page.

### \[read-only\] isCurrentPage : bool {#isCurrentPage-prop}

This property tells us if it is the currently active page.

Specifies if it's the currently selected page in the window's pages row, or if layers are used whether this is the topmost item on the layers stack. If the page is not attached to either a column view or a stack view, expect this to be true.

### \[read-only\] overlay : Item {#overlay-prop}

An item which stays on top of every other item in the page, if you want to make sure some elements are completely in a layer on top of the whole content, parent items to this one. It's a "local" version of [ApplicationWindow](qml-org-kde-kirigami-applicationwindow.md)'s overlay

### progress : var {#progress-prop}

Progress of a task this page is doing.

Set to undefined to indicate that there are no ongoing tasks.

default: `undefined`

### titleDelegate : Component {#titleDelegate-prop}

The delegate which will be used to draw the page title.

It can be customized to put any kind of Item in there.

## Signal Documentation {#signal-documentation}

### backRequested(var *event*) {#backRequested-signal}

Emitted when the application requests a Back action.

For instance a global "back" shortcut or the Android Back button has been pressed. The page can manage the back event by itself, and if it set event.accepted = true, it will stop the main application to manage the back event.

> **Note:** The corresponding handler is `onBackRequested`.
