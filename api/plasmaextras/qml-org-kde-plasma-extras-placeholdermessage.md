---
title: "PlaceholderMessage QML Type"
description: "A placeholder message indicating that a list view is empty."
---

# PlaceholderMessage QML Type

A placeholder message indicating that a list view is empty. [More...](#details)

- Import Statement: import org.kde.plasma.extras
- Inherits: [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html)

## Detailed Description {#details}

The message comprises a label with lightened text, an optional icon above the text, and an optional button below the text which can be used to easily show the user what to do next to add content to the view.

The top-level component is a [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html), so additional components items can simply be added as child items and they will be positioned sanely.

Example usage:

```qml
// Shows how to use PlaceholderMessage to implement a "this view is empty" message
import QtQuick
import org.kde.plasma.extras as PlasmaExtras

ListView {
    id: listView
    model: [...]
    delegate: [...]

    PlasmaExtras.PlaceholderMessage {
        anchors.centerIn: parent
        width: parent.width - (Kirigami.Units.gridUnit * 4)

        visible: listView.count == 0

        text: "There are no items in this list"
    }
}
\endcode

\qml
// Shows how to use PlaceholderMessage to implement a "here's how to proceed" message
import QtQuick
import QtQuick.Controls as QQC2
import org.kde.plasma.extras as PlasmaExtras

ListView {
    id: listView
    model: [...]
    delegate: [...]

    PlasmaExtras.PlaceholderMessage {
        anchors.centerIn: parent
        width: parent.width - (Kirigami.Units.gridUnit * 4)

        visible: listView.count == 0

        text: "Add an item to proceed"

        helpfulAction: QQC2.Action {
            icon.name: "list-add"
            text: "Add item..."
            onTriggered: {
                [...]
            }
        }
    }
    [...]
}
```

```qml
// Shows how to use PlaceholderMessage to implement a "there was a problem here" message
import org.kde.plasma.components as PlasmaComponents3
import org.kde.plasma.extras as PlasmaExtras

PlasmaComponents3.Page {
    id: root
    readonly property bool networkConnected: [...]

    PlasmaExtras.PlaceholderMessage {
        anchors.centerIn: parent
        width: parent.width - (Kirigami.Units.gridUnit * 4)

        visible: root.networkConnected

        iconName: "network-disconnect"
        text: "Unable to load content
        explanation: "Please try again later"
    }
}
```

```qml
import org.kde.plasma.components as PlasmaComponents3
import org.kde.plasma.extras as PlasmaExtras

// Shows how to use PlaceholderMessage to implement a loading indicator
PlasmaComponents3.Page {
    id: root
    readonly property bool loading: [...]
    readonly property int completionStatus: [...]

    PlasmaExtras.PlaceholderMessage {
        anchors.centerIn: parent
        width: parent.width - (Kirigami.Units.gridUnit * 4)

        visible: root.loading

        iconName: "my-awesome-app-icon"
        text: "Loading this awesome app"

        PlasmaComponents3.ProgressBar {
            Layout.preferredWidth: Kirigami.Units.gridUnit * 20
            value: root.completionStatus
            from: 0
            to: 100
        }
    }
}
```

```qml
import QtQuick.Controls as QQC2
import org.kde.plasma.components as PlasmaComponents3
import org.kde.plasma.extras as PlasmaExtras

// Shows how to use PlaceholderMessage to implement a "Here's what you do next" button
PlasmaComponents3.Page {
    id: root

    PlasmaExtras.PlaceholderMessage {
        anchors.centerIn: parent
        width: parent.width - (Kirigami.Units.largeSpacing * 4)

        visible: root.loading

        helpfulAction: QQC2.Action {
            icon.name: "list-add"
            text: "Add item..."
            onTriggered: {
                [...]
            }
        }
    }
}
```

## Property Documentation {#property-documentation}

### explanation : string {#explanation-prop}

Smaller explanatory text to show below the larger title-style text

Useful for providing a user-friendly explanation for how to proceed.

Optional; if not defined, the message will have no supplementary explanatory text.

### helpfulAction : T.Action {#helpfulAction-prop}

An action that helps the user proceed. Typically used to guide the user to the next step for adding content or items to an empty view.

Optional

### \[read-only, since 6.8\] hoveredLink : string {#hoveredLink-prop}

This property holds the link embedded in the explanatory message text that the user is hovering over.

This property was introduced in Qt 6.8.

### iconName : string {#iconName-prop}

The icon to show above the text label.

Optional Falls back to `undefined` if the specified icon is not valid or cannot be loaded.

### text : string {#text-prop}

The text to show as a placeholder label

Optional; if not defined, the message will have no large text label text. If both text: and explanation: are omitted, the message will have no text and only an icon, action button, and/or other custom content.

### type : int {#type-prop}

The type of the message. This can be:

- [PlasmaExtras](plasmaextras-module.md).[PlaceholderMessage](qml-org-kde-plasma-extras-placeholdermessage.md).Type.Actionable: Makes it more attention-getting. Useful when the user is expected to interact with the message.
- [PlasmaExtras](plasmaextras-module.md).[PlaceholderMessage](qml-org-kde-plasma-extras-placeholdermessage.md).Type.Informational: Makes it less prominent. Useful when the message in only informational.
   
   By default if an [helpfulAction](qml-org-kde-plasma-extras-placeholdermessage.md#helpfulAction-prop) is provided this will be of type Actionable otherwise of type Informational.

#### Signal Documentation {#signal-documentation}

##### \[since 6.8\] linkActivated(string *link*) {#linkActivated-signal}

This signal is emitted when a link is clicked or tapped in the explanatory message text.

`link` The clicked or tapped link.

> **Note:** The corresponding handler is `onLinkActivated`.

This signal was introduced in Qt 6.8.

##### \[since 6.8\] linkHovered(string *link*) {#linkHovered-signal}

This signal is emitted when a link is hovered in the explanatory message text.

`link` The hovered link.

> **Note:** The corresponding handler is `onLinkHovered`.

This signal was introduced in Qt 6.8.
