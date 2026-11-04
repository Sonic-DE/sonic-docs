---
title: Typography
description: Laying out your text content.
source_url: https://develop.kde.org/docs/getting-started/kirigami/style-typography/
source_authors: [Carl Schwan, Claudio Cambra, Mikhail Zolotukhin, Nicolas Fella, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "Kirigami Heading.qml and PlatformTheme::defaultFont, Qt 6.11 Text documentation, examples run with the qml tool"
---

# Typography

> **Note:** To make the text examples clearer, this tutorial puts them in an AbstractCard. A better way to get the same result is a [Kirigami Addons FormCard](addons-introduction.md).

## Headings

Kirigami provides a [Heading](/docs/api/kirigami/qml-org-kde-kirigami-heading) component for page or section titles. Its [level](/docs/api/kirigami/qml-org-kde-kirigami-heading#level-prop) ranges from 1 (largest) to 5 (smallest).

```qml
import QtQuick
import QtQuick.Layouts
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Kirigami Heading"
    height: 400
    width: 400

    pageStack.initialPage: Kirigami.Page {
        Kirigami.AbstractCard {
            anchors.fill: parent
            contentItem: ColumnLayout {
                anchors.fill: parent
                Kirigami.Heading {
                    text: "Heading level 1"
                    level: 1
                }
                Kirigami.Heading {
                    text: "Heading level 2"
                    level: 2
                }
                Kirigami.Heading {
                    text: "Heading level 3"
                    level: 3
                }
                Kirigami.Heading {
                    text: "Heading level 4"
                    level: 4
                }
                Kirigami.Heading {
                    text: "Heading level 5"
                    level: 5
                }
            }
        }
    }
}
```

## Labels

Text elements should use the [Label](https://doc.qt.io/qt-6/qml-qtquick-controls-label.html) component from Qt Quick Controls.

```qml
import QtQuick
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Controls Label"
    height: 400
    width: 400

    pageStack.initialPage: Kirigami.Page {
        Kirigami.AbstractCard {
            anchors.fill: parent
            contentItem: Controls.Label {
                    text: "My text"
            }
        }
    }
}
```

## Text alignment

You can align text elements with the [horizontalAlignment](https://doc.qt.io/qt-6/qml-qtquick-text.html#horizontalAlignment-prop) and [verticalAlignment](https://doc.qt.io/qt-6/qml-qtquick-text.html#verticalAlignment-prop) properties.

Centered horizontally:

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Controls Horizontal Center"
    height: 400
    width: 400

    pageStack.initialPage: Kirigami.Page {
        Kirigami.AbstractCard {
            anchors.fill: parent
            contentItem: ColumnLayout {
                Kirigami.Heading {
                    Layout.fillWidth: true
                    horizontalAlignment: Text.AlignHCenter
                    text: "Welcome to my application"
                    wrapMode: Text.Wrap
                }
                Controls.Label {
                    Layout.fillWidth: true
                    horizontalAlignment: Text.AlignHCenter
                    text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere erat a ante."
                    wrapMode: Text.Wrap
                }
            }
        }
    }
}
```

Aligned to the right:

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Horizontal Align Right"
    height: 400
    width: 400

    pageStack.initialPage: Kirigami.Page {
        Kirigami.AbstractCard {
            anchors.fill: parent
            contentItem: ColumnLayout {
                Kirigami.Heading {
                    Layout.fillWidth: true
                    horizontalAlignment: Text.AlignRight
                    text: "Welcome to my application"
                    wrapMode: Text.Wrap
                }
                Controls.Label {
                    Layout.fillWidth: true
                    horizontalAlignment: Text.AlignRight
                    text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere erat a ante."
                    wrapMode: Text.Wrap
                }
            }
        }
    }
}
```

The heading aligned to the bottom of its area and the label to the top:

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Bottom and Top"
    height: 400
    width: 400

    pageStack.initialPage: Kirigami.Page {
        Kirigami.AbstractCard {
            anchors.fill: parent
            contentItem: ColumnLayout {
                Kirigami.Heading {
                    Layout.fillWidth: true
                    Layout.fillHeight: true
                    verticalAlignment: Text.AlignBottom
                    text: "Welcome to my application"
                    wrapMode: Text.WordWrap
                }
                Controls.Label {
                    Layout.fillWidth: true
                    Layout.fillHeight: true
                    verticalAlignment: Text.AlignTop
                    text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere erat a ante."
                    wrapMode: Text.WordWrap
                }
            }
        }
    }
}
```

And the other way round:

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Top and Bottom"
    height: 400
    width: 400

    pageStack.initialPage: Kirigami.Page {
        Kirigami.AbstractCard {
            anchors.fill: parent
            contentItem: ColumnLayout {
                Kirigami.Heading {
                    Layout.fillWidth: true
                    Layout.fillHeight: true
                    verticalAlignment: Text.AlignTop
                    text: "Welcome to my application"
                    wrapMode: Text.WordWrap
                }
                Controls.Label {
                    Layout.fillWidth: true
                    Layout.fillHeight: true
                    verticalAlignment: Text.AlignBottom
                    text: "Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer posuere erat a ante."
                    wrapMode: Text.WordWrap
                }
            }
        }
    }
}
```

## Rich text

QML can display (and edit) rich text. The [textFormat](https://doc.qt.io/qt-6/qml-qtquick-text.html#textFormat-prop) property controls how text is interpreted. Its default, `Text.AutoText`, treats the text as styled text when it detects an HTML tag on the first line, so the example below shows a bold title, a list and a struck-out item.

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Controls Label with rich text"
    height: 400
    width: 400

    pageStack.initialPage: Kirigami.Page {
        Kirigami.AbstractCard {
            anchors.fill: parent
            contentItem: Controls.Label {
                text: "<p><strong>List of fruits to purchase</strong></p>
                <ul>
                <li>Apple</li>
                <li>Cherry</li>
                <li>Orange</li>
                <li><del>Banana</del></li>
                </ul>
                <p>Kris already got some bananas yesterday.</p>"
            }
        }
    }
}
```

## Theme

The font size of the [Kirigami.Theme](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-theme) is available to your application as `Kirigami.Theme.defaultFont.pointSize`.
