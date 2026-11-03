---
title: "NavigationTabButton QML Type"
description: "Navigation buttons to be used for the NavigationTabBar component."
---

# NavigationTabButton QML Type

Navigation buttons to be used for the [NavigationTabBar](qml-org-kde-kirigami-navigationtabbar.md) component. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [TabButton](https://doc.qt.io/qt-6/qml-qtquick-controls-tabbutton.html)

## Detailed Description {#details}

It supplies its own padding, and also supports using the [AbstractButton::display](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html#display-prop) property to be used in column lists.

Alternative way to the actions property on [NavigationTabBar](qml-org-kde-kirigami-navigationtabbar.md), as it can be used with Repeater to generate buttons from models.

Example usage:

```cpp
Kirigami.NavigationTabBar {
     id: navTabBar
     Kirigami.NavigationTabButton {
         visible: true
         icon.name: "document-save"
         text: `test ${tabIndex + 1}`
         QQC2.ButtonGroup.group: navTabBar.tabGroup
     }
     Kirigami.NavigationTabButton {
         visible: false
         icon.name: "document-send"
         text: `test ${tabIndex + 1}`
         QQC2.ButtonGroup.group: navTabBar.tabGroup
     }
     actions: [
         Kirigami.Action {
             visible: true
             icon.name: "edit-copy"
             icon.height: 32
             icon.width: 32
             text: `test 3`
             checked: true
         },
         Kirigami.Action {
             visible: true
             icon.name: "edit-cut"
             text: `test 4`
             checkable: true
         },
         Kirigami.Action {
             visible: false
             icon.name: "edit-paste"
             text: `test 5`
         },
         Kirigami.Action {
             visible: true
             icon.source: "../logo.png"
             text: `test 6`
             checkable: true
         }
     ]
 }
```

## Property Documentation {#property-documentation}

### \[read-only\] tabIndex : int {#tabIndex-prop}

This property tells the index of this tab within the tab bar.
