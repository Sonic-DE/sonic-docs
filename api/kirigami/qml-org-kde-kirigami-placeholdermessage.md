---
title: "PlaceholderMessage QML Type"
description: "A placeholder message indicating that a view is empty."
---

# PlaceholderMessage QML Type

A placeholder message indicating that a view is empty. [More...](#details)

- Import Statement: import org.kde.kirigami
- Inherits: [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html)
- Inherited By: [LoadingPlaceholder](qml-org-kde-kirigami-loadingplaceholder.md)

## Detailed Description {#details}

The message comprises a label with text, an optional explanation below the main text, an optional icon above all the text, and an optional button below all the text which can be used to easily show the user what to do next to add content to the view.

The explanatory text is selectable and can contain clickable links. In this latter case, client code must implement an `onLinkactivated`: signal handler or the links will not work.

The top-level component is a [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html), so additional components items can simply be added as child items and they will be positioned sanely.

Example usage:

Used as a "this view is empty" message:

```qml
import org.kde.kirigami as Kirigami

ListView {
    id: listView
    model: [...]
    delegate: [...]

    Kirigami.PlaceholderMessage {
        anchors.centerIn: parent
        width: parent.width - (Kirigami.Units.largeSpacing * 4)

        visible: listView.count === 0

        text: "There are no items in this list"
    }
}
```

Used as a "here's how to proceed" message:

```qml
import org.kde.kirigami as Kirigami

ListView {
    id: listView
    model: [...]
    delegate: [...]

    Kirigami.PlaceholderMessage {
        anchors.centerIn: parent
        width: parent.width - (Kirigami.Units.largeSpacing * 4)

        visible: listView.count === 0

        text: "Add an item to proceed"

        helpfulAction: Kirigami.Action {
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

Used as a "there was a problem here" message:

```qml
import org.kde.kirigami as Kirigami

Kirigami.Page {
    id: root
    readonly property bool networkConnected: [...]

    Kirigami.PlaceholderMessage {
        anchors.centerIn: parent
        width: parent.width - (Kirigami.Units.largeSpacing * 4)

        visible: root.networkConnected

        icon.name: "network-disconnect"
        text: "Unable to load content"
        explanation: "Please try again later." +
                     " Visit <a href='https://foo.com/com'>this link</a> for more details."
        onLinkActivated: link => Qt.openUrlExternally(link)
    }
}
```

Used as a "Here's what you do next" button:

```qml
import org.kde.kirigami as Kirigami

Kirigami.Page {
    id: root

    Kirigami.PlaceholderMessage {
        anchors.centerIn: parent
        width: parent.width - (Kirigami.Units.largeSpacing * 4)

        visible: root.loading

        helpfulAction: Kirigami.Action {
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

This property holds the smaller explanatory text to show below the larger title-style text

Useful for providing a user-friendly explanation on how to proceed.

Optional; if not defined, the message will have no supplementary explanatory text.

### helpfulAction : QtQuick.Controls.Action {#helpfulAction-prop}

This property holds an action that helps the user proceed.

Typically used to guide the user to the next step for adding content or items to an empty view.

Optional; if undefined, no button will appear below the text label.

### \[read-only\] hoveredLink : string {#hoveredLink-prop}

This property holds the link embedded in the explanatory message text that the user is hovering over.

### icon group {#icon-prop}

### icon.color : color {#icon.color-prop}

### icon.height : int {#icon.height-prop}

### icon.name : string {#icon.name-prop}

### icon.source : string {#icon.source-prop}

### icon.width : int {#icon.width-prop}

This property provides an icon to display above the top text label.

> **Note:** It accepts icon.name and icon.source to set the icon source. It is suggested to use icon.name.

Optional; if undefined, the message will have no icon. Falls back to `undefined` if the specified icon is not valid or cannot be loaded.

### text : string {#text-prop}

This property holds the text to show in the placeholder label.

Optional; if not defined, the message will have no large text label text. If both text and explanation are omitted, the message will have no text and only an icon, action button, and/or other custom content.

### type : enumeration {#type-prop}

This property holds the [PlaceholderMessage](qml-org-kde-kirigami-placeholdermessage.md) type.

The type of the message. This can be:

- Kirigami.[PlaceholderMessage](qml-org-kde-kirigami-placeholdermessage.md).Type.Actionable: Makes it more attention-getting. Useful when the user is expected to interact with the message.
- Kirigami.[PlaceholderMessage](qml-org-kde-kirigami-placeholdermessage.md).Type.Informational: Makes it less prominent. Useful when the message in only informational.

default: if a [helpfulAction](qml-org-kde-kirigami-placeholdermessage.md#helpfulAction-prop) is provided this will be of type Actionable otherwise of type Informational.

## Signal Documentation {#signal-documentation}

### linkActivated(string *link*) {#linkActivated-signal}

This signal is emitted when a link is clicked or tapped in the explanatory message text.

`link` The clicked or tapped link.

> **Note:** The corresponding handler is `onLinkActivated`.

### linkHovered(string *link*) {#linkHovered-signal}

This signal is emitted when a link is hovered in the explanatory message text.

`link` The hovered link.

> **Note:** The corresponding handler is `onLinkHovered`.
