---
title: Controls and interactive elements
description: Make your applications more interactive with buttons, selection controls, sliders and text fields.
source_url: https://develop.kde.org/docs/getting-started/kirigami/components-controls/
source_authors: [Carl Schwan, Claudio Cambra, Jeongu Kim, Mikhail Zolotukhin, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "Qt 6.11 Qt Quick Controls documentation, SonicDE's desktop Qt Quick style (Slider.qml) and Silver widget style (button frame and slider groove rendering); examples run with the qml tool"
---

# Controls and interactive elements

Kirigami applications use a wide selection of interactive elements from Qt. Each type has slightly different interaction styles, visual styles and functionality. Using the right type of control in your application helps make your user interface more responsive and intuitive.

## Buttons

In Kirigami applications we use the Qt Quick Controls [Button](https://doc.qt.io/qt-6/qml-qtquick-controls-button.html). Using it is straightforward: set its [text](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html#text-prop) property, and put whatever it should do in its [onClicked](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html#clicked-signal) handler.

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Controls.Button"
    width: 400
    height: 400
    pageStack.initialPage: Kirigami.Page {
        ColumnLayout {
            anchors.fill: parent
            Controls.Button {
                Layout.alignment: Qt.AlignCenter
                text: "Beep!"
                onClicked: showPassiveNotification("Boop!")
            }
        }
    }
}
```

### Toggleable buttons

Buttons can be made toggleable: they then stay pressed until clicked once more. Turn this on by setting their [checkable](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html#checkable-prop) property to `true`; to have a button toggled on by default, also set [checked](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html#checked-prop) to `true`.

To get the most out of toggleable buttons, use the `onCheckedChanged` signal handler, [generated automatically](https://doc.qt.io/qt-6/qtqml-syntax-signals.html#property-change-signal-handlers) for the [checked](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html#checked-prop) property. It works like `onClicked`, except that it runs when the button's state changes. `checked` is a boolean property, which comes in handy for specific use cases.

In this example, a toggleable button sets the visibility of an inline drawer:

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Controls.Button (toggleable version)"
    width: 400
    height: 400
    pageStack.initialPage: Kirigami.Page {
        ColumnLayout {
            anchors.fill: parent
            Controls.Button {
                Layout.alignment: Qt.AlignCenter
                text: "Hide inline drawer"
                checkable: true
                checked: true
                onCheckedChanged: myDrawer.visible = checked
            }

            Kirigami.OverlayDrawer {
                id: myDrawer
                edge: Qt.BottomEdge
                modal: false

                contentItem: Controls.Label {
                    text: "Peekaboo!"
                }
            }
        }
    }
}
```

With SonicDE's Silver style it can be hard to tell whether a button is toggled: a toggled button is only slightly darker than a normal one, while a pressed button is tinted with the highlight color. Keep this in mind when designing your application: a different control might be more user-friendly.

### Toolbar buttons

There is a button type meant for toolbars, [Controls.ToolButton](https://doc.qt.io/qt-6/qml-qtquick-controls-toolbutton.html). The most obvious difference from a conventional [Button](https://doc.qt.io/qt-6/qml-qtquick-controls-button.html) is the styling: tool buttons are flat (though you can change this with the boolean [flat](https://doc.qt.io/qt-6/qml-qtquick-controls-button.html#flat-prop) property).

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Controls.ToolButton"
    width: 600
    height: 600

    header: Controls.ToolBar {
        RowLayout {
            anchors.fill: parent
            Controls.ToolButton {
                icon.name: "application-menu-symbolic"
                onClicked: showPassiveNotification("Kirigami Pages and Actions are better!")
            }
            Controls.Label {
                text: "Global ToolBar"
                horizontalAlignment: Qt.AlignHCenter
                verticalAlignment: Qt.AlignVCenter
                Layout.fillWidth: true
            }
            Controls.ToolButton {
                text: "Beep!"
                onClicked: showPassiveNotification("ToolButton boop!")
            }
        }
    }
}
```

## Selection controls

Selection controls let users make a choice or pick an option. Different types suit different situations.

### Checkboxes

A [Controls.CheckBox](https://doc.qt.io/qt-6/qml-qtquick-controls-checkbox.html) is meant for options where the choices aren't exclusive and each option has a clear alternative.

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Controls.CheckBox"
    width: 400
    height: 400
    pageStack.initialPage: Kirigami.Page {
        ColumnLayout {
            anchors.left: parent.left
            anchors.right: parent.right
            Controls.CheckBox {
                Layout.alignment: Qt.AlignHCenter
                text: "This checkbox is checked!"
                checked: true
            }
            Controls.CheckBox {
                Layout.alignment: Qt.AlignHCenter
                text: "This checkbox is not checked!"
                checked: false
            }
        }
    }
}
```

As you can see, they are simple to use. The [checked](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html#checked-prop) property holds a boolean value saying whether they are checked.

### Radio buttons

A [Controls.RadioButton](https://doc.qt.io/qt-6/qml-qtquick-controls-radiobutton.html) is designed for situations where the user must choose one option from a set of several.

Radio buttons are [exclusive](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html#autoExclusive-prop) by default: only one button can be checked within the same parent item.

Like checkboxes, they can be checked or unchecked by default with the [checked](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html#checked-prop) property.

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Controls.RadioButton"
    width: 400
    height: 400
    pageStack.initialPage: Kirigami.Page {

        ColumnLayout {
            anchors.left: parent.left
            anchors.right: parent.right
            Controls.RadioButton {
                Layout.alignment: Qt.AlignCenter
                text: "Tick!"
                checked: true
            }
            Controls.RadioButton {
                Layout.alignment: Qt.AlignCenter
                text: "Tock!"
                checked: false
            }
        }
    }
}
```

### Switches

On the desktop, changing settings usually means changing the setting and then applying it by clicking an "Apply" or "OK" button. On mobile, we can use a [Controls.Switch](https://doc.qt.io/qt-6/qml-qtquick-controls-switch.html) instead.

Switches toggle between an on and an off state. They can be toggled by clicking or tapping them, or dragged towards the on or off position. Again, the [checked](https://doc.qt.io/qt-6/qml-qtquick-controls-abstractbutton.html#checked-prop) property sets whether a switch is on or off by default.

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Controls.Switch"
    width: 400
    height: 400
    pageStack.initialPage: Kirigami.Page {
        ColumnLayout {
            anchors.fill: parent
            Controls.Switch {
                Layout.alignment: Qt.AlignCenter
                text: "Switchy"
                checked: true
            }
            Controls.Switch {
                Layout.alignment: Qt.AlignCenter
                text: "Swootchy"
                checked: false
            }
        }
    }
}
```

## Sliders

Sliders let users select a value by sliding a handle along a track. There are several types to choose from, depending on the values you want your users to choose.

### Standard and tick-marked sliders

A standard [Controls.Slider](https://doc.qt.io/qt-6/qml-qtquick-controls-slider.html) gives the user very fine control over their selection.

In left-to-right mode, horizontal sliders increase from left to right; in right-to-left mode they go the other way. In both modes, vertical sliders go from the bottom up.

The coloring is a visual indicator of how large the selected value is: the track is filled with the highlight color up to the handle.

Sliders have a few important properties:

- [value](https://doc.qt.io/qt-6/qml-qtquick-controls-slider.html#value-prop): the value at which the handle is placed. You can also set it to give a default starting value.
- [to](https://doc.qt.io/qt-6/qml-qtquick-controls-slider.html#to-prop): the range of the slider, as the maximum value it can go to.
- [orientation](https://doc.qt.io/qt-6/qml-qtquick-controls-slider.html#orientation-prop): set it to [Qt.Vertical](https://doc.qt.io/qt-6/qt.html#Orientation-enum) for a vertical slider.

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Controls.Slider"
    width: 400
    height: 400
    pageStack.initialPage: Kirigami.Page {
        ColumnLayout {
            anchors.fill: parent
            Controls.Slider {
                id: normalSlider
                Layout.alignment: Qt.AlignHCenter
                Layout.fillHeight: true
                orientation: Qt.Vertical
                value: 60
                to: 100
            }
            Controls.Label {
                Layout.alignment: Qt.AlignHCenter
                text: Math.round(normalSlider.value)
            }
        }
    }
}
```

Another useful property is [stepSize](https://doc.qt.io/qt-6/qml-qtquick-controls-slider.html#stepSize-prop). Together with [snapMode](https://doc.qt.io/qt-6/qml-qtquick-controls-slider.html#snapMode-prop) set to `Slider.SnapAlways` (the default, `Slider.NoSnap`, doesn't snap), it makes a slider that snaps to multiples of `stepSize`, and tick marks show those multiples. So with `stepSize` set to `2.0`, the user dragging the handle can only select `0.0`, `2.0`, `4.0` and so on, up to the value of `to`.

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Controls.Slider (with steps)"
    width: 400
    height: 400
    pageStack.initialPage: Kirigami.Page {
        ColumnLayout {
            anchors.fill: parent
            Controls.Slider {
                id: tickmarkedSlider
                Layout.alignment: Qt.AlignHCenter
                Layout.fillWidth: true
                orientation: Qt.Horizontal
                snapMode: Controls.Slider.SnapAlways
                value: 6.0
                to: 10.0
                stepSize: 2.0
            }
            Controls.Label {
                Layout.alignment: Qt.AlignHCenter
                text: tickmarkedSlider.value
            }
        }
    }
}
```

### Range sliders

Qt Quick Controls also provides [Controls.RangeSlider](https://doc.qt.io/qt-6/qml-qtquick-controls-rangeslider.html). It has two handles, so you can define a range of numbers between them.

Two new properties are important: [first.value](https://doc.qt.io/qt-6/qml-qtquick-controls-rangeslider.html#first-prop) and [second.value](https://doc.qt.io/qt-6/qml-qtquick-controls-rangeslider.html#second-prop), which hold the values of the two handles. Like the [value](https://doc.qt.io/qt-6/qml-qtquick-controls-slider.html#value-prop) property of standard sliders, they can be preset.

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Controls.RangeSlider"
    width: 400
    height: 400
    pageStack.initialPage: Kirigami.Page {
        ColumnLayout {
            anchors.fill: parent
            Controls.RangeSlider {
                id: rangeSlider
                Layout.alignment: Qt.AlignHCenter
                to: 10.0
                first.value: 2.0
                second.value: 8.0
                stepSize: 1.0
                snapMode: Controls.Slider.SnapAlways
            }
            RowLayout {
                Layout.alignment: Qt.AlignHCenter
                Layout.fillWidth: true
                Controls.Label {
                    Layout.fillWidth: true
                    text: "The slider's first value is: " + Math.round(rangeSlider.first.value)
                }
                Controls.Label {
                    Layout.fillWidth: true
                    text: "The slider's second value is: " + Math.round(rangeSlider.second.value)
                }
            }
            Controls.Label {
                Layout.alignment: Qt.AlignHCenter
                font.bold: true
                text: "Is the selected range between 2 and 8?"
            }
            Controls.Button {
                Layout.alignment: Qt.AlignHCenter
                icon.name: {
                    if (rangeSlider.first.value >= 2 && rangeSlider.second.value <= 8)
                        return "emblem-checked"
                    else
                        return "emblem-error"
                }
            }
        }
    }
}
```
