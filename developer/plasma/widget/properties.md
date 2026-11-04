---
title: Widget properties
description: A rundown of the QML properties of a widget.
source_url: https://develop.kde.org/docs/plasma/widget/properties/
source_authors: [Alexander Hau, Alexander Lohnau, Carl Schwan, Chris Holland, Christoph Dreier, Claudius Ellsel, David Edmundson, Florian Ruechel, Fushan Wen, Johannes Zarl-Zierl, Joshua Goins, Kunda Ki, Marco Martin, Mariusz Libera, Michael Pyne, Mikhail Zolotukhin, Nate Graham, Nicolas Fella, Parth Dhiman, Paul Brown, Plata Hill, Raresh Rus, Rony Bou Moujahed, Thiago Sueto, Tino Lorenz, Tobias Fella, Yaron Shahrabani, Zren (Chris Holland), ivan tkachenko, yaniss khima]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "Q_PROPERTY lists of Plasma::Applet, Plasma::Containment, PlasmaQuick::AppletQuickItem and PlasmoidItem; plasma.h background hints; the system tray's metadata keys; metadata.json of shipped applets; config file name in sonic-workspace/shell; examples checked with qmllint"
---

# Widget properties

## Two sets of properties

Since Plasma 6, a widget's properties are split in two (see [Porting widgets to KF6](porting-kf6.md)):

- The root [`PlasmoidItem`](/docs/api/plasmaquick/qml-org-kde-plasma-plasmoid-plasmoiditem) has the properties specific to Qt Quick, such as its representations. Set them directly on the root item.
- The `Plasmoid` attached property, available when you `import org.kde.plasma.plasmoid`, is the underlying applet. It has properties such as `icon`, `title` and `configuration`.

Inside the root item's properties, `plasmoid` (lowercase) also points to the applet.

```qml
import QtQuick
import org.kde.plasma.components as PlasmaComponents
import org.kde.plasma.plasmoid

PlasmoidItem {
    id: widget
    Plasmoid.icon: "starred-symbolic"

    fullRepresentation: PlasmaComponents.Label {
        text: Plasmoid.icon
    }
}
```

### PlasmoidItem properties

| Property | Type | Notes |
| --- | --- | --- |
| `compactRepresentation` | `Component` | The small "icon" view of the widget, shown in the panel. See [below](#compactrepresentation). |
| `compactRepresentationItem` | `Item` | The instance of the `compactRepresentation` component. May be `null` if it isn't visible. |
| `fullRepresentation` | `Component` | The full "popup" view of the widget. See [below](#fullrepresentation). |
| `fullRepresentationItem` | `Item` | The instance of the `fullRepresentation` component. |
| `preloadFullRepresentation` | `bool` | Load the full representation without waiting for it to be shown. |
| `preferredRepresentation` | `Component` | Force a representation, for example `fullRepresentation`. |
| `switchWidth`, `switchHeight` | `int` | With more room than this, the full representation is shown directly. |
| `expanded` | `bool` | Whether the full representation is shown. |
| `activationTogglesExpanded` | `bool` | Whether the keyboard shortcut toggles `expanded`. |
| `expandedOnDragHover` | `bool` | Whether dragging something over the widget expands it. |
| `hideOnWindowDeactivate` | `bool` | Set to `false` to "pin" the popup open when it loses focus. |
| `badgeText` | `string` | Text of a badge over the icon. |
| `toolTipMainText`, `toolTipSubText` | `string` | The default tooltip's text. |
| `toolTipTextFormat` | `int` | The text format of the tooltip. |
| `toolTipItem` | `Item` | A custom tooltip. |
| `screen` | `int` | The screen the widget is on. |
| `screenGeometry` | `rect` | The geometry of that screen. |
| `availableScreenRect` | `rect` | The part of the screen not taken by panels. |
| `availableScreenRegion` | `list` | The same as a list of rectangles. |
| `plasmoid` | `Applet` | The applet, the same object as the `Plasmoid` attached property. |

### Plasmoid properties

| Property | Type | Notes |
| --- | --- | --- |
| `Plasmoid.id` | `uint` | An integer identifying this instance of the widget. For the widget's name, see `Plasmoid.pluginName`. |
| `Plasmoid.pluginName` | `string` | The widget's `Id`. |
| `Plasmoid.title` | `string` | The widget's title; by default its translated `Name`. |
| `Plasmoid.icon` | `string` | The widget's icon. See [below](#plasmoidicon). |
| `Plasmoid.formFactor` | `Plasma::Types::FormFactor` | How the widget is shown, for example horizontal in a panel. |
| `Plasmoid.location` | `Plasma::Types::Location` | Where the widget is on the screen. |
| `Plasmoid.status` | `Plasma::Types::ItemStatus` | How important the widget currently is, for example to the system tray. |
| `Plasmoid.immutability` | `Plasma::Types::ImmutabilityType` | Whether widgets are locked, for example by Kiosk mode. |
| `Plasmoid.immutable` | `bool` | Whether the widget is immutable. |
| `Plasmoid.containmentDisplayHints` | `Plasma::Types::ContainmentDisplayHints` | Hints from the containment holding the widget. |
| `Plasmoid.busy` | `bool` | Draw a busy indicator over the widget. |
| `Plasmoid.userConfiguring` | `bool` | Whether the user is configuring the widget. |
| `Plasmoid.backgroundHints` | `Plasma::Types::BackgroundHints` | The background of the widget on the desktop. See [below](#plasmoidbackgroundhints). |
| `Plasmoid.userBackgroundHints` | `Plasma::Types::BackgroundHints` | The background the user chose. |
| `Plasmoid.effectiveBackgroundHints` | `Plasma::Types::BackgroundHints` | The actual background, from `backgroundHints` and `userBackgroundHints`. |
| `Plasmoid.configuration` | `KConfigPropertyMap` | The user's configuration values. See [below](#plasmoidconfiguration). |
| `Plasmoid.globalShortcut` | `QKeySequence` | The widget's global shortcut. |
| `Plasmoid.configurationRequired` | `bool` | Whether to show a Configure button over the widget. |
| `Plasmoid.hasConfigurationInterface` | `bool` | Whether the widget has a configuration window. |
| `Plasmoid.constraintHints` | `Plasma::Applet::ConstraintHints` | Hints for the containment. |
| `Plasmoid.metaData` | [`KPluginMetaData`](/docs/api/kcoreaddons/kpluginmetadata) | The widget's `metadata.json`. |
| `Plasmoid.containment` | `Plasma::Containment` | The containment holding the widget. |
| `Plasmoid.contextualActions` | `list<QAction>` | The widget's actions, in its header and context menu. |
| `Plasmoid.isContainment` | `bool` | Whether the widget is a containment. |

### compactRepresentation

The compact representation uses [DefaultCompactRepresentation.qml](https://github.com/Sonic-DE/sonic-desktop-interface/blob/master/desktoppackage/contents/applet/DefaultCompactRepresentation.qml) by default. To summarize, it:

* Draws `Plasmoid.icon` with a [Kirigami.Icon](/docs/api/kirigami/qml-org-kde-kirigami-primitives-icon).
* Defines a [MouseArea](https://doc.qt.io/qt-6/qml-qtquick-mousearea.html) that toggles the `expanded` property, which displays the full representation.

### fullRepresentation

If there is enough room (more than `switchWidth` and `switchHeight`), the widget's full representation can be drawn directly in the panel or on the desktop. To force this, set `preferredRepresentation`:

```qml
preferredRepresentation: fullRepresentation
```

If there isn't enough room, the widget displays `compactRepresentation` instead, and the full representation is visible when `expanded` is `true`, in a dialog you can't access directly. You can manipulate the dialog:

* Set `Layout.preferredWidth` and `Layout.preferredHeight` in your full representation to change the dialog's size.
* Set `hideOnWindowDeactivate` to keep the dialog from closing. You can use this for a configurable "pin".

See [CompactApplet.qml](https://github.com/Sonic-DE/sonic-desktop-interface/blob/master/desktoppackage/contents/applet/CompactApplet.qml) for the exact behavior. For an example that sets the size, see [Setup](setup.md#contentsuimainqml).

### Plasmoid.icon

As mentioned in [Setup](setup.md#metadatajson), the widget's icon comes from the `Icon` value in `metadata.json` by default.

For a dynamic or user-configurable icon, assign an icon name to `Plasmoid.icon`. You can search for icon names in the `/usr/share/icons` folder, or browse them with Icon Explorer (`iconexplorer`) from [sonic-theme-sdk](https://github.com/Sonic-DE/sonic-theme-sdk).

```qml
import QtQuick
import org.kde.plasma.plasmoid

PlasmoidItem {
    id: widget
    property bool hasUnread: true
    Plasmoid.icon: hasUnread ? "mail-unread" : "mail-message"

    Timer {
        interval: 1000
        repeat: true
        running: true
        onTriggered: widget.hasUnread = !widget.hasUnread
    }
}
```

### Plasmoid.configuration

This property gives access to the user's configuration values, as `Plasmoid.configuration.varName`. It is populated from the keys and values in `config/main.xml`. Assign to it, as in `Plasmoid.configuration.varName = "value"`, to change a value for the user. The default of a key is available as `Plasmoid.configuration.varNameDefault`.

The user's configuration is stored in `~/.config/sonic-org.sonicde.desktop-appletsrc`.

```qml
import QtQuick
import QtQuick.Layouts
import org.kde.plasma.components as PlasmaComponents
import org.kde.plasma.plasmoid

PlasmoidItem {
    fullRepresentation: RowLayout {
        PlasmaComponents.Label {
            text: i18np("%1 Click", "%1 Clicks", Plasmoid.configuration.numClicked)
        }
        PlasmaComponents.Button {
            icon.name: "value-increase-symbolic"
            text: i18n("Add")
            onClicked: Plasmoid.configuration.numClicked += 1
        }
    }
}
```

### Plasmoid.backgroundHints

* `PlasmaCore.Types.DefaultBackground` **(default)** is the same as `StandardBackground`.
* `PlasmaCore.Types.StandardBackground`: the standard background from the theme is drawn.
* `PlasmaCore.Types.TranslucentBackground`: an alternate version of the background is drawn, usually more translucent.
* `PlasmaCore.Types.ShadowBackground`: the widget has no SVG background, but a drop shadow of its content done with a shader. The text color also inverts.
* `PlasmaCore.Types.NoBackground`: hides the background of a desktop widget.
* `PlasmaCore.Types.ConfigurableBackground`: lets the user configure the background. This is a flag to combine with another value, using the bitwise OR operator `|`.

```qml
import QtQuick
import org.kde.plasma.core as PlasmaCore
import org.kde.plasma.plasmoid

PlasmoidItem {
    Plasmoid.backgroundHints: PlasmaCore.Types.NoBackground
}
```

```qml
import QtQuick
import QtQuick.Layouts
import org.kde.kirigami as Kirigami
import org.kde.plasma.core as PlasmaCore
import org.kde.plasma.components as PlasmaComponents
import org.kde.plasma.plasmoid

PlasmoidItem {
    Plasmoid.icon: "starred-symbolic"
    Plasmoid.backgroundHints: PlasmaCore.Types.StandardBackground | PlasmaCore.Types.ConfigurableBackground

    preferredRepresentation: fullRepresentation
    fullRepresentation: RowLayout {
        Kirigami.Icon {
            source: Plasmoid.icon
            Layout.fillHeight: true
            Layout.preferredWidth: height
        }
        PlasmaComponents.Label {
            text: "Text"
            font.pointSize: 30
        }
    }
}
```

## metadata.json

The common `metadata.json` properties are covered in [Setup](setup.md#metadatajson). The [KPluginMetaData](/docs/api/kcoreaddons/kpluginmetadata) documentation describes the format.

### Name, Description

You can translate these with `Name[fr]` and `Description[fr]`. The translated `Name` is used in the "Add Widgets" list. The `Description` is used for the default tooltip subtext when the widget is added to a panel.

```json
{
    "KPlugin": {
        "Description": "Month display with your appointments and events",
        "Description[fr]": "Vue mensuelle avec vos rendez-vous et évènements",
        "Name": "Calendar",
        "Name[fr]": "Calendrier"
    }
}
```

### Icon

`Icon` is the icon name associated with the widget. You can search for icon names in the `/usr/share/icons` folder, or browse them with Icon Explorer (`iconexplorer`) from [sonic-theme-sdk](https://github.com/Sonic-DE/sonic-theme-sdk).

```json
{
    "KPlugin": {
        "Icon": "office-calendar"
    }
}
```

### Id

`Id` must be a unique name, since it is used for the name of the folder the widget is installed into. Consider it the widget's namespace.

To view the installed namespaces:

```bash
kpackagetool6 --type Plasma/Applet --list
kpackagetool6 --type Plasma/Applet --list --global
```

```json
{
    "KPlugin": {
        "Id": "com.example.helloworld"
    }
}
```

### Category

`Category` filters widgets in the widget list.

```json
{
    "KPlugin": {
        "Category": "Date and Time"
    }
}
```

* `Accessibility`: tools that help people with special needs or disabilities use their computer
* `Application Launchers`: application starters and file openers
* `Astronomy`: anything to do with the night sky or other celestial bodies
* `Date and Time`: clocks, calendars, scheduling and so on
* `Development Tools`: tools and utilities that help software developers
* `Education`: teaching and educational aids
* `Environment and Weather`: information about the weather or other environmental data
* `Examples`: samples not meant for production systems
* `File System`: anything operating on files or the file system as its primary purpose, such as file watchers or directory listings; merely using a file as storage doesn't qualify
* `Fun and Games`: games and amusements
* `Graphics`: widgets whose primary purpose is displaying images, photos or graphical eye candy
* `Language`: widgets whose primary purpose is language related, such as dictionaries and translators
* `Mapping`: geography and geographic data
* `Multimedia`: music and video
* `Online Services`: interfaces to online services such as social networking or blogging sites; if another category fits the topic better (such as mapping), prefer that one
* `System Information`: information about the computer, such as network activity, hardware health or memory usage
* `Utilities`: useful tools like calculators
* `Windows and Tasks`: managers for application windows or tasks, such as taskbars

### KPackageStructure

`KPackageStructure` identifies the associated [KPackage::PackageStructure](/docs/api/kpackage/kpackage-packagestructure). For a desktop widget, it is `Plasma/Applet`.

```json
{
    "KPackageStructure": "Plasma/Applet"
}
```

The entry point of a widget is always `ui/main.qml`, so the older `X-Plasma-API` and `X-Plasma-MainScript` keys are no longer used.

### X-Plasma-Provides (alternatives)

A widget can specify the type of functionality it offers, such as a clock or an application launcher. This is used to list alternative widgets for a function: the context menu of the Application Launcher (kickoff) offers Application Menu (kicker) and Application Dashboard (kickerdash) as alternatives, because all three define:

```json
{
    "X-Plasma-Provides": [
        "org.kde.plasma.launchermenu"
    ]
}
```

These values are in fact arbitrary, so you can choose your own. The list can have several values. Here are some used throughout the desktop:

* `org.kde.plasma.launchermenu`: application launcher menus
* `org.kde.plasma.multimediacontrols`: multimedia controls
* `org.kde.plasma.time`: clocks
* `org.kde.plasma.date`: calendars
* `org.kde.plasma.notifications`: notifications
* `org.kde.plasma.removabledevices`: removable devices, auto-mounters and so on
* `org.kde.plasma.multitasking`: task switchers
* `org.kde.plasma.virtualdesktops`: virtual desktop switchers
* `org.kde.plasma.activities`: activity switchers
* `org.kde.plasma.trash`: trash and file deletion

### X-Plasma-NotificationArea (system tray)

The [Media Controller widget](https://github.com/Sonic-DE/sonic-workspace/blob/master/applets/mediacontroller/metadata.json) is a good example, since it uses most of the system tray's metadata features:

```json
{
    "KPlugin": {
        "EnabledByDefault": true
    },
    "X-Plasma-DBusActivationService": "org.mpris.MediaPlayer2.*",
    "X-Plasma-NotificationArea": "true",
    "X-Plasma-NotificationAreaCategory": "ApplicationStatus"
}
```

With `X-Plasma-NotificationArea`, the system tray widget finds this widget.

`EnabledByDefault` makes sure it is enabled in the system tray by default.

The widget should also set `X-Plasma-NotificationAreaCategory`, so that icons are grouped together. Its allowed values are:

* `ApplicationStatus`: the item represents an active application.
* `Hardware`: the item manages hardware (for example a battery monitor or the Wi-Fi widget).
* `SystemServices`: the item shows information about system services, for example the status of file indexing or software updates.

### X-Plasma-DBusActivationService

`X-Plasma-DBusActivationService` loads and unloads widgets in the system tray automatically when a D-Bus service becomes available or stops, so the user doesn't have to enable or remove the widget in the notification area settings.

For example, the Media Controller widget is loaded as soon as an application offers the `org.mpris.MediaPlayer2` D-Bus service in the session. The key accepts wildcards, which makes D-Bus names easier to match. It also helps avoid having a widget loaded when it's unnecessary, which saves visual clutter and memory.

```json
{
    "X-Plasma-DBusActivationService": "org.mpris.MediaPlayer2.*"
}
```
