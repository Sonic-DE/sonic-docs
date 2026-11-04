---
title: Colors and themes in Kirigami
description: Make your application follow the user's color scheme.
source_url: https://develop.kde.org/docs/getting-started/kirigami/style-colors/
source_authors: [Carl Schwan, Chris Holland, Claudio Cambra, Jonah Brüchert, Mikhail Zolotukhin, Nicolas Fella, Thiago Sueto, Yuri Chornoivan]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "Kirigami Platform::PlatformTheme (ColorSet enum), SilverLight.colors, examples run with the qml tool"
---

# Colors and themes in Kirigami

Kirigami has a color palette that follows the system colors, so applications integrate with the platform they run on.

All QML components of Kirigami and Qt Quick Controls already follow this palette by default, so these controls usually need no custom coloring.

Primitive components such as [Rectangle](https://doc.qt.io/qt-6/qml-qtquick-rectangle.html) should always be colored with the palette Kirigami provides through the [Kirigami.Theme](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-theme) attached property.

Avoid hardcoded colors in QML, such as `#32b2fa` or `red`. If you really need elements with custom colors, keep them to an area where only custom colors are used (usually the content area of the application, never chrome areas such as toolbars or dialogs). For instance, a hardcoded `black` foreground can't be used over a [Kirigami.Theme.backgroundColor](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-theme#backgroundColor-attached-prop) background: with a dark color scheme the result is black over almost black, with poor contrast. This is an accessibility issue and should be avoided.

> **Note:** If you really need custom colors, check that they have good contrast and meet the [WCAG](https://en.wikipedia.org/wiki/Web_Content_Accessibility_Guidelines) contrast requirements.

## Theme

[Kirigami.Theme](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-theme) is an attached property, so it is available to any QML item. Its properties include all the colors of the palette, and which palette to use, set with the [colorSet](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-theme#colorSet-attached-prop) property.

```qml
import QtQuick
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    height: 300
    width: 400

    pageStack.initialPage: Kirigami.Page {
        Rectangle {
            anchors.centerIn: parent
            implicitHeight: 100
            implicitWidth: 200
            color: Kirigami.Theme.highlightColor
        }
    }
}
```

## Color set

Depending on where a control is, it should use a different color set. For instance, with the Silver Light color scheme the normal background in [views](https://doc.qt.io/qt-6/qtquick-modelviewsdata-modelview.html) is white, while in other regions, such as toolbars or dialogs, it is grey.

If you set a color set on an item, all its child items inherit it recursively, unless their [inherit](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-theme#inherit-attached-prop) property is explicitly set to `false`. Set `inherit` to `false` whenever you want to force a specific color set. This makes it easy to change the colors of a whole hierarchy of items without touching the items themselves.

[Kirigami.Theme](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-theme) supports 7 color sets:

* **View**: for item views; usually the lightest of all (in light color schemes).
* **Window**: for windows and chrome areas. This is the default color set.
* **Button**: for buttons.
* **Selection**: for selected areas.
* **Tooltip**: for tooltips.
* **Complementary**: meant to be complementary to Window; usually dark even in light color schemes. May be used for emphasis in small areas of the application.
* **Header**: for heading areas of applications, such as toolbars.

Here is an example showing how color sets are inherited and can be used to tell components apart. A wide border makes the colors easier to compare.

```qml
// The comments assume the system uses the Silver Light color scheme
import QtQuick
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami


Kirigami.ApplicationWindow {
    height: 500
    width: 800

    Rectangle {
        anchors.fill: parent
        border.width: 5

        // A gray color will be used, as the default color set is Window
        color: Kirigami.Theme.backgroundColor

        Controls.Label {
            // The text will be near-black, as defined in the Window color set for light themes
            text: "Rectangle that uses default background color\nfrom the Window color set"
            padding: 100
        }
        Rectangle {
            anchors.bottom: parent.bottom
            border.width: 5
            width: parent.width
            height: Math.round(parent.height / 2)

            // Use the color set used for Views
            Kirigami.Theme.colorSet: Kirigami.Theme.View
            // Do not inherit from the parent
            Kirigami.Theme.inherit: false
            // This will be a near-white color in light themes
            color: Kirigami.Theme.backgroundColor

            Controls.Label {
                text: "Rectangle that does not inherit the default background color\nand uses the Theme.View color set"
                padding: 50

            }

            Rectangle {
                anchors.bottom: parent.bottom
                anchors.left: parent.left
                border.width: 5
                width: Math.round(parent.width / 2)
                height: Math.round(parent.height / 2)

                // This will be a near-white color too, as the color set
                // is inherited from the parent and will be View
                color: Kirigami.Theme.backgroundColor

                Controls.Label {
                    // The text will be near-black, as defined in the View color set for light themes
                    text: "Rectangle that inherits the Theme.View color set"
                    anchors.centerIn: parent
                }
            }

            Rectangle {
                anchors.bottom: parent.bottom
                anchors.right: parent.right
                border.width: 5
                width: Math.round(parent.width / 2)
                height: Math.round(parent.height / 2)

                // Use the Complementary set
                Kirigami.Theme.colorSet: Kirigami.Theme.Complementary
                // Do not inherit from the parent
                Kirigami.Theme.inherit: false
                // This will be near-black as the background color
                // of the Complementary color set is dark in light themes
                color: Kirigami.Theme.backgroundColor

                Controls.Label {
                    // The text will be near-white, as defined in the Complementary color set for light themes
                    text: "Rectangle that does not inherit the Theme.View\nand uses Theme.Complementary instead"
                    anchors.centerIn: parent
                }
            }
        }
    }
}
```

## Using custom colors

Hardcoded colors are discouraged, but Kirigami offers a more maintainable way to give an item and all its children a custom palette, so the custom colors are defined in one place only:

```qml
import QtQuick
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Custom colors"
    height: 300
    width: 300

    Rectangle {
        anchors.fill: parent
        Kirigami.Theme.inherit: false
        // NOTE: regardless of the color set used, it is recommended
        // to replace all available colors in Theme, to avoid
        // badly contrasting colors

        Kirigami.Theme.colorSet: Kirigami.Theme.Window
        Kirigami.Theme.backgroundColor: "#b9d795"
        Kirigami.Theme.textColor: "#465c2b"
        Kirigami.Theme.highlightColor: "#89e51c"
        // Redefine all the other colors you want

        // This will be "#b9d795"
        color: Kirigami.Theme.backgroundColor

        Rectangle {
            // This will be "#465c2b"
            anchors.centerIn: parent
            height: Math.round(parent.height / 2)
            width: Math.round(parent.width / 2)
            color: Kirigami.Theme.textColor
        }
    }
}
```
