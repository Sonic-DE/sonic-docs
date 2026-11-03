---
title: "GlobalDrawer QML Type"
description: "A specialized form of the Drawer intended for showing an application's always-available global actions."
---

# GlobalDrawer QML Type

A specialized form of the Drawer intended for showing an application's always-available global actions. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [OverlayDrawer](qml-org-kde-kirigami-overlaydrawer.md)

## Detailed Description {#details}

Think of it like a mobile version of a desktop application's menubar.

Example usage:

```cpp
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
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
}
```

## Property Documentation {#property-documentation}

### actions : list\<Action\> {#actions-prop}

This property holds the actions displayed in the drawer.

The list of actions can be nested having a tree structure. A tree depth bigger than 2 is discouraged.

Example usage:

```cpp
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
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
}
```

### collapseButtonVisible : bool {#collapseButtonVisible-prop}

This property sets the visibility of the collapse button when the drawer collapsible.

default: true

### \[default\] content : QtObject {#content-prop}

This property holds items that are displayed under the actions.

Example usage:

```cpp
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
 [...]
    globalDrawer: Kirigami.GlobalDrawer {
        actions: [...]
        Button {
            text: "Button"
            onClicked: //do stuff
        }
    }
 [...]
}
```

### \[read-only\] currentSubMenu : T.Action {#currentSubMenu-prop}

This property points to the action acting as a submenu

### footer : Item {#footer-prop}

This property holds an item that will always be displayed at the bottom of the drawer.

If the drawer contents can be scrolled, this item will stay still and won't scroll.

> **Note:** This property is mainly intended for toolbars.

### header : Item {#header-prop}

This property holds an item that will always be displayed at the top of the drawer.

If the drawer contents can be scrolled, this item will stay still and won't scroll.

> **Note:** This property is mainly intended for toolbars.

### isMenu : bool {#isMenu-prop}

This property sets whether the drawer becomes a menu.

Prior to 6.21 this option had no effect for mobile applications. If you wish to keep that behaviour you can use something like:

```cpp
isMenu: !Platform.Settings.isMobile
```

default: `false`

### resetMenuOnTriggered : bool {#resetMenuOnTriggered-prop}

This property sets whether activating a leaf action resets the menu to show leaf's parent actions.

A leaf action is an action without any child actions.

default: true

### showContentWhenCollapsed : bool {#showContentWhenCollapsed-prop}

This property sets whether content items at the bottom should be shown. when the drawer is collapsed as a sidebar.

If you want to keep some items visible and some invisible, set this to false and control the visibility/opacity of individual items, binded to the collapsed property.

default: false

*See also* [content](qml-org-kde-kirigami-globaldrawer.md#content-prop)

### showTopContentWhenCollapsed : bool {#showTopContentWhenCollapsed-prop}

This property sets whether content items at the top should be shown. when the drawer is collapsed as a sidebar.

If you want to keep some items visible and some invisible, set this to false and control the visibility/opacity of individual items, binded to the collapsed property.

default: false

### title : string {#title-prop}

This property holds the title displayed at the top of the drawer.

### titleIcon : var {#titleIcon-prop}

This property holds an icon to be displayed alongside the title.

*See also* [Icon::source](qml-org-kde-kirigami-primitives-icon.md#source-prop)

### topContent : QtObject {#topContent-prop}

This property holds items that are displayed above the actions.

Example usage:

```cpp
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
 [...]
    globalDrawer: Kirigami.GlobalDrawer {
        actions: [...]
        topContent: [Button {
            text: "Button"
            onClicked: //do stuff
        }]
    }
 [...]
}
```

## Method Documentation {#method-documentation}

### ensureVisible(*item*, *yOffset*) {#ensureVisible-method}

This method checks whether a particular drawer entry is in view, and scrolls the drawer to center the item if it is not.

Drawer items supplied through the actions property will handle this automatically, but items supplied in [topContent](qml-org-kde-kirigami-globaldrawer.md#topContent-prop) will need to call this explicitly on receiving focus Otherwise, if the user passes focus to the item with e.g. keyboard navigation, it may be outside the visible area.

When called, this method will place the visible area such that the item at the center if any part of it is currently outside.

```cpp
QQC2.ItemDelegate {
    id: item
    //  ...
    onFocusChanged: if (focus) drawer.ensureVisible(item)
}
```

`item` The item that should be in the visible area of the drawer. Item coordinates need to be in the coordinate system of the drawer's flickable.

`yOffset` Offset to align the item's and the flickable's coordinate system (optional)

### void resetMenu() {#resetMenu-method}

This function reverts the menu back to its initial state.
