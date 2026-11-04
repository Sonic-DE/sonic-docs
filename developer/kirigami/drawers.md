---
title: Drawers
description: Drawers give quick access to the controls and pages of your application.
source_url: https://develop.kde.org/docs/getting-started/kirigami/components-drawers/
source_authors: [Carl Schwan, Claudio Cambra, Jeongu Kim, Mikhail Zolotukhin, Nicolas Fella, Thiago Sueto, Tobias Fella, Yuri Chornoivan]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "Kirigami GlobalDrawer.qml, ContextDrawer.qml, OverlayDrawer template and Page.qml; examples run with the qml tool in desktop and mobile mode (isMenu, context drawer state, inline drawer state)"
---

# Drawers

Drawers are panels that slide out of the sides of the application window. They can hold interactive elements such as Kirigami actions, buttons, text and more.

Drawers come in different types, shapes and forms. This page goes over each type and gives an overview of its characteristics.

## Global drawer

The global drawer is a standard feature of mobile applications and is sometimes found in their desktop versions too. It contains the application's main menu: any functions that aren't specific to the current page but still matter for general navigation or interaction within the application.

It is opened by tapping the hamburger menu, or by swiping from the left edge to the middle of the screen in left-to-right mode (from the right edge in right-to-left mode).

[Kirigami.GlobalDrawer](/docs/api/kirigami/qml-org-kde-kirigami-globaldrawer) components create such drawers. They are set as the [globalDrawer](/docs/api/kirigami/qml-org-kde-kirigami-abstractapplicationwindow#globalDrawer-prop) property of the [Kirigami.ApplicationWindow](/docs/api/kirigami/qml-org-kde-kirigami-applicationwindow) at the base of our Kirigami application.

```qml
import QtQuick
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Drawers App"
    width: 600
    height: 600
    pageStack.initialPage: Kirigami.Page { /* Page code here... */ }

    globalDrawer: Kirigami.GlobalDrawer {
        title: "Global Drawer"
        titleIcon: "applications-graphics"
        actions: [
            Kirigami.Action {
                text: "Kirigami Action 1"
                icon.name: "user-home-symbolic"
                onTriggered: showPassiveNotification("Action 1 clicked")
            },
            Kirigami.Action {
                text: "Kirigami Action 2"
                icon.name: "settings-configure-symbolic"
                onTriggered: showPassiveNotification("Action 2 clicked")
            },
            Kirigami.Action {
                text: i18n("Quit")
                icon.name: "application-exit-symbolic"
                shortcut: StandardKey.Quit
                onTriggered: Qt.quit()
            }
        ]
    }
}
```

The [titleIcon](/docs/api/kirigami/qml-org-kde-kirigami-globaldrawer#titleIcon-prop) property takes names of system-wide icons following the FreeDesktop specification. You can browse these icons and their names with Icon Explorer (`iconexplorer`), which comes with [sonic-theme-sdk](https://github.com/Sonic-DE/sonic-theme-sdk), or in [FreeDesktop's icon naming specification](https://specifications.freedesktop.org/icon-naming-spec).

### Header

A header places sticky components at the top of your global drawer. The header stays in place even when nested Kirigami actions replace the current layer of the global drawer, and when the drawer's contents scroll.

Set your header component with the global drawer's [header](/docs/api/kirigami/qml-org-kde-kirigami-globaldrawer#header-prop) property; it replaces the global drawer's title. This is useful for adding a [Kirigami.SearchField](/docs/api/kirigami/qml-org-kde-kirigami-searchfield), for example:

```qml
import QtQuick
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Drawers App"
    width: 600
    height: 600
    pageStack.initialPage: Kirigami.Page { /* Page code here... */ }

    globalDrawer: Kirigami.GlobalDrawer {
        title: "Global Drawer with searchfield (not visible)"

        header: Kirigami.SearchField {
                id: searchField
        }

        actions: [
            Kirigami.Action {
                text: "Kirigami Action 1"
                icon.name: "user-home-symbolic"
                onTriggered: showPassiveNotification("Action 1 clicked")
            },
            Kirigami.Action {
                text: "Kirigami Action 2"
                icon.name: "settings-configure-symbolic"
                onTriggered: showPassiveNotification("Action 2 clicked")
            },
            Kirigami.Action {
                text: i18n("Quit")
                icon.name: "application-exit-symbolic"
                shortcut: StandardKey.Quit
                onTriggered: Qt.quit()
            }
        ]
    }
}
```

### Adapting for the desktop

Panel-style global drawers are useful in mobile environments, but they can be too large on the desktop, especially when the application has few actions.

Kirigami global drawers have an [isMenu](/docs/api/kirigami/qml-org-kde-kirigami-globaldrawer#isMenu-prop) property for this. When it is `true`, the drawer becomes a more traditional menu. This applies in mobile mode too; to get a menu only on the desktop, set it to `!Kirigami.Settings.isMobile`.

In menu mode, headers and banners aren't visible.

```qml
globalDrawer: Kirigami.GlobalDrawer {
    isMenu: true

    actions: [
        // Kirigami Actions here...
    ]
}
```

## Context drawers

While a [Kirigami.GlobalDrawer](/docs/api/kirigami/qml-org-kde-kirigami-globaldrawer) displays global actions available throughout your application, a [Kirigami.ContextDrawer](/docs/api/kirigami/qml-org-kde-kirigami-contextdrawer) is meant for actions that are only relevant in certain contexts, usually on separate [pages](pages.md). It is set as the [contextDrawer](/docs/api/kirigami/qml-org-kde-kirigami-abstractapplicationwindow#contextDrawer-prop) property of the window.

A context drawer shows the actions set in its own [actions](/docs/api/kirigami/qml-org-kde-kirigami-contextdrawer#actions-prop) property. It slides out of the right edge in left-to-right mode (the left edge in right-to-left mode): tap the button with the overflow-menu icon, or swipe from that edge to the middle of the screen.

How it behaves depends on whether the application runs on mobile or on the desktop:

- On the desktop, the page toolbar uses the ToolBar style and the context drawer is disabled. Put page-specific actions in the page's [actions](/docs/api/kirigami/qml-org-kde-kirigami-page#actions-prop) instead: they show up in the top toolbar, and the ones that don't fit move into its overflow menu.
- On mobile, the context drawer is available whenever it has actions. The page's own actions appear in a toolbar at the bottom of the page.

```qml
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Drawers App"
    height: 600
    width: 1200
    minimumWidth: 500

    globalDrawer: Kirigami.GlobalDrawer {}
    contextDrawer: Kirigami.ContextDrawer {
        actions: [
            Kirigami.Action {
                text: "Contextual Action 1"
                icon.name: "media-playback-start"
            },
            Kirigami.Action {
                text: "Contextual Action 2"
                icon.name: "media-playback-stop"
            }
        ]
    }

    pageStack.initialPage: [ emptyPage, contextDrawerPage ]

    Kirigami.Page {
        title: "Empty page"
        id: emptyPage
    }

    Kirigami.Page {
        id: contextDrawerPage
        title: "Context Drawer page"
    }
}
```

## Modal and inline drawers

Kirigami offers two more types of drawers, modal drawers and inline drawers. They are quite similar: both span the whole width or height of the application and can be placed on the edges of the window. They react differently to user interaction, though.

- Modal drawers are hidden by default and darken the rest of the application; clicking a darkened area dismisses them.
- Inline drawers are shown by default, let the user keep interacting with the rest of the application without being dismissed, and don't darken other areas.

This kind of drawer is open-ended and flexible, but generally you may want it when a small list of options should appear on a long press or right click.

The two are so similar because they are, in fact, the same Kirigami component: [Kirigami.OverlayDrawer](/docs/api/kirigami/qml-org-kde-kirigami-overlaydrawer). Here are a few important inherited properties of this component to keep in mind:

- [Popup.modal](https://doc.qt.io/qt-6/qml-qtquick-controls-popup.html#modal-prop) makes the drawer modal or inline, depending on its boolean value.
- [Drawer.edge](https://doc.qt.io/qt-6/qml-qtquick-controls-drawer.html#edge-prop) sets the edge of the application window the drawer appears on. Its options are part of the [Edge enum](https://doc.qt.io/qt-6/qt.html#Edge-enum): `Qt.TopEdge`, `Qt.RightEdge`, `Qt.BottomEdge` and `Qt.LeftEdge`.
- [Popup.contentItem](https://doc.qt.io/qt-6/qml-qtquick-controls-popup.html#contentItem-prop) contains the component that forms the content of your drawer.

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Drawers App"
    width: 400
    height: 600
    pageStack.initialPage: Kirigami.Page {
        title: "OverlayDrawer at the bottom"
        actions: [
            Kirigami.Action {
                text: "Open bottomDrawer"
                onTriggered: bottomDrawer.open()
            }
        ]
        Kirigami.OverlayDrawer {
            id: bottomDrawer
            edge: Qt.BottomEdge
            // Set modal to false to make this drawer inline!
            modal: true

            contentItem: RowLayout {
                Controls.Label {
                    Layout.fillWidth: true
                    text: "Say hello to my little drawer!"
                }
                Controls.Button {
                    text: "Close"
                    onClicked: bottomDrawer.close()
                }
            }
        }
    }
}
```
