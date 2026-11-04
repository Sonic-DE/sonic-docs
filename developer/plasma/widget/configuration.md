---
title: Configuration
description: Adding user-configured settings to your widget.
source_url: https://develop.kde.org/docs/plasma/widget/configuration/
source_authors: [Alexander Hau, Alexander Lohnau, Carl Schwan, Chris Holland, Christoph Dreier, Claudius Ellsel, David Edmundson, Florian Ruechel, Fushan Wen, Johannes Zarl-Zierl, Joshua Goins, Kunda Ki, Marco Martin, Mariusz Libera, Michael Pyne, Mikhail Zolotukhin, Nate Graham, Nicolas Fella, Parth Dhiman, Paul Brown, Plata Hill, Raresh Rus, Rony Bou Moujahed, Thiago Sueto, Tino Lorenz, Tobias Fella, Yaron Shahrabani, Zren (Chris Holland), ivan tkachenko, yaniss khima]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "AppletConfiguration.qml and applet_p.cpp, config pages of kickoff, taskmanager and mediaframe, org.kde.kcmutils, org.kde.kquickcontrols and org.kde.iconthemes QML modules; examples checked with qmllint"
---

# Configuration

## Introduction

Every widget has a "Configure MyWidget..." action when you right-click it. By default its window contains a form to set a global shortcut that activates your widget.

## contents/config/main.xml

`main.xml` defines the properties stored in `~/.config/sonic-org.sonicde.desktop-appletsrc`. All of them are accessible as `Plasmoid.configuration.variableName`, whatever group they are in.

[KConfig](../../configuration/introduction.md) has a variety of data types:

* `Int` for an integer.
* `Double` for a double-precision floating point number.
* `String` for a string of characters.
* `Color` for a hexadecimal color. The color defaults to `#000000` (black) if the default is left empty.
* `Path` for a string specially treated as a file path. In particular, paths in the home directory are prefixed with `$HOME` when stored in the configuration file.
* `StringList` for a comma-separated list of strings.

These are the more common ones; there are more in [Using KConfig XT](../../configuration/kconfig-xt.md).

If you want to default to a color from the color scheme, don't use `Color`. Use a `String` that is empty by default instead, and fall back to the theme color in QML:

```xml
<entry name="labelColor" type="String">
    <default></default>
</entry>
```

```qml
PlasmaComponents.Label {
    color: Plasmoid.configuration.labelColor || Kirigami.Theme.textColor
}
```

A complete file:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<kcfg xmlns="http://www.kde.org/standards/kcfg/1.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.kde.org/standards/kcfg/1.0 http://www.kde.org/standards/kcfg/1.0/kcfg.xsd">
    <kcfgfile name=""/>

    <group name="General">
        <entry name="variableName" type="Bool">
            <default>true</default>
        </entry>
        <entry name="integerExample" type="Int">
            <default>6</default>
        </entry>
        <entry name="floatingPointExample" type="Double">
            <default>3.1459</default>
        </entry>
        <entry name="textExample" type="String">
            <default>Hello World</default>
        </entry>
        <entry name="listExample" type="StringList">
            <default>First Item,Second Item,Third Item</default>
        </entry>
        <entry name="colorExample" type="Color">
            <default>#336699</default>
        </entry>
    </group>
    <group name="AnotherGroup">
        <entry name="secondGroupExample" type="Bool">
            <default>false</default>
        </entry>
    </group>
</kcfg>
```

## contents/config/config.qml

`config.qml` defines the tabs of the configuration window. We import `ConfigModel` and `ConfigCategory`, and define each tab's name, icon and QML file.

```qml
import QtQuick
import org.kde.plasma.configuration

ConfigModel {
    ConfigCategory {
        name: i18n("General")
        icon: "configure"
        source: "configGeneral.qml"
    }
    ConfigCategory {
        name: i18n("Another Tab")
        icon: "color-management"
        source: "configAnotherTab.qml"
    }
}
```

## contents/ui/configGeneral.qml

`configGeneral.qml` is where all the checkboxes and text fields go.

The root item of a configuration page must be one of the KCM components from `org.kde.kcmutils`. `SimpleKCM` is right for most widgets; the others are `AbstractKCM`, `ScrollViewKCM` and `GridViewKCM`.

Don't use `PlasmaComponents.*` controls in the configuration window, as those are styled and colored for the panel. The normal `QtQuick.Controls` follow the application style and colors.

`Kirigami.FormLayout` lays out the controls in the center of the page. The `Kirigami.FormData.label` attached property places labels in front of the controls. These labels are optional, so you don't need them for checkboxes, which have their own labels on the right.

```qml
import QtQuick
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami
import org.kde.kcmutils as KCM

KCM.SimpleKCM {
    id: page

    property alias cfg_showLabel: showLabel.checked
    property alias cfg_showIcon: showIcon.checked
    property alias cfg_labelText: labelText.text

    Kirigami.FormLayout {
        QQC2.CheckBox {
            id: showLabel
            Kirigami.FormData.label: i18n("Section:")
            text: i18n("Show label")
        }
        QQC2.CheckBox {
            id: showIcon
            text: i18n("Show icon")
        }
        QQC2.TextField {
            id: labelText
            Kirigami.FormData.label: i18n("Label:")
            placeholderText: i18n("Placeholder")
        }
    }
}
```

## configPage.cfg_variableName

All values are copied to the root item of the page, prefixed with `cfg_`, as in `page.cfg_variableName`. This lets the user discard or apply changes. Define a `cfg_` property for each value you bind to a QML control.

You can use a [property alias](https://doc.qt.io/qt-6/qtqml-syntax-objectattributes.html#property-aliases) to a control's property, like `checkBox.checked` or `textField.text`.

## CheckBox: Boolean

A [CheckBox](https://doc.qt.io/qt-6/qml-qtquick-controls-checkbox.html) is for boolean on/off values.

```xml
<entry name="variableName" type="Bool">
    <default>true</default>
</entry>
```

```qml
import QtQuick
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami
import org.kde.kcmutils as KCM

KCM.SimpleKCM {
    property alias cfg_variableName: variableName.checked

    Kirigami.FormLayout {
        QQC2.CheckBox {
            id: variableName
            text: i18n("Show")
        }
    }
}
```

## SpinBox: Integer

A [SpinBox](https://doc.qt.io/qt-6/qml-qtquick-controls-spinbox.html) is for numbers.

```xml
<entry name="variableName" type="Int">
    <default>6</default>
</entry>
```

```qml
import QtQuick
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami
import org.kde.kcmutils as KCM

KCM.SimpleKCM {
    property alias cfg_variableName: variableName.value

    Kirigami.FormLayout {
        QQC2.SpinBox {
            id: variableName
        }
    }
}
```

## SpinBox: Double

A SpinBox holds integers. For decimal places, scale the value, and convert it for display and for the configuration.

```xml
<entry name="variableName" type="Double">
    <default>3.1459</default>
</entry>
```

```qml
import QtQuick
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami
import org.kde.kcmutils as KCM

KCM.SimpleKCM {
    id: page
    property real cfg_variableName

    Kirigami.FormLayout {
        QQC2.SpinBox {
            readonly property int factor: 100

            from: 0
            to: 100 * factor
            value: Math.round(page.cfg_variableName * factor)
            onValueModified: page.cfg_variableName = value / factor
            textFromValue: (value, locale) => Number(value / factor).toLocaleString(locale, "f", 2)
            valueFromText: (text, locale) => Math.round(Number.fromLocaleString(locale, text) * factor)
        }
    }
}
```

## TextField: String

A [TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html) is for a single line of text. It can be a base for many other data types as well. See the base [TextInput](https://doc.qt.io/qt-6/qml-qtquick-textinput.html) for more properties.

```xml
<entry name="variableName" type="String">
    <default>Hello World</default>
</entry>
```

```qml
import QtQuick
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami
import org.kde.kcmutils as KCM

KCM.SimpleKCM {
    property alias cfg_variableName: variableName.text

    Kirigami.FormLayout {
        QQC2.TextField {
            id: variableName
        }
    }
}
```

## TextArea: multi-line String

A [TextArea](https://doc.qt.io/qt-6/qml-qtquick-controls-textarea.html) is for paragraphs of text. See the base [TextEdit](https://doc.qt.io/qt-6/qml-qtquick-textedit.html) for more properties.

```xml
<entry name="variableName" type="String">
    <default>Hello World</default>
</entry>
```

```qml
import QtQuick
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami
import org.kde.kcmutils as KCM

KCM.SimpleKCM {
    property alias cfg_variableName: variableName.text

    Kirigami.FormLayout {
        QQC2.TextArea {
            id: variableName
        }
    }
}
```

## ColorButton: Color

[ColorButton](https://github.com/Sonic-DE/sonic-frameworks-qml-bridge/blob/master/src/qmlcontrols/kquickcontrols/ColorButton.qml), from `org.kde.kquickcontrols`, previews the selected color and opens a color dialog for selecting one.

```xml
<entry name="variableName" type="Color">
    <default>#336699</default>
</entry>
```

```qml
import QtQuick
import org.kde.kirigami as Kirigami
import org.kde.kcmutils as KCM
import org.kde.kquickcontrols as KQControls

KCM.SimpleKCM {
    property alias cfg_variableName: variableName.color

    Kirigami.FormLayout {
        KQControls.ColorButton {
            id: variableName
            showAlphaChannel: true
        }
    }
}
```

`ColorButton` doesn't easily support the empty-`String` pattern above, as it stores the value in a QML `color` property, which reads an empty string as the default color `#000000` (black). A `TextField` holding the value as a string, with the default color scheme color as `placeholderText`, works around this.

## FileDialog: Path

To store a file path in the configuration, use the `Path` or `PathList` type. It substitutes `/home/user/...` with `$HOME/...`. To lay out the file selector, use a `RowLayout` with a `TextField` and a `Button` that opens a [FileDialog](https://doc.qt.io/qt-6/qml-qtquick-dialogs-filedialog.html). Set the folder the dialog opens in with `currentFolder`.

Place `Kirigami.FormData.label` on the `RowLayout`, as it is the direct child of `Kirigami.FormLayout`.

```xml
<entry name="variableName" type="Path">
    <default>/usr/share/sounds/freedesktop/stereo/message.oga</default>
</entry>
```

```qml
import QtCore
import QtQuick
import QtQuick.Controls as QQC2
import QtQuick.Dialogs as QQD
import QtQuick.Layouts
import org.kde.kirigami as Kirigami
import org.kde.kcmutils as KCM

KCM.SimpleKCM {
    property alias cfg_variableName: variableName.text

    Kirigami.FormLayout {
        RowLayout {
            Kirigami.FormData.label: i18n("Sound File:")

            QQC2.TextField {
                id: variableName
                placeholderText: i18n("No file selected.")
            }
            QQC2.Button {
                text: i18n("Browse")
                icon.name: "folder-symbolic"
                onClicked: fileDialog.open()
            }
        }
    }

    QQD.FileDialog {
        id: fileDialog
        currentFolder: StandardPaths.standardLocations(StandardPaths.MusicLocation)[0]
        nameFilters: [
            i18n("Sound files (%1)", "*.wav *.mp3 *.oga *.ogg"),
            i18n("All files (%1)", "*"),
        ]
        onAccepted: variableName.text = decodeURIComponent(selectedFile.toString().replace("file://", ""))
    }
}
```

## IconDialog: Icon

`KIconThemes.IconDialog`, from `org.kde.iconthemes`, makes it easy to search and preview icons. The Application Launcher's [icon selector](https://github.com/Sonic-DE/sonic-desktop-interface/blob/master/applets/kickoff/ConfigGeneral.qml) is an example, and [Widget examples](examples.md) has one too.

## Assigning to Plasmoid.configuration.varName

You can also assign directly to `Plasmoid.configuration.variableName`, in the configuration window or anywhere else in your widget. In a configuration page, this skips the "apply" step and the value applies right away.

```qml
import QtQuick
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami
import org.kde.kcmutils as KCM
import org.kde.plasma.plasmoid

KCM.SimpleKCM {
    Kirigami.FormLayout {
        QQC2.CheckBox {
            checked: Plasmoid.configuration.variableName
            onToggled: Plasmoid.configuration.variableName = checked
        }
    }
}
```

## Configuration examples

To learn by example, look at a couple of widgets:

* Application Launcher: [main.xml](https://github.com/Sonic-DE/sonic-desktop-interface/blob/master/applets/kickoff/main.xml), [config.qml](https://github.com/Sonic-DE/sonic-desktop-interface/blob/master/applets/kickoff/config.qml), [ConfigGeneral.qml](https://github.com/Sonic-DE/sonic-desktop-interface/blob/master/applets/kickoff/ConfigGeneral.qml)
* Task Manager: [main.xml](https://github.com/Sonic-DE/sonic-desktop-interface/blob/master/applets/taskmanager/main.xml), [config.qml](https://github.com/Sonic-DE/sonic-desktop-interface/blob/master/applets/taskmanager/qml/config.qml), [ConfigAppearance.qml](https://github.com/Sonic-DE/sonic-desktop-interface/blob/master/applets/taskmanager/qml/ConfigAppearance.qml), [ConfigBehavior.qml](https://github.com/Sonic-DE/sonic-desktop-interface/blob/master/applets/taskmanager/qml/ConfigBehavior.qml)

## No-apply control library

The third-party [libconfig](https://github.com/Zren/plasma-applet-lib/tree/master/package/contents/ui/libconfig) is a set of controls that use the pattern above, updating the configuration as soon as you change a value: check boxes, color fields, combo boxes, icon fields, radio button groups, spin boxes, text alignment, text areas and text fields. Each takes a `configKey`:

```qml
import QtQuick
import QtQuick.Controls as QQC2
import org.kde.plasma.plasmoid

QQC2.CheckBox {
    property string configKey: ""
    checked: Plasmoid.configuration[configKey]
    onClicked: Plasmoid.configuration[configKey] = !Plasmoid.configuration[configKey]
}
```

To add it to your widget:

```bash
cd ~/Code/plasmoid-helloworld/package/contents/ui
mkdir -p ./libconfig
cd ./libconfig
wget https://github.com/Zren/plasma-applet-lib/archive/master.zip
unzip -j master.zip plasma-applet-lib-master/package/contents/ui/libconfig/*
rm master.zip
```
