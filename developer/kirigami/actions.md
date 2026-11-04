---
title: Adding actions
description: Kirigami actions make the application more useful.
source_url: https://develop.kde.org/docs/getting-started/kirigami/introduction-actions/
source_authors: [Alessio Mattiazzi, Antti Savolainen, Carl Schwan, Claudio Cambra, Justin Kourie, Justin Zobel, Mikhail Zolotukhin, Nicolas Fella, Phu Nguyen, Swapnil Tripathi, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-quick-ui (Action.qml derives from QQC2.Action, GlobalDrawer.isMenu, Page.qml actions and ToolBarPageFooter), sonic-silver-icons, sonic-theme-sdk (iconexplorer); the example was built into the tutorial application and loaded offscreen, in desktop and mobile mode, without QML errors
---

# Adding actions

## Recap

So far we built a simple application that shows cards, but the user can't add new cards yet.

This step looks at Kirigami actions, which add interactivity to the application in a consistent, fast and accessible way.

## Actions

A [Kirigami.Action](/docs/api/kirigami/qml-org-kde-kirigami-action) is a user interface action. Actions give applications easy-to-reach commands for their essential functions.

If you have used Kirigami applications, you have used Kirigami actions, for example the buttons with icons to the right of a page's title. Actions can be shown in several ways and can do all kinds of things.

## Adding countdowns

A countdown application isn't much use if you can't add countdowns. Let's create an action for that.

```qml
pageStack.initialPage: Kirigami.ScrollablePage {
    // Other page properties...
    actions: [
        Kirigami.Action {
            id: addAction
            icon.name: "list-add-symbolic"
            text: i18nc("@action:button", "Add kountdown")
            onTriggered: kountdownModel.append({
                name: "Kirigami Action added card!",
                description: "Congratulations, your Kirigami Action works!",
                date: 1000
            })
        }
    ]
    // ...
}
```

We put the [Kirigami.Action](/docs/api/kirigami/qml-org-kde-kirigami-action) in our main page from the previous steps. We could add more actions to the page if we wanted (and even nest actions in actions!).

The brackets `[]` work like [JavaScript arrays](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array): they hold one or more things, separated by commas:

```qml
// General JavaScript array of components:
variable: [ component1, component2 ]
// Passing an array of Kirigami actions to QML:
actions: [ Kirigami.Action {}, Kirigami.Action {} ]
```

`id` and `text` are familiar from the previous steps. More interesting is the [icon](https://doc.qt.io/qt-6/qml-qtquick-controls-action.html#icon-prop) property, inherited from Qt Quick Controls' Action (Kirigami.Action derives from it): an object with several properties for the action's icon. To use an icon from the icon theme, just set its name, `icon.name`.

> **Finding icons:** SonicDE's Icon Explorer (`iconexplorer`, in `sonic-theme-sdk`) shows all the icons you can use: how they look in the installed icon themes, at different sizes, and more. Most icon names follow the freedesktop.org [Icon Naming Specification](https://specifications.freedesktop.org/icon-naming-spec/latest/), which lists the names available on every desktop. SonicDE's Silver icon theme has both icons used here.

The [onTriggered](https://doc.qt.io/qt-6/qml-qtquick-controls-action.html#triggered-signal) signal handler is the most important part: it is what the action does when used. Here it calls [kountdownModel.append()](https://doc.qt.io/qt-6/qml-qtqml-models-listmodel.html#append-method) of the `kountdownModel` from the previous step, which adds an element to our list model. We give it an object (in curly braces `{}`) with the properties of a countdown (`name`, `description` and the placeholder `date`).

Each time you click the "Add kountdown" button at the top right, a new card is added.

## Global drawer

Next, a [Kirigami.GlobalDrawer](/docs/api/kirigami/qml-org-kde-kirigami-globaldrawer). It appears as a [hamburger menu](https://en.wikipedia.org/wiki/Hamburger_button). By default it opens a sidebar, which is especially useful on mobile, where the user can swipe it in from the side of the screen. Global drawers are good for navigation and actions that concern the whole application. We create a simple one with a "Quit" button:

```qml
Kirigami.ApplicationWindow {
    id: root
    // Other window properties...
    globalDrawer: Kirigami.GlobalDrawer {
        isMenu: true
        actions: [
            Kirigami.Action {
                text: i18n("Quit")
                icon.name: "application-exit-symbolic"
                shortcut: StandardKey.Quit
                onTriggered: Qt.quit()
            }
        ]
    }
    // ...
}
```

The global drawer goes in the application window. The main property is [GlobalDrawer.actions](/docs/api/kirigami/qml-org-kde-kirigami-globaldrawer#actions-prop), a list of [Kirigami.Action](/docs/api/kirigami/qml-org-kde-kirigami-action)s. This action has a fitting icon and calls [Qt.quit()](https://doc.qt.io/qt-6/qml-qtqml-qt.html#quit-method) when triggered, which closes the application.

Since our global drawer is simple for now, we set [GlobalDrawer.isMenu](/docs/api/kirigami/qml-org-kde-kirigami-globaldrawer#isMenu-prop) to `true`. It is then shown as a normal application menu, which takes less space than the default drawer pane.

> **Tip:** [Actions based components](actions-based-components.md) explains Kirigami actions and their uses in more detail.

## Actions are contextual

Where you put Kirigami actions matters. Actions added to a [Kirigami.Page](/docs/api/kirigami/qml-org-kde-kirigami-page), [Kirigami.ScrollablePage](/docs/api/kirigami/qml-org-kde-kirigami-scrollablepage) or another page type appear on the right of the page header on the desktop. In mobile mode they appear in a toolbar at the bottom of the page.

Actions added to a [Kirigami.GlobalDrawer](/docs/api/kirigami/qml-org-kde-kirigami-globaldrawer) appear in the drawer or menu.

Other components that show actions in their own way:

- [Kirigami.ContextDrawer](/docs/api/kirigami/qml-org-kde-kirigami-contextdrawer): see [Drawers](drawers.md)
- [Kirigami.AbstractCard](/docs/api/kirigami/qml-org-kde-kirigami-abstractcard) and the types derived from it: see [Cards](cards.md)
- [Kirigami.Dialog](/docs/api/kirigami/qml-org-kde-kirigami-dialogs-dialog) and the types derived from it: see [Dialog types](dialogs.md)
- [Kirigami.ActionToolBar](/docs/api/kirigami/qml-org-kde-kirigami-actiontoolbar): see [Action toolbars](action-toolbars.md)

And other Kirigami components.

## Our application so far

`Main.qml`:

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    id: root

    width: 400
    height: 300

    title: i18nc("@title:window", "Day Kountdown")

    // Global drawer element with app-wide actions
    globalDrawer: Kirigami.GlobalDrawer {
        // Makes drawer a small menu rather than sliding pane
        isMenu: true
        actions: [
            Kirigami.Action {
                text: i18n("Quit")
                icon.name: "application-exit-symbolic"
                shortcut: StandardKey.Quit
                onTriggered: Qt.quit()
            }
        ]
    }

    ListModel {
        id: kountdownModel
        ListElement {
            name: "Dog birthday!!"
            description: "Big doggo birthday blowout."
            date: 100
        }
    }

    Component {
        id: kountdownDelegate
        Kirigami.AbstractCard {
            contentItem: Item {
                implicitWidth: delegateLayout.implicitWidth
                implicitHeight: delegateLayout.implicitHeight
                GridLayout {
                    id: delegateLayout
                    anchors {
                        left: parent.left
                        top: parent.top
                        right: parent.right
                    }
                    rowSpacing: Kirigami.Units.largeSpacing
                    columnSpacing: Kirigami.Units.largeSpacing
                    columns: root.wideScreen ? 4 : 2

                    Kirigami.Heading {
                        Layout.fillHeight: true
                        level: 1
                        text: date
                    }

                    ColumnLayout {
                        Kirigami.Heading {
                            Layout.fillWidth: true
                            level: 2
                            text: name
                        }
                        Kirigami.Separator {
                            Layout.fillWidth: true
                            visible: description.length > 0
                        }
                        Controls.Label {
                            Layout.fillWidth: true
                            wrapMode: Text.WordWrap
                            text: description
                            visible: description.length > 0
                        }
                    }
                    Controls.Button {
                        Layout.alignment: Qt.AlignRight
                        Layout.columnSpan: 2
                        text: i18n("Edit")
                    }
                }
            }
        }
    }

    pageStack.initialPage: Kirigami.ScrollablePage {
        title: i18nc("@title", "Kountdown")

        // Kirigami.Action encapsulates a UI action. Inherits from Controls.Action
        actions: [
            Kirigami.Action {
                id: addAction
                // Name of icon associated with the action
                icon.name: "list-add-symbolic"
                // Action text, i18n function returns translated string
                text: i18nc("@action:button", "Add kountdown")
                // What to do when triggering the action
                onTriggered: kountdownModel.append({
                    name: "Kirigami Action added card!",
                    description: "Congratulations, your Kirigami Action works!",
                    date: 1000
                })
            }
        ]

        Kirigami.CardsListView {
            id: cardsView
            model: kountdownModel
            delegate: kountdownDelegate
        }
    }
}
```
