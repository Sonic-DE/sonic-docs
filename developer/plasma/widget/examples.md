---
title: Widget examples
description: Resizable popup, clock, configurable icon and other simple examples.
source_url: https://develop.kde.org/docs/plasma/widget/examples/
source_authors: [Alexander Hau, Alexander Lohnau, Carl Schwan, Chris Holland, Christoph Dreier, Claudius Ellsel, David Edmundson, Florian Ruechel, Fushan Wen, Johannes Zarl-Zierl, Joshua Goins, Kunda Ki, Marco Martin, Mariusz Libera, Michael Pyne, Mikhail Zolotukhin, Nate Graham, Nicolas Fella, Parth Dhiman, Paul Brown, Plata Hill, Raresh Rus, Rony Bou Moujahed, Thiago Sueto, Tino Lorenz, Tobias Fella, Yaron Shahrabani, Zren (Chris Holland), ivan tkachenko, yaniss khima]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "fuzzy-clock and kickoff applets, org.kde.plasma.clock, org.kde.iconthemes and org.kde.plasma.plasma5support QML modules, the time data engine in sonic-plasma5-support-library; examples checked with qmllint"
---

# Widget examples

There are also several examples in [sonic-interface-libraries](https://github.com/Sonic-DE/sonic-interface-libraries/tree/master/examples/applets).

## Configurable icon

To make your panel icon configurable, like in the [Application Launcher widget](https://github.com/Sonic-DE/sonic-desktop-interface/tree/master/applets/kickoff), we:

* Create a new string configuration key (`Plasmoid.configuration.icon`).
* Set [Plasmoid.icon](properties.md#plasmoidicon) to `Plasmoid.configuration.icon`.
* Make a reusable icon selector control, in a `ConfigIcon.qml` file.
* Add a `ConfigIcon` button to our `ConfigGeneral.qml` tab, and bind it to a `cfg_icon` property.

`contents/config/main.xml`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<kcfg xmlns="http://www.kde.org/standards/kcfg/1.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.kde.org/standards/kcfg/1.0 http://www.kde.org/standards/kcfg/1.0/kcfg.xsd">
    <kcfgfile name=""/>

    <group name="General">
        <entry name="icon" type="String">
            <default>start-here-sonicde</default>
        </entry>
    </group>
</kcfg>
```

`contents/ui/main.qml`:

```qml
import QtQuick
import org.kde.plasma.plasmoid

PlasmoidItem {
    Plasmoid.icon: Plasmoid.configuration.icon
}
```

`contents/ui/ConfigIcon.qml`:

```qml
import QtQuick
import QtQuick.Controls as QQC2
import org.kde.iconthemes as KIconThemes
import org.kde.kirigami as Kirigami

QQC2.Button {
    id: configIcon

    property string defaultValue: ""
    property string value: ""

    implicitWidth: Kirigami.Units.iconSizes.large + Kirigami.Units.smallSpacing * 4
    implicitHeight: implicitWidth

    onPressed: iconMenu.opened ? iconMenu.close() : iconMenu.open()

    KIconThemes.IconDialog {
        id: iconDialog
        onIconNameChanged: configIcon.value = iconName || configIcon.defaultValue
    }

    Kirigami.Icon {
        anchors.centerIn: parent
        width: Kirigami.Units.iconSizes.large
        height: width
        source: configIcon.value
    }

    QQC2.Menu {
        id: iconMenu

        // Appear below the button
        y: parent.height

        QQC2.MenuItem {
            text: i18n("Choose...")
            icon.name: "document-open-folder"
            onClicked: iconDialog.open()
        }
        QQC2.MenuItem {
            text: i18n("Clear Icon")
            icon.name: "edit-clear"
            onClicked: configIcon.value = configIcon.defaultValue
        }
    }
}
```

`contents/ui/ConfigGeneral.qml`:

```qml
import QtQuick
import org.kde.kirigami as Kirigami
import org.kde.kcmutils as KCM

KCM.SimpleKCM {
    property alias cfg_icon: configIcon.value

    Kirigami.FormLayout {
        ConfigIcon {
            id: configIcon
            Kirigami.FormData.label: i18n("Icon:")
        }
    }
}
```

`contents/config/config.qml`:

```qml
import QtQuick
import org.kde.plasma.configuration

ConfigModel {
    ConfigCategory {
        name: i18n("General")
        icon: "configure"
        source: "ConfigGeneral.qml"
    }
}
```

## Configurable panel widget width and height

To let the user permanently configure the popup size of a panel widget, or the size of the compact view in the panel, we store the width and height in the configuration.

We change our hardcoded sizes:

```qml
fullRepresentation: Item {
    Layout.preferredWidth: 640
    Layout.preferredHeight: 480
}
```

into this:

```qml
fullRepresentation: Item {
    Layout.preferredWidth: Plasmoid.configuration.width
    Layout.preferredHeight: Plasmoid.configuration.height
}
```

To simplify testing, we set `hideOnWindowDeactivate: false`, which keeps the popup from closing when you focus the configuration window.

Next we register the configuration keys and their default values in `config/main.xml`, create a form in `ui/configGeneral.qml` with a [SpinBox](https://doc.qt.io/qt-6/qml-qtquick-controls-spinbox.html) whose maximum is the largest signed integer value in QML, and register the General tab in `config/config.qml`.

`contents/ui/main.qml`:

```qml
import QtQuick
import QtQuick.Layouts
import org.kde.plasma.components as PlasmaComponents
import org.kde.plasma.plasmoid

PlasmoidItem {
    hideOnWindowDeactivate: false

    fullRepresentation: Item {
        id: popupView
        Layout.preferredWidth: Plasmoid.configuration.width
        Layout.preferredHeight: Plasmoid.configuration.height

        ColumnLayout {
            anchors.fill: parent

            PlasmaComponents.Label {
                text: i18n("Size: %1 x %2", popupView.width, popupView.height)
            }
        }
    }
}
```

`contents/config/main.xml`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<kcfg xmlns="http://www.kde.org/standards/kcfg/1.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.kde.org/standards/kcfg/1.0 http://www.kde.org/standards/kcfg/1.0/kcfg.xsd">
    <kcfgfile name=""/>

    <group name="General">
        <entry name="width" type="Int">
            <default>640</default>
        </entry>
        <entry name="height" type="Int">
            <default>480</default>
        </entry>
    </group>
</kcfg>
```

`contents/ui/configGeneral.qml`:

```qml
import QtQuick
import QtQuick.Controls as QQC2
import QtQuick.Layouts
import org.kde.kirigami as Kirigami
import org.kde.kcmutils as KCM

KCM.SimpleKCM {
    property alias cfg_width: widthSpinBox.value
    property alias cfg_height: heightSpinBox.value

    Kirigami.FormLayout {
        RowLayout {
            Kirigami.FormData.label: i18n("Size:")

            QQC2.SpinBox {
                id: widthSpinBox
                from: 0
                to: 2147483647 // 2^31-1
            }
            QQC2.Label {
                text: " x "
            }
            QQC2.SpinBox {
                id: heightSpinBox
                from: 0
                to: 2147483647 // 2^31-1
            }
        }
    }
}
```

`contents/config/config.qml`:

```qml
import QtQuick
import org.kde.plasma.configuration

ConfigModel {
    ConfigCategory {
        name: i18n("General")
        icon: "configure"
        source: "configGeneral.qml"
    }
}
```

## A clock

An extremely simple example is the [fuzzy clock widget](https://github.com/Sonic-DE/sonic-workspace-addons/blob/master/applets/fuzzy-clock/qml/main.qml).

The `new Date()` is familiar if you come from JavaScript, and a Timer with the Date type would work, but `Clock`, from `org.kde.plasma.clock`, keeps the time for you. Its `dateTime` property updates every minute, or every second if you set `trackSeconds`.

A clock can then use [Qt.locale()](https://doc.qt.io/qt-6/qml-qtqml-qt.html#locale-method) to display the time in a human-readable format.

```qml
import QtQuick
import QtQuick.Layouts
import org.kde.kirigami as Kirigami
import org.kde.plasma.clock
import org.kde.plasma.components as PlasmaComponents
import org.kde.plasma.plasmoid
import org.kde.plasma.workspace.calendar as PlasmaCalendar

PlasmoidItem {
    id: root

    readonly property date currentDateTime: clockSource.dateTime

    width: Kirigami.Units.gridUnit * 10
    height: Kirigami.Units.gridUnit * 4

    preferredRepresentation: compactRepresentation

    toolTipMainText: Qt.locale().toString(currentDateTime, "dddd")
    toolTipSubText: Qt.locale().toString(currentDateTime, Qt.locale().timeFormat(Locale.LongFormat))

    Clock {
        id: clockSource
    }

    compactRepresentation: PlasmaComponents.Label {
        text: Qt.locale().toString(root.currentDateTime, Qt.locale().timeFormat(Locale.ShortFormat))

        MouseArea {
            anchors.fill: parent
            onClicked: root.expanded = !root.expanded
        }
    }

    fullRepresentation: PlasmaCalendar.MonthView {
        Layout.minimumWidth: Kirigami.Units.gridUnit * 20
        Layout.minimumHeight: Kirigami.Units.gridUnit * 20

        today: root.currentDateTime
    }
}
```

## Solar data source

Data engines share data between widgets. They now come from `sonic-plasma5-support-library`, through `Plasma5Support.DataSource`.

The `time` data engine provides the sun's [azimuth](https://en.wikipedia.org/wiki/Azimuth), [zenith](https://en.wikipedia.org/wiki/Zenith) and "corrected elevation" for a longitude and latitude at a specific time of day. Ask for a source name like the following, here for Toronto, Canada:

```text
UTC-04:00|Solar|Latitude=43.68|Longitude=79.63|DateTime=2021-03-23T19:00:00
```

```qml
import QtQuick
import org.kde.plasma.plasma5support as Plasma5Support
import org.kde.plasma.plasmoid

PlasmoidItem {
    Plasma5Support.DataSource {
        id: dataSource
        readonly property string source: "UTC-04:00|Solar|Latitude=43.68|Longitude=79.63|DateTime=2021-03-23T19:00:00"
        engine: "time"
        connectedSources: [source]
        onNewData: (sourceName, data) => console.log("Corrected Elevation", data["Corrected Elevation"])
    }
}
```

The data holds these keys:

| Type | Key | Value |
| --- | --- | --- |
| `double` | `Azimuth` | 69.6342657428925 |
| `double` | `Corrected Elevation` | -18.092120068676486 |
| `QDateTime` | `DateTime` | Tue Mar 23 19:00:00 2021 |
| `int` | `Offset` | UTC-04:00 |
| `QString` | `Timezone` | UTC-04:00 |
| `QString` | `Timezone Abbreviation` | UTC-04:00 |
| `QString` | `Timezone City` | UTC-04:00 |
| `double` | `Zenith` | 108.10976492154272 |

## Avoid widget resize on text change

We use [TextMetrics](https://doc.qt.io/qt-6/qml-qtquick-textmetrics.html) to calculate the size of the [Text](https://doc.qt.io/qt-6/qml-qtquick-text.html) label at its widest, maximum value of `100%`.

```qml
import QtQuick
import QtQuick.Layouts
import org.kde.kirigami as Kirigami
import org.kde.plasma.components as PlasmaComponents
import org.kde.plasma.plasmoid

PlasmoidItem {
    id: widget

    property int value: 0
    property int maxValue: 100

    function formatText(n) {
        return "" + n + "%"
    }

    preferredRepresentation: compactRepresentation

    compactRepresentation: PlasmaComponents.Label {
        id: label
        Layout.minimumWidth: textMetrics.width
        Layout.minimumHeight: textMetrics.height

        text: widget.formatText(widget.value)

        font.pointSize: 40
        horizontalAlignment: Text.AlignHCenter

        TextMetrics {
            id: textMetrics
            font.family: label.font.family
            font.pointSize: label.font.pointSize
            text: widget.formatText(100)
        }

        // Since we overrode the default compactRepresentation,
        // we need to set up the click that toggles the popup.
        MouseArea {
            anchors.fill: parent
            onClicked: widget.expanded = !widget.expanded
        }
    }

    fullRepresentation: Item {
        Layout.preferredWidth: Kirigami.Units.gridUnit * 35
        Layout.preferredHeight: Kirigami.Units.gridUnit * 26

        Rectangle {
            id: popup
            anchors.left: parent.left
            anchors.top: parent.top
            anchors.bottom: parent.bottom
            width: parent.width * (widget.value / 100)
            color: Kirigami.Theme.highlightColor
        }
    }

    Timer {
        interval: 100
        running: true
        repeat: true
        onTriggered: widget.value = (widget.value + 1) % (widget.maxValue + 1)
    }
}
```
