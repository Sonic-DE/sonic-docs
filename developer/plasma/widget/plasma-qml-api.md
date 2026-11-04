---
title: The widget QML API
description: A rundown of the QML types SonicDE ships for desktop widgets.
source_url: https://develop.kde.org/docs/plasma/widget/plasma-qml-api/
source_authors: [Alexander Hau, Alexander Lohnau, Carl Schwan, Chris Holland, Christoph Dreier, Claudius Ellsel, David Edmundson, Florian Ruechel, Fushan Wen, Johannes Zarl-Zierl, Joshua Goins, Kunda Ki, Marco Martin, Mariusz Libera, Michael Pyne, Mikhail Zolotukhin, Nate Graham, Nicolas Fella, Parth Dhiman, Paul Brown, Plata Hill, Raresh Rus, Rony Bou Moujahed, Thiago Sueto, Tino Lorenz, Tobias Fella, Yaron Shahrabani, Zren (Chris Holland), ivan tkachenko, yaniss khima]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "plasmacomponents3 and plasmaextracomponents sources in sonic-interface-libraries; org.kde.plasma.core qmltypes; Kirigami Units and PlatformTheme in sonic-frameworks-quick-ui; KSvg in sonic-frameworks-svg; examples checked with qmllint and run together on the built libraries under Xvfb"
---

# The widget QML API

SonicDE's frameworks add a number of QML types to what Qt ships. The API documentation describes each type's properties: see [PlasmaComponents](/docs/api/plasmacomponents/org-kde-plasma-components-qmlmodule), [PlasmaExtras](/docs/api/plasmaextras/org-kde-plasma-extras-qmlmodule), [PlasmaCore](/docs/api/plasmacore/org-kde-plasma-core-qmlmodule), [Kirigami](/docs/api/kirigami/kirigami-index) and [KSvg](/docs/api/ksvgqml/org-kde-ksvg-qmlmodule). The sources of the widget components are in [`sonic-interface-libraries/src/declarativeimports`](https://github.com/Sonic-DE/sonic-interface-libraries/tree/master/src/declarativeimports).

The root item of a widget's `main.qml` must be a `PlasmoidItem`, as [the QML page](qml.md) explains. To stay short, the examples here show only the items that go inside it.

## PlasmaComponents controls

PlasmaComponents is a QML library that extends the [Qt Quick Controls](https://doc.qt.io/qt-6/qtquickcontrols-index.html) with defaults for desktop widgets. Its controls are drawn with the SVGs of the [desktop theme](../theme/quickstart.md), and they follow the color scheme of the panel they are in.

They inherit from Qt Quick Controls and have the same API, so the Qt documentation applies. For the behavior specific to SonicDE, read each control's QML source in [`plasmacomponents3/`](https://github.com/Sonic-DE/sonic-interface-libraries/tree/master/src/declarativeimports/plasmacomponents3).

```qml
import org.kde.plasma.components as PlasmaComponents
```

### Label

A [Label](https://doc.qt.io/qt-6/qml-qtquick-controls-label.html) displays text to the user. Plasma's [`Label.qml`](https://github.com/Sonic-DE/sonic-interface-libraries/blob/master/src/declarativeimports/plasmacomponents3/Label.qml) adds defaults such as a text color that follows the panel's color scheme.

```qml
PlasmaComponents.Label {
    text: i18n("Hello World")
}
```

### CheckBox

A [CheckBox](https://doc.qt.io/qt-6/qml-qtquick-controls-checkbox.html) is a simple toggle. Source: [`CheckBox.qml`](https://github.com/Sonic-DE/sonic-interface-libraries/blob/master/src/declarativeimports/plasmacomponents3/CheckBox.qml).

```qml
PlasmaComponents.CheckBox {
    text: i18n("Hello World")
    checked: true
}
```

### RadioButton

A [RadioButton](https://doc.qt.io/qt-6/qml-qtquick-controls-radiobutton.html) offers one of several choices. Source: [`RadioButton.qml`](https://github.com/Sonic-DE/sonic-interface-libraries/blob/master/src/declarativeimports/plasmacomponents3/RadioButton.qml).

With more than three options, the [Human Interface Guidelines](../../hig/index.md) suggest a ComboBox instead.

```qml
import QtQuick.Layouts

ColumnLayout {
    PlasmaComponents.RadioButton {
        text: i18n("Top")
        checked: true
        autoExclusive: true
    }
    PlasmaComponents.RadioButton {
        text: i18n("Bottom")
        autoExclusive: true
    }
}
```

### ComboBox

A [ComboBox](https://doc.qt.io/qt-6/qml-qtquick-controls-combobox.html) is a dropdown menu. Read the selected value from `currentValue`. Source: [`ComboBox.qml`](https://github.com/Sonic-DE/sonic-interface-libraries/blob/master/src/declarativeimports/plasmacomponents3/ComboBox.qml).

```qml
PlasmaComponents.ComboBox {
    textRole: "text"
    valueRole: "value"
    model: [
        { value: "a", text: i18n("A") },
        { value: "b", text: i18n("B") },
        { value: "c", text: i18n("C") },
    ]
}
```

### Slider

A [Slider](https://doc.qt.io/qt-6/qml-qtquick-controls-slider.html) controls an integer or real number. This example keeps the label next to it wide enough for the largest value, so the slider doesn't change size as the value changes. Source: [`Slider.qml`](https://github.com/Sonic-DE/sonic-interface-libraries/blob/master/src/declarativeimports/plasmacomponents3/Slider.qml).

```qml
import QtQuick
import QtQuick.Layouts

RowLayout {
    PlasmaComponents.Slider {
        id: slider
        Layout.fillWidth: true
        from: 0
        to: 100
        value: 50
        stepSize: 5
    }
    PlasmaComponents.Label {
        id: sliderValueLabel
        function formatText(value) {
            return i18n("%1%", value)
        }
        text: formatText(slider.value)

        TextMetrics {
            id: textMetrics
            font: sliderValueLabel.font
            text: sliderValueLabel.formatText(slider.to)
        }
        Layout.minimumWidth: textMetrics.width
    }
}
```

### SpinBox

A [SpinBox](https://doc.qt.io/qt-6/qml-qtquick-controls-spinbox.html) also controls a number, with buttons and a text field. Source: [`SpinBox.qml`](https://github.com/Sonic-DE/sonic-interface-libraries/blob/master/src/declarativeimports/plasmacomponents3/SpinBox.qml).

```qml
import QtQuick.Layouts

RowLayout {
    PlasmaComponents.Label {
        text: i18n("Label:")
        Layout.alignment: Qt.AlignRight
    }
    PlasmaComponents.SpinBox {
        from: 0
        to: 100
        value: 25
        stepSize: 1
    }
}
```

### TextField and TextArea

[TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html) enters one line of text and [TextArea](https://doc.qt.io/qt-6/qml-qtquick-controls-textarea.html) several. Sources: [`TextField.qml`](https://github.com/Sonic-DE/sonic-interface-libraries/blob/master/src/declarativeimports/plasmacomponents3/TextField.qml), [`TextArea.qml`](https://github.com/Sonic-DE/sonic-interface-libraries/blob/master/src/declarativeimports/plasmacomponents3/TextArea.qml).

```qml
import QtQuick.Layouts

RowLayout {
    PlasmaComponents.Label {
        Layout.alignment: Qt.AlignRight
        text: i18n("Name:")
    }
    PlasmaComponents.TextField {
        placeholderText: i18n("Name")
    }
}
```

```qml
PlasmaComponents.TextArea {
    text: "Lorem ipsum\ndolor sit amet,\nconsectetur adipisicing elit"
}
```

### Button and ToolButton

[Button](https://doc.qt.io/qt-6/qml-qtquick-controls-button.html) is a regular button and [ToolButton](https://doc.qt.io/qt-6/qml-qtquick-controls-toolbutton.html) its flat version. Sources: [`Button.qml`](https://github.com/Sonic-DE/sonic-interface-libraries/blob/master/src/declarativeimports/plasmacomponents3/Button.qml), [`ToolButton.qml`](https://github.com/Sonic-DE/sonic-interface-libraries/blob/master/src/declarativeimports/plasmacomponents3/ToolButton.qml).

```qml
PlasmaComponents.Button {
    icon.name: "view-refresh"
    text: i18n("Refresh")
}
```

```qml
PlasmaComponents.ToolButton {
    icon.name: "view-refresh-symbolic"
    text: i18n("Refresh")
}
```

### ScrollView

A [ScrollView](https://doc.qt.io/qt-6/qml-qtquick-controls-scrollview.html) adds a scrollbar to manage overflow. Source: [`ScrollView.qml`](https://github.com/Sonic-DE/sonic-interface-libraries/blob/master/src/declarativeimports/plasmacomponents3/ScrollView.qml).

```qml
import QtQuick

PlasmaComponents.ScrollView {
    ListView {
        model: 100
        delegate: PlasmaComponents.CheckBox {
            required property int index
            text: i18n("CheckBox #%1", index + 1)
        }
    }
}
```

### BusyIndicator

A [BusyIndicator](https://doc.qt.io/qt-6/qml-qtquick-controls-busyindicator.html) draws `widgets/busywidget.svg` from the desktop theme and spins it. If the animation speed in System Settings is set to instant, it doesn't rotate. Sources: [`BusyIndicator.qml`](https://github.com/Sonic-DE/sonic-interface-libraries/blob/master/src/declarativeimports/plasmacomponents3/BusyIndicator.qml), [the default `busywidget.svg`](https://github.com/Sonic-DE/sonic-interface-libraries/blob/master/src/desktoptheme/default/widgets/busywidget.svg).

## PlasmaExtras

PlasmaExtras holds components with an API of their own, made for widgets. Among them are [Heading](/docs/api/plasmaextras/qml-org-kde-plasma-extras-heading), `PlasmoidHeading`, `Representation`, `PlaceholderMessage` and `ExpandableListItem`.

```qml
import org.kde.plasma.extras as PlasmaExtras
```

### Heading

`PlasmaExtras.Heading` is a label with a preset size for its `level`, wrapped by default. For a block of body text, use a `PlasmaComponents.Label` with `wrapMode: Text.Wrap`.

```qml
import QtQuick
import QtQuick.Layouts

ColumnLayout {
    spacing: 0

    Repeater {
        model: 5
        PlasmaExtras.Heading {
            required property int index
            Layout.fillWidth: true
            level: index + 1
            text: i18n("Heading level %1", level)
        }
    }

    PlasmaComponents.Label {
        Layout.fillWidth: true
        wrapMode: Text.Wrap
        text: i18n("Lorem ipsum dolor sit amet, consectetur adipiscing elit.")
    }
}
```

## PlasmaCore

```qml
import org.kde.plasma.core as PlasmaCore
```

`PlasmaCore` has the widget-level types [ToolTipArea](/docs/api/plasmacore/qml-org-kde-plasma-core-tooltiparea), [WindowThumbnail](/docs/api/plasmacore/qml-org-kde-plasma-core-windowthumbnail), `Dialog`, `AppletPopup` and `Window`, along with the enums of [Plasma::Types](/docs/api/plasma/plasma-types), such as form factors and screen locations.

Colors, sizes and icons are no longer in `PlasmaCore`; [the porting guide](porting-kf6.md) lists what replaced them. They are described below.

## Icons and SVGs

[Kirigami.Icon](/docs/api/kirigami/qml-org-kde-kirigami-primitives-icon) draws icons.

```qml
import org.kde.kirigami as Kirigami

Kirigami.Icon {
    source: "view-refresh"
    implicitWidth: Kirigami.Units.iconSizes.small
    implicitHeight: implicitWidth
}
```

KSvg draws SVGs, colored with the desktop theme's palette: [SvgItem](/docs/api/ksvgqml/qml-org-kde-ksvg-svgitem) one element of an image, [FrameSvgItem](/docs/api/ksvgqml/qml-org-kde-ksvg-framesvgitem) a resizable frame, and [Svg](/docs/api/ksvgqml/qml-org-kde-ksvg-svg) the image itself.

```qml
import org.kde.ksvg as KSvg

KSvg.SvgItem {
    imagePath: "widgets/configuration-icons"
    elementId: "configure"
}
```

```qml
KSvg.FrameSvgItem {
    imagePath: "widgets/background"
}
```

## Kirigami.Theme

[Kirigami.Theme](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-theme) holds the current color palette and the fonts.

- `Kirigami.Theme.textColor`
- `Kirigami.Theme.disabledTextColor`
- `Kirigami.Theme.highlightColor`
- `Kirigami.Theme.highlightedTextColor`
- `Kirigami.Theme.backgroundColor`
- `Kirigami.Theme.alternateBackgroundColor`
- `Kirigami.Theme.linkColor`
- `Kirigami.Theme.visitedLinkColor`
- `Kirigami.Theme.positiveTextColor`
- `Kirigami.Theme.neutralTextColor`
- `Kirigami.Theme.negativeTextColor`
- `Kirigami.Theme.defaultFont`
- `Kirigami.Theme.smallFont`
- `Kirigami.Theme.fixedWidthFont`

There are no separate properties for the color groups. Instead, an item sets `Kirigami.Theme.colorSet` to one of `View`, `Window`, `Button`, `Selection`, `Tooltip`, `Complementary` or `Header`, and `Kirigami.Theme.inherit: false` to stop following its parent; the same color properties then give the colors of that set. [Colors and themes](../../kirigami/colors.md) describes this in more detail.

## Kirigami.Units

[Kirigami.Units](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-units) holds preset values, so that widgets stay consistent with the rest of the desktop.

### Spacing

- `Kirigami.Units.gridUnit`: 18
- `Kirigami.Units.smallSpacing`: 4
- `Kirigami.Units.mediumSpacing`: 6
- `Kirigami.Units.largeSpacing`: 8

These are logical pixels: there is no `devicePixelRatio` to multiply by, because Qt scales the whole interface for the display. A plain size such as the `4` below scales the same way.

```qml
import QtQuick
import QtQuick.Layouts
import org.kde.kirigami as Kirigami

RowLayout {
    spacing: Kirigami.Units.smallSpacing
    Rectangle {
        implicitWidth: 4
        Layout.fillHeight: true
        color: Kirigami.Theme.highlightColor
    }
    PlasmaComponents.Label {
        text: i18n("Label")
    }
}
```

### Icon sizes

- `Kirigami.Units.iconSizes.small`: 16
- `Kirigami.Units.iconSizes.smallMedium`: 22
- `Kirigami.Units.iconSizes.medium`: 32
- `Kirigami.Units.iconSizes.large`: 48
- `Kirigami.Units.iconSizes.huge`: 64
- `Kirigami.Units.iconSizes.enormous`: 128

`iconSizes.sizeForLabels` is the icon size that fits the height of the default font, and `iconSizes.roundedIconSize(value)` rounds a size down to a standard icon size (sizes below 16 or from 64 up stay as they are).

### Durations

These are scaled by the animation speed in System Settings; the values below are at the default speed.

- `Kirigami.Units.veryShortDuration`: 50 ms
- `Kirigami.Units.shortDuration`: 100 ms
- `Kirigami.Units.longDuration`: 200 ms
- `Kirigami.Units.veryLongDuration`: 400 ms

`Kirigami.Units.humanMoment` (2000 ms) isn't scaled and shouldn't be used for animations. Use it to measure how long to wait before telling the user something, or as the limit before something starts automatically.
