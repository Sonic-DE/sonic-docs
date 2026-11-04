---
title: Progress bars and indicators
description: Give your users loading-state information with progress bars.
source_url: https://develop.kde.org/docs/getting-started/kirigami/components-progressbars/
source_authors: [Carl Schwan, Claudio Cambra, Jeongu Kim, Mikhail Zolotukhin, Nicolas Fella, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "Qt 6.11 ProgressBar and BusyIndicator documentation; examples run with the qml tool"
---

# Progress bars and indicators

Whenever your application does something that takes a noticeable amount of time, use a visual element that tells the user something is happening in the background.

Qt Quick Controls provides two useful components for this.

## Progress bar

[Controls.ProgressBar](https://doc.qt.io/qt-6/qml-qtquick-controls-progressbar.html) lets you easily include progress bars in your application. There are four main properties you will need:

- [from](https://doc.qt.io/qt-6/qml-qtquick-controls-progressbar.html#from-prop): the minimum value, represented by the start of the progress bar.
- [to](https://doc.qt.io/qt-6/qml-qtquick-controls-progressbar.html#to-prop): the maximum value, represented by the end of the progress bar.
- [value](https://doc.qt.io/qt-6/qml-qtquick-controls-progressbar.html#value-prop): the current value of the action in progress (for example 50% loaded).
- [indeterminate](https://doc.qt.io/qt-6/qml-qtquick-controls-progressbar.html#indeterminate-prop): if the action in progress has no clear progress value yet, set this to `true` to show the user that something is happening even though its progress isn't known yet.

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Progressbar App"
    width: 400
    height: 400
    pageStack.initialPage: Kirigami.Page {
        ColumnLayout {
            anchors.left: parent.left
            anchors.right: parent.right
            Controls.ProgressBar {
                Layout.fillWidth: true
                from: 0
                to: 100
                value: 50
                indeterminate: false
            }
            Controls.ProgressBar {
                Layout.fillWidth: true
                from: 0
                to: 100
                // value: 50
                indeterminate: true
            }
        }
    }
}
```

## Busy indicator

When loading times are shorter, or measuring progress isn't feasible, use a [Controls.BusyIndicator](https://doc.qt.io/qt-6/qml-qtquick-controls-busyindicator.html) instead. It shows a simple spinning wheel that tells users something is happening.

To stop the indicator, set its [running](https://doc.qt.io/qt-6/qml-qtquick-controls-busyindicator.html#running-prop) property to `false`; the indicator is then hidden, as it is only visible while `running` is `true`.

```qml
import QtQuick
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Progressbar App"
    width: 400
    height: 400
    pageStack.initialPage: Kirigami.Page {
        actions: [
            Kirigami.Action {
                text: "Toggle busy indicator"
                onTriggered: indicator.running ? indicator.running = false : indicator.running = true
            }
        ]
        Controls.BusyIndicator {
            id: indicator
            anchors.centerIn: parent
        }
    }
}
```
