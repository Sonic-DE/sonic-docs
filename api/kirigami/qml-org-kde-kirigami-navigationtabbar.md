---
title: "NavigationTabBar QML Type"
description: "Page navigation tab-bar, used as an alternative to sidebars for 3-5 elements. A NavigationTabBar can be both used as a footer or a header for a page. It can be combined with secondary toolbars above (if in the footer) to provide page actions."
---

# NavigationTabBar QML Type

Page navigation tab-bar, used as an alternative to sidebars for 3-5 elements. A [NavigationTabBar](qml-org-kde-kirigami-navigationtabbar.md) can be both used as a footer or a header for a page. It can be combined with secondary toolbars above (if in the footer) to provide page actions. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [ToolBar](https://doc.qt.io/qt-6/qml-qtquick-controls-toolbar.html)

## Detailed Description {#details}

Example usage:

```qml
import QtQuick
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Clock"

    pageStack.initialPage: worldPage

    Kirigami.Page {
        id: worldPage
        title: "World"
        visible: false
    }
    Kirigami.Page {
        id: timersPage
        title: "Timers"
        visible: false
    }
    Kirigami.Page {
        id: stopwatchPage
        title: "Stopwatch"
        visible: false
    }
    Kirigami.Page {
        id: alarmsPage
        title: "Alarms"
        visible: false
    }

    footer: Kirigami.NavigationTabBar {
        actions: [
            Kirigami.Action {
                icon.name: "globe"
                text: "World"
                checked: worldPage.visible
                onTriggered: {
                     if (!worldPage.visible) {
                         while (pageStack.depth > 0) {
                             pageStack.pop();
                         }
                         pageStack.push(worldPage);
                    }
                }
            },
            Kirigami.Action {
                icon.name: "player-time"
                text: "Timers"
                checked: timersPage.visible
                onTriggered: {
                    if (!timersPage.visible) {
                        while (pageStack.depth > 0) {
                            pageStack.pop();
                        }
                        pageStack.push(timersPage);
                    }
                }
            },
            Kirigami.Action {
                icon.name: "chronometer"
                text: "Stopwatch"
                checked: stopwatchPage.visible
                onTriggered: {
                    if (!stopwatchPage.visible) {
                        while (pageStack.depth > 0) {
                            pageStack.pop();
                        }
                        pageStack.push(stopwatchPage);
                    }
                }
            },
            Kirigami.Action {
                icon.name: "notifications"
                text: "Alarms"
                checked: alarmsPage.visible
                onTriggered: {
                    if (!alarmsPage.visible) {
                        while (pageStack.depth > 0) {
                            pageStack.pop();
                        }
                        pageStack.push(alarmsPage);
                    }
                }
            }
        ]
    }
}
```

A [NavigationTabBar](qml-org-kde-kirigami-navigationtabbar.md) can also be combined with a [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) [SwipeView](https://doc.qt.io/qt-6/qml-qtquick-controls-swipeview.html), through which swiping between Pages becomes possible.

Example usage with a [SwipeView](https://doc.qt.io/qt-6/qml-qtquick-controls-swipeview.html):

```qml
import QtQuick
import QtQuick.Controls as QQC
import QtQuick.Layouts
import org.kde.kirigami as Kirigami

Kirigami.Page {
    title: "Clock"
    QQC.SwipeView {
        id: swipeView
        anchors.fill: parent
        clip: true
        onCurrentIndexChanged: footer.currentIndex = currentIndex
        Kirigami.Page {
            id: worldPage
            title: "World"
            QQC.Label {
                anchors.centerIn: parent
                text: "Current Page: World"
            }
        }
        Kirigami.Page {
            [...]
        }
        ...
        Kirigami.Page {
            id: alarmsPage
            title: "Alarms"
            QQC.Label {
                anchors.centerIn: parent
                text: "Current Page: Alarms"
            }
        }
    }

    footer: Kirigami.NavigationTabBar {
        actions: [
            Kirigami.Action {
                icon.name: "globe"
                text: "World"
                checked: true
                onTriggered: swipeView.currentIndex = footer.currentIndex
            },
            Kirigami.Action {
                [...]
            },
            ...
            Kirigami.Action {
                icon.name: "notifications"
                text: "Alarms"
                onTriggered: swipeView.currentIndex = footer.currentIndex
            }
        ]
    }
}
```

*See also* [NavigationTabButton](qml-org-kde-kirigami-navigationtabbutton.md)

## Property Documentation {#property-documentation}

### actions : list\<Action\> {#actions-prop}

This property holds the list of actions to be displayed in the toolbar.

If the `checked` attribute in the action is set to `true`, the tab will be highlighted/selected.

### buttonWidth : real {#buttonWidth-prop}

This property holds the calculated width that buttons on the tab bar use.

### \[read-only\] count : int {#count-prop}

This property holds the number of tab buttons.

### currentIndex : int {#currentIndex-prop}

This property holds the index of currently checked tab.

If the index set is out of bounds, or the triggered signal did not change any checked property of an action, the index will remain the same.

### \[since 6.23\] delegate : Component {#delegate-prop}

\*brief Property for the delegate component that will be instantiated inside tab bar.

This property was introduced in Qt 6.23.

### maximumContentWidth : real {#maximumContentWidth-prop}

The property holds the maximum width of the toolbar actions, before margins are added.

### \[read-only\] tabGroup : ButtonGroup {#tabGroup-prop}

This property holds the [ButtonGroup](https://doc.qt.io/qt-6/qml-qtquick-controls-buttongroup.html) used to manage the tabs.

### \[read-only\] visibleActions : list\<Action\> {#visibleActions-prop}

This property holds a subset of visible actions of the list of actions.

An action is considered visible if it is either a Kirigami.Action with `visible` property set to true, or it is a plain QQC.Action.
