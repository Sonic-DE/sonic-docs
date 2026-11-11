---
title: Setup
description: Create a new desktop widget from scratch.
source_url: https://develop.kde.org/docs/plasma/widget/setup/
source_authors: [Alexander Hau, Alexander Lohnau, Carl Schwan, Chris Holland, Christoph Dreier, Claudius Ellsel, David Edmundson, Florian Ruechel, Fushan Wen, Johannes Zarl-Zierl, Joshua Goins, Kunda Ki, Marco Martin, Mariusz Libera, Michael Pyne, Mikhail Zolotukhin, Nate Graham, Nicolas Fella, Parth Dhiman, Paul Brown, Plata Hill, Raresh Rus, Rony Bou Moujahed, Thiago Sueto, Tino Lorenz, Tobias Fella, Yaron Shahrabani, Zren (Chris Holland), ivan tkachenko, yaniss khima]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "PlasmoidItem and applets in sonic-desktop-interface and sonic-workspace-addons (DefaultCompactRepresentation.qml, kickoff, showdesktop); examples checked with qmllint"
---

# Setup

## Folder structure

To start a new widget from scratch, first create a folder for it somewhere in your coding directory (for example `~/Code/plasmoid-helloworld`).

Inside it, create another folder called `package`. Everything in `package` is what eventually gets installed to `~/.local/share/plasma/plasmoids/com.example.helloworld/`, and what we eventually zip to share online. Text editor files, build scripts, screenshots and so on can stay outside `package`.

Inside `package` is a `metadata.json` file. It describes the name of the widget, its category, and various other keys.

Inside `contents`, create the `ui` and `config` folders. `ui` holds your layout files, like `main.qml` and `configGeneral.qml`. `configGeneral.qml` is the layout of the first tab of the widget's configuration window.

The `config` folder holds `main.xml`, the schema of all the widget's saved configuration keys and values, and `config.qml`, which defines the tabs of the configuration window. Each tab opens a QML layout file (like `ui/configGeneral.qml`).

You don't *need* the three config files: `main.qml` and `metadata.json` are enough for a barebones widget.

```text
└── ~/Code/plasmoid-helloworld/
    └── package
        ├── contents
        │   ├── ui
        │   │   ├── main.qml
        │   │   └── configGeneral.qml
        │   └── config
        │       ├── config.qml
        │       └── main.xml
        └── metadata.json
```

## metadata.json

In `metadata.json`, set the `Name` of the widget.

`Icon` is the icon name associated with the widget. You can search for icon names in the `/usr/share/icons` folder, or browse them with Icon Explorer (`iconexplorer`) from [sonic-theme-sdk](https://github.com/Sonic-DE/sonic-theme-sdk).

`Id` must be a unique name, since it is used for the name of the folder the widget is installed into. Use a name like `com.example.helloworld`.

Widgets installed by the user (without root), for example from the widget explorer, go to `~/.local/share/plasma/plasmoids/`, which may not exist yet.

`Category` is the category the widget can be filtered with in the widget list.

`KPackageStructure` defines that this package is a desktop widget.

`"X-Plasma-API-Minimum-Version": "6.0"` is required: widgets without this key are assumed not to work with the current API, and aren't offered in the user interface.

```json
{
    "KPlugin": {
        "Authors": [
            {
                "Email": "myemail@example.com",
                "Name": "My Name"
            }
        ],
        "Category": "System Information",
        "Description": "A widget to take over the world!",
        "Icon": "battery",
        "Id": "com.example.helloworld",
        "Name": "Hello World",
        "Version": "1",
        "Website": "https://example.com/user/plasmoid-helloworld",
        "BugReportUrl": "https://example.com/user/plasmoid-helloworld/bugs"
    },
    "X-Plasma-API-Minimum-Version": "6.0",
    "KPackageStructure": "Plasma/Applet"
}
```

### Where a widget can be placed

Three optional keys at the top level of `metadata.json` limit where a widget goes. SonicDE's Terminal Panel and Terminal widgets use all three.

- `"NoDisplay": true` keeps the widget out of the Add Widgets list. A layout template can still add it by its `Id`.
- `"X-SonicDE-AloneInContainment": true` keeps the widget's panel or desktop to itself. While it is there, that panel offers no **Add Widgets** and no **Clone Panel**, and widgets can't be dropped onto it. Layout scripts can still add widgets.
- `"X-SonicDE-HiddenWhilePlaced"` is a list of widget `Id`s. While any of them is placed anywhere, on any screen or activity, the widget isn't offered in Add Widgets and isn't copied when its panel is cloned. List the widget's own `Id` for "one at a time"; give every member of a group the same list for "one of the group at a time". The key works the same way on layout templates (see [Layout templates](../scripting/templates.md)).

```json
{
    "KPlugin": {
        "Id": "com.example.onlyone",
        "Name": "Only One"
    },
    "X-Plasma-API-Minimum-Version": "6.0",
    "X-SonicDE-HiddenWhilePlaced": ["com.example.onlyone"]
}
```

## contents/ui/main.qml

This is the entry point. Widgets have several ways of being shown:

* In a panel, usually as just an icon that shows a popup window when clicked.
* On the desktop, as a desktop widget the user can resize. It can switch between the small "icon" view (which opens a popup) when small, and showing the contents of the popup directly when there is enough room.
* Inside another widget (a containment), like the system tray or the panel itself.
* In its own window, like an application.

The root of a widget must be a `PlasmoidItem`.

`Plasmoid.location` and `Plasmoid.formFactor` tell you how the widget is placed. `Plasmoid` is available when you `import org.kde.plasma.plasmoid`.

`compactRepresentation` and `fullRepresentation` define the layout of the small "icon" view and the full "popup" view. Both are properties of the root `PlasmoidItem`. If neither is set, the contents of the root `PlasmoidItem` are the full representation. You can change this behavior with its `preferredRepresentation` property.

If you change the compact representation, you need a [MouseArea](https://doc.qt.io/qt-6/qml-qtquick-mousearea.html) to toggle the `expanded` property of the root `PlasmoidItem`. See [DefaultCompactRepresentation.qml](https://github.com/Sonic-DE/sonic-desktop-interface/blob/master/desktoppackage/contents/applet/DefaultCompactRepresentation.qml) for an example.

`Layout.preferredWidth` defines the default width of a panel widget, or the size of the popup window (unless it is in the system tray, whose popups have a fixed size). It can also define the width of the compact "icon" view in a horizontal panel, not just the full "popup" width. The `Layout.preferredWidth` and `Layout.preferredHeight` of the compact representation scale automatically to the thickness of the panel.

`Layout.minimumWidth` defines the minimum size of a desktop widget or popup.

`width` and `height` (not `Layout.*`) define the default size of a desktop widget. Desktop widgets ignore `Layout.preferredWidth` when calculating their default size.

You can also set the tooltip contents and various other things in `main.qml`.

### Examples of main.qml

* [colorpicker](https://github.com/Sonic-DE/sonic-workspace-addons/blob/master/applets/colorpicker/qml/main.qml)
* [fifteenPuzzle](https://github.com/Sonic-DE/sonic-workspace-addons/blob/master/applets/fifteenPuzzle/qml/main.qml)

A minimal widget:

```qml
import QtQuick
import org.kde.plasma.plasmoid
import org.kde.plasma.components as PlasmaComponents

PlasmoidItem {
    PlasmaComponents.Label {
        text: "Hello World!"
    }
}
```

To show the text in the panel rather than in a popup:

```qml
import QtQuick
import org.kde.plasma.plasmoid
import org.kde.plasma.components as PlasmaComponents

PlasmoidItem {
    // Always display the full view. Never show the compact icon view
    // like it does by default when shown in the panel.
    preferredRepresentation: fullRepresentation

    fullRepresentation: PlasmaComponents.Label {
        text: "Hello World!"
    }
}
```

To set the popup size:

```qml
import QtQuick
import QtQuick.Layouts
import org.kde.kirigami as Kirigami
import org.kde.plasma.plasmoid
import org.kde.plasma.components as PlasmaComponents

PlasmoidItem {
    // Always display the compact view.
    // Never show the full popup view even if there is space for it.
    preferredRepresentation: compactRepresentation

    fullRepresentation: Item {
        Layout.minimumWidth: label.implicitWidth
        Layout.minimumHeight: label.implicitHeight
        Layout.preferredWidth: Kirigami.Units.gridUnit * 35
        Layout.preferredHeight: Kirigami.Units.gridUnit * 26

        PlasmaComponents.Label {
            id: label
            anchors.fill: parent
            text: "Hello World!"
            horizontalAlignment: Text.AlignHCenter
        }
    }
}
```
