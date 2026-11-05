---
title: Creating sensor faces
description: Create new display styles for the System Monitor application and widgets.
source_url: https://develop.kde.org/docs/apps/sensor-faces/
source_authors: [Alexander Lohnau, Carl Schwan, David Redondo, Fushan Wen, Phu Nguyen, Raresh Rus, Rocket Aaron, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "faces and sensors in sonic-system-monitor-library, the KSysguard/SensorFace package structure and shipped faces. Each example linted and loaded through SensorFaceController on the staged libraries under Xvfb with live ksystemstats data, and captured; a face installed with kpackagetool6. Config.qml loaded but was not edited through a real settings dialog, and faces were not shown inside the System Monitor application."
---

# Creating sensor faces

A sensor face is a display style for the System Monitor application and its widgets.

## Folder structure

A sensor face has several parts, some required and others optional. The structure is similar to that of desktop widgets:

```text
rootdir
├── contents
│   ├── ui
│   │   ├── FullRepresentation.qml (required)
│   │   ├── CompactRepresentation.qml (required)
│   │   └── Config.qml (optional)
│   ├── config
│   │   └── main.xml (optional)
│   └── faceproperties (required)
└── metadata.json (required)
```

The most interesting files are `FullRepresentation.qml` and `CompactRepresentation.qml`, which hold the elements that display the data of the sensors. `Config.qml` is a user interface for the face's settings, which are described in `main.xml` in [KConfig XT syntax](configuration/kconfig-xt.md). `faceproperties` says which features the face supports, and `metadata.json` describes the face and tells the system about it.

## The visual representations

Both representations follow the same schema but are used in different contexts. The full representation is the one normally used, and has additional elements such as a legend or title. The compact representation is used when something much smaller is needed, such as when the System Monitor widget is added to a panel.

The root item of both representations has to be `SensorFace`. Assign the root of your visualization to its `contentItem` property. `SensorFace` also gives access to the face controller through its `controller` property, which tells the face which sensors to display and how.

The controller's most important property is `highPrioritySensorIds`, which the user interface calls just "Sensors". The face should always display the data of these sensors. This very basic face shows just the IDs of the sensors it should display:

```qml
import QtQuick.Controls
import org.kde.ksysguard.faces

SensorFace {
    contentItem: Label {
        text: "Sensors that should be shown: "
            + controller.highPrioritySensorIds.join(",")
    }
}
```

Other interesting properties of the face controller are:

- `sensorColors`: maps sensor IDs to colors. Use this if you need a color for an element related to a sensor.
- `lowPrioritySensorIds`: sensor IDs of lower importance than the normal sensors. They appear as "Text-Only Sensors", because most faces display them just as text in the legend.
- `totalSensors`: sensors whose values represent totals of some sort. The pie chart face, for example, shows them in its center.
- `title`: the title of this face instance, which can be empty.
- `showTitle`: whether the face should display the title.

For all the available properties, see [`SensorFaceController.h`](https://github.com/Sonic-DE/sonic-system-monitor-library/blob/master/faces/SensorFaceController.h).

With some of these, the basic face can also show a title and a color for each sensor:

```qml
import QtQuick
import QtQuick.Controls
import QtQuick.Layouts

import org.kde.kirigami as Kirigami

import org.kde.ksysguard.faces as Faces

Faces.SensorFace {
    contentItem: ColumnLayout {
        Kirigami.Heading {
            Layout.alignment: Qt.AlignHCenter
            text: "Title: " + controller.title
            visible: controller.showTitle
            level: 2
        }
        Label {
            text: "Sensors that should be shown: "
                + controller.highPrioritySensorIds.map(id => "<font color='" + controller.sensorColors[id] + "'>" + id + "</font>").join(", ")
        }
    }
}
```

### Retrieving the data

The face controller supplies the list of sensor IDs. To get more information about the sensors and their current values, there are two options.

You can create a `Sensor` for each ID and read its `formattedValue`, or its raw `value` and `unit`. It also has the sensor's user-visible `name`, and the range of possible values in `minimum` and `maximum`. See [`Sensor.h`](https://github.com/Sonic-DE/sonic-system-monitor-library/blob/master/sensors/Sensor.h).

Or you can pass the list of IDs to a `SensorDataModel` and get the data from there. The sensors become a table with one column for each sensor, and the same properties as a `Sensor` are available as the model's roles. See [`SensorDataModel.h`](https://github.com/Sonic-DE/sonic-system-monitor-library/blob/master/sensors/SensorDataModel.h).

This example shows both methods. A `TableView` needs its column widths set, since the delegates are created before the sensor data has arrived.

```qml
import QtQuick
import QtQuick.Controls
import QtQuick.Layouts

import org.kde.kirigami as Kirigami

import org.kde.ksysguard.faces as Faces
import org.kde.ksysguard.sensors as Sensors

Faces.SensorFace {
    contentItem: ColumnLayout {
        Kirigami.Heading {
            Layout.alignment: Qt.AlignHCenter
            text: i18n("Title: %1", controller.title)
            visible: controller.showTitle
            level: 2
        }

        Label {
            text: i18n("We can use Sensor directly")
        }
        Repeater {
            model: controller.highPrioritySensorIds
            delegate: Label {
                id: sensorLabel
                required property string modelData

                text: i18n("%1: %2", sensor.name, sensor.formattedValue)
                color: controller.sensorColors[sensor.sensorId]

                Sensors.Sensor {
                    id: sensor
                    sensorId: sensorLabel.modelData
                }
            }
        }

        Label {
            text: i18n("Or use a SensorDataModel")
        }
        Sensors.SensorDataModel {
            id: sensorModel
            sensors: controller.highPrioritySensorIds
            sensorColors: controller.sensorColors
        }
        TableView {
            id: table
            Layout.fillWidth: true
            Layout.preferredHeight: contentHeight
            columnWidthProvider: () => table.width / table.columns
            model: sensorModel
            delegate: Label {
                required property var model

                text: i18n("%1: %2", model.Name, model.FormattedValue)
                color: model.Color
            }
        }
    }
}
```

### Adding a legend

A legend is useful for matching colors to a chart and reading exact current values. `ExtendedLegend` is a ready-made component that displays a legend generated from a `SensorDataModel` assigned to its `sourceModel` property. Its `sensorIds` property holds the IDs of additional sensors to include. Most faces use it for the "text only" `lowPrioritySensorIds`. A typical use looks like this:

```qml
import QtQuick
import QtQuick.Controls
import QtQuick.Layouts

import org.kde.kirigami as Kirigami

import org.kde.ksysguard.faces as Faces
import org.kde.ksysguard.sensors as Sensors

Faces.SensorFace {
    contentItem: ColumnLayout {
        Kirigami.Heading {
            Layout.alignment: Qt.AlignHCenter
            text: "Title: " + controller.title
            visible: controller.showTitle
            level: 2
        }

        Sensors.SensorDataModel {
            id: sensorModel
            sensors: controller.highPrioritySensorIds
            sensorColors: controller.sensorColors
        }

        // Here would be the face specific visualization

        Faces.ExtendedLegend {
            sourceModel: sensorModel
            sensorIds: controller.lowPrioritySensorIds
            Layout.fillWidth: true
        }
    }
}
```

The `sensorColors` from the controller go to the `SensorDataModel` through its own `sensorColors` property, so that the legend includes each sensor's color.

## Adding configuration options

If a face has configurable elements or display settings, declare them in `main.xml`. A simple example:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<kcfg xmlns="http://www.kde.org/standards/kcfg/1.0"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://www.kde.org/standards/kcfg/1.0
      http://www.kde.org/standards/kcfg/1.0/kcfg.xsd" >
    <kcfgfile name=""/>
    <group name="General">
        <entry name="showRectangle" type="Bool">
            <default>true</default>
        </entry>
        <entry name="rectangleText" type="String">
            <default>Rectangle</default>
        </entry>
    </group>
</kcfg>
```

This declares two options: a boolean `showRectangle`, and `rectangleText`, which holds some text. By default the rectangle is shown and the text is "Rectangle". Options can have many types, such as `Int`, `StringList`, `Double` and `Color`. [Using KConfig XT](configuration/kconfig-xt.md) introduces the file format and the data types.

The controller exposes the active configuration as `faceConfiguration`, and the current values are properties of it. This face displays a rectangle with `rectangleText` on it if `showRectangle` is true:

```qml
import QtQuick
import org.kde.ksysguard.faces as Faces

Faces.SensorFace {
    contentItem: Rectangle {
        visible: controller.faceConfiguration.showRectangle
        border.width: 2
        Text {
            text: controller.faceConfiguration.rectangleText
            anchors.centerIn: parent
        }
    }
}
```

To let the user change the options, the face provides a user interface in `Config.qml`:

```qml
import QtQuick.Controls

import org.kde.kirigami as Kirigami

Kirigami.FormLayout {
    property alias cfg_showRectangle: rectangleCheckbox.checked
    property alias cfg_rectangleText: rectangleTextEdit.text

    CheckBox {
        id: rectangleCheckbox
        text: "Show Rectangle"
    }
    TextField {
        id: rectangleTextEdit
        Kirigami.FormData.label: "Rectangle Text"
    }
}
```

Here a checkbox controls whether the rectangle is shown, and a text field holds its text. Properties named `cfg_configOption` are automatically bound to the stored setting if `configOption` is a declared option. They are set to the currently configured value, and when they change, the controller is told that the setting has changed. Here they are aliases for properties of controls, but they can also be normal properties with more complicated bindings.

When the configuration changes, the matching property of `controller.faceConfiguration` is updated automatically. The controller handles reading, saving and updating the configuration, so the face doesn't need to.

## Finishing it up

Two files are left.

### metadata.json

This has user-visible and other metadata about the face.

```json
{
    "KPlugin": {
        "Authors": [
            {
                "Email": "your.name@example.org",
                "Name": "Your Name"
            }
        ],
        "Icon": "office-chart-line",
        "Id": "org.example.awesomeface",
        "License": "",
        "Name": "My awesome face",
        "Version": "1.0",
        "Website": ""
    },
    "X-KDE-ParentApp": "org.sonicde.sonicshell",
    "KPackageStructure": "KSysguard/SensorFace"
}
```

`Name` and `Icon` are the face's user-visible name and an icon for it. `Id` is its unique identifier. [KPluginMetaData](/docs/api/kcoreaddons/kpluginmetadata) documents all the entries in the `KPlugin` object. `KPackageStructure` is needed for the face to be found.

### faceproperties

Not every face supports every feature exposed by the [face controller](#the-visual-representations). The file `contents/faceproperties` says which it supports, so that settings for unsupported features can be hidden, for example.

The file starts with a `[Config]` line, followed by key-value pairs. The keys are `SupportsSensorsColors`, `SupportsTotalSensors`, `SupportsLowPrioritySensors` and `MaxTotalSensors`. By default, a face is assumed not to support these features, and `MaxTotalSensors` is `1` when total sensors are supported. For example:

```ini
[Config]
SupportsSensorsColors=false
SupportsTotalSensors=true
MaxTotalSensors=2
```

This face doesn't support sensor colors, which it declares explicitly, or low priority sensors, because the default is `false`. It does support displaying two total sensors.

### Installation

For applications to find a face, it has to be in a specific directory: typically `/usr/share/ksysguard/sensorfaces/` for faces installed for the system, or `~/.local/share/ksysguard/sensorfaces/` for one user. The root folder has to have the same name as the `Id` in the metadata.

`kpackagetool6` handles this for you:

```bash
kpackagetool6 --type=KSysguard/SensorFace -i /path/to/package
```

A face distributed through the [KDE Store](https://store.kde.org), which SonicDE uses for downloads, is installed automatically by the relevant tools.

## Further topics

- For faces with charts, the [KQuickCharts](/docs/api/kquickcharts/kquickcharts-index) framework makes it easy to create charts from QML. The [faces that ship with SonicDE](https://github.com/Sonic-DE/sonic-system-monitor-library/tree/master/faces/facepackages) are good examples.
