---
title: Action toolbars
description: Create your own customizable toolbars with the ActionToolBar component.
source_url: https://develop.kde.org/docs/getting-started/kirigami/components-actiontoolbar/
source_authors: [Carl Schwan, Claudio Cambra, Jeongu Kim, Mikhail Zolotukhin, Nicolas Fella, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "Kirigami ActionToolBar.qml, examples run with the qml tool plus an overflow check at two window widths"
---

# Action toolbars

Kirigami pages make it easy to place a set of actions in the page header, but sometimes you want something more flexible.

Kirigami provides the [Kirigami.ActionToolBar](/docs/api/kirigami/qml-org-kde-kirigami-actiontoolbar) component. It displays a list of [Kirigami.Action](/docs/api/kirigami/qml-org-kde-kirigami-action) objects, as many of them as fit, and provides an overflow menu for the ones that don't. The ActionToolBar is dynamic: it moves actions in and out of the overflow menu depending on the space available to it.

> **Note:** This page assumes you are familiar with [Kirigami.Action](/docs/api/kirigami/qml-org-kde-kirigami-action) objects. If you aren't, you can learn all about them in the beginner tutorial or on [their own page](actions-based-components.md).

## Creating our first ActionToolBar

The layout and location of your [Kirigami.ActionToolBar](/docs/api/kirigami/qml-org-kde-kirigami-actiontoolbar) are up to you, but for user-friendliness it's usually a good idea to stick to UI conventions: put your toolbar near the top or bottom of your page and let it span the width.

Like most other components that hold actions, [Kirigami.ActionToolBar](/docs/api/kirigami/qml-org-kde-kirigami-actiontoolbar) has an [actions](/docs/api/kirigami/qml-org-kde-kirigami-actiontoolbar#actions-prop) property, to which we can assign an array of [Kirigami.Action](/docs/api/kirigami/qml-org-kde-kirigami-action) components.

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    id: root

    title: "ActionToolBar App"
    width: 600
    height: 400

    pageStack.initialPage: Kirigami.Page {
        Kirigami.ActionToolBar {
            anchors.left: parent.left
            anchors.right: parent.right

            actions: [
                Kirigami.Action {
                    text: "Beep"
                    icon.name: "notifications"
                    onTriggered: showPassiveNotification("BEEP!")
                },
                Kirigami.Action {
                    text: "Action Menu"
                    icon.name: "overflow-menu"

                    Kirigami.Action {
                        text: "Deet";
                        icon.name: "notifications"
                        onTriggered: showPassiveNotification("DEET!")
                    }
                    Kirigami.Action {
                        text: "Doot";
                        icon.name: "notifications"
                        onTriggered: showPassiveNotification("DOOT!")
                    }
                },
                Kirigami.Action {
                    icon.name: "search"
                    displayComponent: Kirigami.SearchField { }
                }
            ]
        }
    }
}
```

With enough space, all the actions are shown in the toolbar; when the window gets narrower, the ones that don't fit move into the overflow menu.

### Alignment

By default, the actions in a [Kirigami.ActionToolBar](/docs/api/kirigami/qml-org-kde-kirigami-actiontoolbar) are aligned to the left. That isn't always what you want, and you can change it with the [alignment](/docs/api/kirigami/qml-org-kde-kirigami-actiontoolbar#alignment-prop) property. It accepts a range of values, but the three most relevant ones are `Qt.AlignLeft`, `Qt.AlignCenter` and `Qt.AlignRight` (which deal with [horizontal alignment](https://doc.qt.io/qt-6/qt.html#AlignmentFlag-enum)).

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    id: root

    title: "ActionToolBar App"
    width: 600
    height: 400

    pageStack.initialPage: Kirigami.Page {
        Controls.GroupBox {
            anchors.left: parent.left
            anchors.right: parent.right

            Kirigami.ActionToolBar {
                anchors.fill: parent

                alignment: Qt.AlignCenter

                actions: [
                    Kirigami.Action {
                        text: "Beep"
                        icon.name: "notifications"
                        onTriggered: showPassiveNotification("BEEP!")
                    }
                ]
            }
        }
    }
}
```
