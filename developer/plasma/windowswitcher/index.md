---
title: Create a custom task switcher
description: Style the Alt+Tab task switcher with QML layouts.
source_url: https://develop.kde.org/docs/plasma/windowswitcher/
source_authors: [Carl Schwan, Martin Gräßlin, Mikhail Zolotukhin]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "SwitcherItem, ClientModel, tabboxhandler and the windowswitcher package structure in sonic-win; thumbnail_grid in sonic-win and the switchers in sonic-workspace-addons. Read from code; no custom switcher was run."
---

# Create a custom task switcher

The task switcher (`Alt+Tab`) can be styled with layouts written in QML. The window manager supports several switchers and exchanges the loaded layout at runtime. The underlying model is recreated each time the switcher is opened, and some properties can change with the screen and settings, so the QML loader sets properties on your component if they are available.

The QML API is available with:

```qml
import org.kde.kwin as KWin
```

## KWin.TabBoxSwitcher

`KWin.TabBoxSwitcher` is the base element of a task switcher and has no visual representation. Its properties are:

- `QAbstractItemModel *model` (read-only): the model listing all windows
- `QRect screenGeometry` (read-only): the height, width, x and y position of the current screen, for restraining the switcher's size and position
- `bool visible`: whether the switcher is currently visible
- `bool allDesktops` (read-only): whether the model includes windows from all desktops or only the current one. Use it, for example, to hide the desktop of a window when only the current desktop is shown. Don't use it to filter the list, which the model does.
- `int currentIndex`: the selected item in the model. Updating it switches to that window.
- `bool noModifierGrab` (read-only), `bool compositing` (read-only), `bool automaticallyHide`
- `QObject *item`: the item to show

## Model

The `model` is a standard `QAbstractItemModel`, usable in a `ListView` or `Repeater`. It provides these roles:

- `string caption`: the window title
- `bool minimized`: whether the window is minimized
- `string desktopName`: the name of the desktop the window is on
- `ulonglong windowId`: the window's ID
- `bool closeable`: whether the window can be closed
- `string icon`: the icon for the window

## Thumbnails

The window manager provides a QML component that renders a live thumbnail of a window. It is called `WindowThumbnail`, and takes the window's ID in its `wId` property. The bundled switcher puts it in a container item, as this example does:

```qml
import QtQuick
import org.kde.kwin as KWin

KWin.TabBoxSwitcher {
    id: tabBox
    currentIndex: thumbnailListView.currentIndex

    ListView {
        id: thumbnailListView
        model: tabBox.model
        delegate: Item {
            width: 200
            height: 200

            required property var windowId

            KWin.WindowThumbnail {
                anchors.fill: parent
                wId: parent.windowId
            }
        }
    }
}
```

## Installation

A switcher is a package of type `KWin/WindowSwitcher`, with its layout in `contents/ui/main.qml`. Install it with:

```bash
kpackagetool6 --type=KWin/WindowSwitcher -i /path/to/package
```

It goes in `~/.local/share/kwin/tabbox/`.

Examples:

- [`thumbnail_grid`](https://github.com/Sonic-DE/sonic-win/tree/master/src/tabbox/switchers/thumbnail_grid), which ships with SonicWin
- [`big_icons`, `compact`, `coverswitch`, `flipswitch` and `sidebar`](https://github.com/Sonic-DE/sonic-workspace-addons/tree/master/kwin/windowswitchers), in `sonic-workspace-addons`

A switcher can also be bundled in a global theme, as `contents/windowswitcher/WindowSwitcher.qml`.
