---
title: QML
description: Learn the basics of QML.
source_url: https://develop.kde.org/docs/plasma/widget/qml/
source_authors: [Alexander Hau, Alexander Lohnau, Carl Schwan, Chris Holland, Christoph Dreier, Claudius Ellsel, David Edmundson, Florian Ruechel, Fushan Wen, Johannes Zarl-Zierl, Joshua Goins, Kunda Ki, Marco Martin, Mariusz Libera, Michael Pyne, Mikhail Zolotukhin, Nate Graham, Nicolas Fella, Parth Dhiman, Paul Brown, Plata Hill, Raresh Rus, Rony Bou Moujahed, Thiago Sueto, Tino Lorenz, Tobias Fella, Yaron Shahrabani, Zren (Chris Holland), ivan tkachenko, yaniss khima]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "Qt 6.11 documentation; default sizes, layout spacing, and the sizes of items in a ColumnLayout measured with the qml tool; examples checked with qmllint"
---

# QML

This is a quick introduction to QML. If you are already comfortable with it, skip to the next section.

The official QML tutorial is in the [QML documentation](https://doc.qt.io/qt-6/qtqml-syntax-basics.html).

## Item

An [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html) is a simple visible object. It can have children as well. Items have a default width and height of 0px and don't grow to fit their contents. So unlike the HTML box model, you need to use layouts or anchors.

The root of a widget is a `PlasmoidItem`, which is an Item too.

```qml
import QtQuick
import org.kde.plasma.plasmoid

PlasmoidItem {
    id: widget

    Item {
        id: childItemA
    }

    Item {
        id: childItemB
    }
}
```

## Rectangle

To draw a colored rectangle, use a [Rectangle](https://doc.qt.io/qt-6/qml-qtquick-rectangle.html). For its other properties, like border color and width, read its [page in the QML documentation](https://doc.qt.io/qt-6/qml-qtquick-rectangle.html).

```qml
import QtQuick
import org.kde.plasma.plasmoid

PlasmoidItem {
    Rectangle {
        anchors.fill: parent
        color: "#0ff" // Teal
    }
}
```

## Items are 0px wide by default

By default, an [Item](https://doc.qt.io/qt-6/qml-qtquick-item.html) doesn't expand to fit its contents, nor to fit the width of its parent (like a `<div>` in HTML).

In this example, only the teal rectangle is visible, since the green rectangle has the default width and height of 0px.

```qml
import QtQuick
import org.kde.plasma.plasmoid

PlasmoidItem {
    Rectangle {
        anchors.fill: parent
        color: "#0ff" // Teal

        Rectangle { // We need to set the size of this one.
            color: "#0f0" // Green
        }
    }
}
```

## anchors.fill

Here the green rectangle resizes to its parent, the teal rectangle, and covers it completely, so only the green rectangle is visible.

```qml
import QtQuick
import org.kde.plasma.plasmoid

PlasmoidItem {
    Rectangle {
        anchors.fill: parent
        color: "#0ff" // Teal

        Rectangle {
            color: "#0f0" // Green
            anchors.fill: parent // The same size as the parent.
        }
    }
}
```

## anchors.bottom

Here we anchor the green rectangle to the bottom right and make it half the width and height of the teal rectangle, so we end up with a rectangle that is 3/4 teal and 1/4 green.

Other ways to use `anchors` properties are in the QML documentation pages on [Positioning with Anchors](https://doc.qt.io/qt-6/qtquick-positioning-anchors.html) and the [`Item.anchors` property group](https://doc.qt.io/qt-6/qml-qtquick-item.html#anchors-prop).

```qml
import QtQuick
import org.kde.plasma.plasmoid

PlasmoidItem {
    Rectangle {
        anchors.fill: parent
        color: "#0ff" // Teal

        Rectangle {
            color: "#0f0" // Green
            anchors.right: parent.right
            anchors.bottom: parent.bottom
            width: parent.width / 2
            height: parent.height / 2
        }
    }
}
```

## ColumnLayout

To stack a number of items on top of each other, use a [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html).

This example uses labels, which are fancy [Text](https://doc.qt.io/qt-6/qml-qtquick-text.html) items that follow the desktop's color theme. They have a default font size, and so their own default height, so they are stacked on top of each other.

If the `ColumnLayout` is taller than its contents, the children have spacing between them.

```qml
import QtQuick
import QtQuick.Layouts
import org.kde.plasma.plasmoid
import org.kde.plasma.components as PlasmaComponents

PlasmoidItem {
    ColumnLayout {
        anchors.fill: parent

        PlasmaComponents.Label {
            text: "Item 1"
        }
        PlasmaComponents.Label {
            text: "Item 2"
        }
    }
}
```

## Layout.fillWidth: true

If you want an item to scale to its parent's width, you can try setting it to the parent's width (which doesn't work in a layout) or anchoring it to the left and right (which works, but gives a warning).

In a [Layout](https://doc.qt.io/qt-6/qml-qtquick-layouts-layout.html), the proper way is the special attached property `Layout.fillWidth`. Setting it to `true` makes the item scale to fill the empty space. Likewise, set sizes in a layout with `Layout.preferredWidth` and `Layout.preferredHeight` rather than `width` and `height`.

The other properties related to layouts are in the [Layout documentation](https://doc.qt.io/qt-6/qml-qtquick-layouts-layout.html).

```qml
import QtQuick
import QtQuick.Layouts
import org.kde.plasma.plasmoid

PlasmoidItem {
    ColumnLayout {
        anchors.fill: parent

        Rectangle {
            color: "#f00" // Red
            Layout.preferredHeight: 40
            Layout.fillWidth: true
        }
        Rectangle {
            color: "#0f0" // Green
            Layout.preferredHeight: 40
            width: parent.width // Does not work
        }
        Rectangle {
            color: "#00f" // Blue
            Layout.preferredHeight: 40
            Layout.preferredWidth: 40 // Does not fill parent
        }
        Rectangle {
            color: "#ff0" // Yellow
            Layout.preferredHeight: 40
            anchors.left: parent.left
            anchors.right: parent.right
            // Anchors in a ColumnLayout give an "undefined behavior" warning.
        }
    }
}
```

## Layout.fillHeight: true

To make one item (or several) in a layout expand to take up the unused space, use `Layout.fillHeight: true`.

```qml
import QtQuick
import QtQuick.Layouts
import org.kde.plasma.plasmoid

PlasmoidItem {
    ColumnLayout {
        anchors.fill: parent

        Rectangle {
            color: "#f00" // Red
            Layout.preferredHeight: 40
            Layout.fillWidth: true
        }
        Rectangle {
            color: "#0f0" // Green
            Layout.fillHeight: true
            Layout.fillWidth: true
        }
        Rectangle {
            color: "#00f" // Blue
            Layout.fillHeight: true
            Layout.fillWidth: true
        }
        Rectangle {
            color: "#ff0" // Yellow
            Layout.preferredHeight: 40
            Layout.fillWidth: true
        }
    }
}
```

## Spacing between items in a layout

There is still spacing between the items above, because the default [ColumnLayout.spacing](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html#spacing-prop) is `5`. Setting it to `0` removes the extra space.

```qml
import QtQuick
import QtQuick.Layouts
import org.kde.plasma.plasmoid

PlasmoidItem {
    ColumnLayout {
        anchors.fill: parent
        spacing: 0

        Rectangle {
            color: "#f00" // Red
            Layout.preferredHeight: 40
            Layout.fillWidth: true
        }
        Rectangle {
            color: "#0f0" // Green
            Layout.fillHeight: true
            Layout.fillWidth: true
        }
        Rectangle {
            color: "#00f" // Blue
            Layout.fillHeight: true
            Layout.fillWidth: true
        }
        Rectangle {
            color: "#ff0" // Yellow
            Layout.preferredHeight: 40
            Layout.fillWidth: true
        }
    }
}
```

## Other layouts

There are also [RowLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-rowlayout.html) and [GridLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-gridlayout.html). Lastly, [Flow](https://doc.qt.io/qt-6/qml-qtquick-flow.html) treats its contents as if they all had the CSS `display: inline-block`.

```qml
import QtQuick
import QtQuick.Layouts
import org.kde.plasma.plasmoid
import org.kde.plasma.components as PlasmaComponents

PlasmoidItem {
    RowLayout {
        anchors.fill: parent

        PlasmaComponents.Label {
            text: "Item 1"
        }
        PlasmaComponents.Label {
            text: "Item 2"
        }
    }
}
```
