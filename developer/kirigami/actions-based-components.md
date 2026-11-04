---
title: Actions based components
description: Kirigami's actions add functionality to components.
source_url: https://develop.kde.org/docs/getting-started/kirigami/components-actions/
source_authors: [Carl Schwan, Claudio Cambra, Joshua Wug, Mikhail Zolotukhin, Nicolas Fella, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "Kirigami Action.qml, DisplayHint, Page.qml, ContextDrawer.qml, GlobalDrawer.qml, ActionTextField.qml, SwipeListItem.qml, ActionToolBar.qml and Card.qml; sonic-theme-sdk Icon Explorer; snippets run with the qml tool in desktop and mobile mode"
---

# Actions based components

## Actions

A [Kirigami.Action](/docs/api/kirigami/qml-org-kde-kirigami-action) is a clickable action whose appearance depends on where it is added. Typically it is a button with an icon and text.

Use them to give your application easy-to-reach actions that are essential to its functionality.

> **Note:** Kirigami actions inherit from [QtQuick.Controls.Action](https://doc.qt.io/qt-6/qml-qtquick-controls-action.html) and can be assigned shortcuts.

Like [Qt Quick Controls actions](https://doc.qt.io/qt-6/qml-qtquick-controls-action.html), they can be assigned to menu items and toolbar buttons, but also to many other Kirigami components.

```qml
import org.kde.kirigami as Kirigami

Kirigami.Action {
    id: copyAction
    text: i18n("Copy")
    icon.name: "edit-copy"
    shortcut: StandardKey.Copy
    onTriggered: {
        // ...
    }
}
```

> **Note:** The [icon.name](https://doc.qt.io/qt-6/qml-qtquick-controls-action.html#icon.name-prop) property takes names of system-wide icons following the FreeDesktop specification. You can browse these icons and their names with Icon Explorer (`iconexplorer`), which comes with [sonic-theme-sdk](https://github.com/Sonic-DE/sonic-theme-sdk), or in [FreeDesktop's icon naming specification](https://specifications.freedesktop.org/icon-naming-spec).

One feature Kirigami actions offer on top of Qt Quick actions is nesting:

```qml
import org.kde.kirigami as Kirigami

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
}
```

Kirigami actions can also give the items that use them hints on how to display them. These are mostly handled by the [displayHint](/docs/api/kirigami/qml-org-kde-kirigami-action#displayHint-prop) and [displayComponent](/docs/api/kirigami/qml-org-kde-kirigami-action#displayComponent-prop) properties.

The item respects these properties where it can. For example, the following action is displayed as a [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html), and the item tries its best to keep it visible as long as possible.

```qml
import QtQuick.Controls
import org.kde.kirigami as Kirigami

Kirigami.Action {
    text: "Search"
    icon.name: "search"

    displayComponent: TextField { }

    displayHint: Kirigami.DisplayHint.KeepVisible
}
```

## Using actions in other components

As mentioned in the [introduction to actions](actions.md), Kirigami actions are [contextual](actions.md#actions-are-contextual): they show up in different places depending on where you put them. They also have different representations on the desktop and on mobile.

### Page

A [Kirigami.Page](/docs/api/kirigami/qml-org-kde-kirigami-page) shows its actions on the right of the top header in desktop mode, and in a footer toolbar in mobile mode.

```qml
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Actions Demo"
    width: 600
    height: 600

    globalDrawer: Kirigami.GlobalDrawer {}
    contextDrawer: Kirigami.ContextDrawer {}

    pageStack.initialPage: Kirigami.Page {
        title: "Demo"

        actions: [
            Kirigami.Action {
                icon.name: "go-home"
                onTriggered: showPassiveNotification("Main action triggered")
            },
            Kirigami.Action {
                icon.name: "go-previous"
                onTriggered: showPassiveNotification("Left action triggered")
            },
            Kirigami.Action {
                icon.name: "go-next"
                onTriggered: showPassiveNotification("Right action triggered")
            },
            Kirigami.Action {
                text: "Contextual Action 1"
                icon.name: "bookmarks"
                onTriggered: showPassiveNotification("Contextual action 1 clicked")
            },
            Kirigami.Action {
                text: "Contextual Action 2"
                icon.name: "folder"
                enabled: false
            }
        ]
    }
}
```

### Global drawer

The [Kirigami.GlobalDrawer](/docs/api/kirigami/qml-org-kde-kirigami-globaldrawer) is a menu-like sidebar that provides action-based navigation for your application. This is where nested actions are useful, because they create nested navigation:

```qml
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Actions Demo"
    globalDrawer: Kirigami.GlobalDrawer {
        title: "Demo"
        titleIcon: "applications-graphics"
        actions: [
            Kirigami.Action {
                text: "View"
                icon.name: "view-list-icons"
                Kirigami.Action {
                    text: "View Action 1"
                    onTriggered: showPassiveNotification("View Action 1 clicked")
                }
                Kirigami.Action {
                    text: "View Action 2"
                    onTriggered: showPassiveNotification("View Action 2 clicked")
                }
            },
            Kirigami.Action {
                text: "Action 1"
                onTriggered: showPassiveNotification("Action 1 clicked")
            },
            Kirigami.Action {
                text: "Action 2"
                onTriggered: showPassiveNotification("Action 2 clicked")
            }
        ]
    }
    //...
}
```

You can read more about global drawers in the [page about drawers](drawers.md#global-drawer).

### Context drawer

A [Kirigami.ContextDrawer](/docs/api/kirigami/qml-org-kde-kirigami-contextdrawer) shows the actions you set in its own [actions](/docs/api/kirigami/qml-org-kde-kirigami-contextdrawer#actions-prop) property, behind a button with an overflow-menu icon at the edge of the window: in the toolbar if there is one, otherwise at the bottom. It is meant for actions that are only relevant to a specific page. The context drawer is disabled while the page's toolbar uses the ToolBar style, as it does on the desktop. You can read more about it in the [page about drawers](drawers.md).

### ActionTextFields

A [Kirigami.ActionTextField](/docs/api/kirigami/qml-org-kde-kirigami-actiontextfield) adds contextual actions to a text field, for example to clear the text or to search for it.

```qml
Kirigami.ActionTextField {
    id: searchField
    rightActions: [
        Kirigami.Action {
            icon.name: "edit-clear"
            visible: searchField.text !== ""
            onTriggered: {
                searchField.text = ""
                searchField.accepted()
            }
        }
    ]
}
```

This example creates a "clear" button for a search field that is only visible when text has been entered.

> **Note:** You should rarely use an ActionTextField directly. [SearchField](/docs/api/kirigami/qml-org-kde-kirigami-searchfield) and [PasswordField](/docs/api/kirigami/qml-org-kde-kirigami-passwordfield) both inherit from [ActionTextField](/docs/api/kirigami/qml-org-kde-kirigami-actiontextfield) and probably cover your use case.

### SwipeListItem

A [Kirigami.SwipeListItem](/docs/api/kirigami/qml-org-kde-kirigami-swipelistitem) is a delegate meant to support extra actions, shown at its right end. On the desktop its actions are always shown. In mobile mode they are hidden, and on a touch screen you uncover them by dragging the item by its handle.

```qml
ListView {
    model: myModel
    delegate: Kirigami.SwipeListItem {
        Controls.Label {
            text: model.text
        }
        actions: [
            Kirigami.Action {
                icon.name: "document-decrypt"
                onTriggered: print("Action 1 clicked")
            },
            Kirigami.Action {
                icon.name: model.action2Icon
                onTriggered: {
                    // do something
                }
            }
        ]
    }
}
```

### ActionToolBar

A [Kirigami.ActionToolBar](/docs/api/kirigami/qml-org-kde-kirigami-actiontoolbar) is a toolbar built from a list of actions. By default, each action that fits in the toolbar is shown as a [ToolButton](https://doc.qt.io/qt-6/qml-qtquick-controls-toolbutton.html), and those that don't fit are moved into an overflow menu at the end of the toolbar.

Like [ActionTextField](/docs/api/kirigami/qml-org-kde-kirigami-actiontextfield), you may not need [ActionToolBar](/docs/api/kirigami/qml-org-kde-kirigami-actiontoolbar) directly, as page headers and cards use it to display their actions.

```qml
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Actions Demo"
    width: 350
    height: 350
    header: Kirigami.ActionToolBar {
        actions: [
            Kirigami.Action {
                text: i18n("View Action 1")
                onTriggered: showPassiveNotification(i18n("View Action 1 clicked"))
            },
            Kirigami.Action {
                text: i18n("View Action 2")
                onTriggered: showPassiveNotification(i18n("View Action 2 clicked"))
            },
            Kirigami.Action {
                text: i18n("Action 1")
                onTriggered: showPassiveNotification(i18n("Action 1 clicked"))
            },
            Kirigami.Action {
                text: i18n("Action 2")
                onTriggered: showPassiveNotification(i18n("Action 2 clicked"))
            }
        ]
    }
}
```

You can read more about [ActionToolBar](/docs/api/kirigami/qml-org-kde-kirigami-actiontoolbar) in its [own page](action-toolbars.md).

### Cards

A [Kirigami.Card](/docs/api/kirigami/qml-org-kde-kirigami-card) displays a collection of information or actions together. Actions go in its [actions](/docs/api/kirigami/qml-org-kde-kirigami-card#actions-prop) property, as with the previous components.

```qml
Kirigami.Card {
    actions: [
        Kirigami.Action {
            text: qsTr("Action1")
            icon.name: "add-placemark"
        },
        Kirigami.Action {
            text: qsTr("Action2")
            icon.name: "address-book-new-symbolic"
        },
        // ...
    ]
    banner {
        source: "../banner.jpg"
        title: "Title Alignment"
        titleAlignment: Qt.AlignLeft | Qt.AlignBottom
    }
    contentItem: Controls.Label {
        wrapMode: Text.WordWrap
        text: "My Text"
    }
}
```

For more information, see the [page about cards](cards.md).
