---
title: Inline messages
description: Display messages related to the content of your application.
source_url: https://develop.kde.org/docs/getting-started/kirigami/components-inlinemessages/
source_authors: [Carl Schwan, Claudio Cambra, Frederik Schwarzer, Jeongu Kim, Mikhail Zolotukhin, Nicolas Fella, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "Kirigami InlineMessage (template and control), SilverLight.colors, Silver icon theme; examples run with the qml tool"
---

# Inline messages

Inline messages are an immediate way to tell your users about something that happened while they use the application.

## Basic inline message

[Kirigami.InlineMessage](/docs/api/kirigami/qml-org-kde-kirigami-inlinemessage) components have two important properties:

- [visible](https://doc.qt.io/qt-6/qml-qtquick-item.html#visible-prop): `false` by default, so that the message only appears when you explicitly want it to. You can override this by setting it to `true`. When a hidden inline message is made visible, it appears with an animation.
- [text](/docs/api/kirigami/qml-org-kde-kirigami-inlinemessage#text-prop): the text of your inline message.

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.Page {

    ColumnLayout {
        Kirigami.InlineMessage {
            id: inlineMessage
            Layout.fillWidth: true
            text: "Hello! I am a siiiiiiimple lil' inline message!"
        }

        Controls.Button {
            text: "Show inline message!"
            onClicked: inlineMessage.visible = !inlineMessage.visible
        }
    }
}
```

## Different types

Standard inline messages are like the ones above: with SonicDE's Silver color schemes they have a blue background and a default icon. You can change this with the [type](/docs/api/kirigami/qml-org-kde-kirigami-inlinemessage#type-prop) property, which sets the message to a different type. There are four types to choose from:

- **Information** (`Kirigami.MessageType.Information`): the default. Has a blue background and an "i" icon, and is used to announce a result or tell the user something general. You don't need to set it explicitly.
- **Positive** (`Kirigami.MessageType.Positive`): has a green background and a tick icon, and indicates that something went well.
- **Warning** (`Kirigami.MessageType.Warning`): has an orange background and an exclamation-mark icon, and warns the user about something they should keep in mind.
- **Error** (`Kirigami.MessageType.Error`): has a red background and a cross icon, and tells the user that something has gone wrong.

```qml
ColumnLayout {

    Kirigami.InlineMessage {
        Layout.fillWidth: true
        text: "Hello! Let me tell you something interesting!"
        visible: true
    }

    Kirigami.InlineMessage {
        Layout.fillWidth: true
        text: "Hey! Let me tell you something positive!"
        type: Kirigami.MessageType.Positive
        visible: true
    }

    Kirigami.InlineMessage {
        Layout.fillWidth: true
        text: "Hmm... You should keep this in mind!"
        type: Kirigami.MessageType.Warning
        visible: true
    }
   
    Kirigami.InlineMessage {
        Layout.fillWidth: true
        text: "Argh!!! Something went wrong!!"
        type: Kirigami.MessageType.Error
        visible: true
    }

}
```

## Customizing text and icons

Inline messages support rich text, defined with simple HTML-like markup. This lets you format the text of your inline message, or even include a web link.

```qml
Kirigami.InlineMessage {
    Layout.fillWidth: true
    // Note that when you use quotes in a string you will have to escape them!
    text: "Check out <a href=\"https://sonicde.org\">SonicDE's website!</a>"
    onLinkActivated: Qt.openUrlExternally(link)
    visible: true
}
```

You can also change the icon in the top left of your message by giving a system icon name to the [icon.source](/docs/api/kirigami/qml-org-kde-kirigami-inlinemessage#icon.source-prop) property. The names must match icons installed on your system; to browse and search the available icons and see their names, use Icon Explorer (`iconexplorer`) from [sonic-theme-sdk](https://github.com/Sonic-DE/sonic-theme-sdk).

```qml
Kirigami.InlineMessage {
    Layout.fillWidth: true
    text: "Look at me! I look SPECIAL!"
    icon.source: "actor"
    visible: true
}
```

## Using actions in inline messages

If your messages need to be interactive, you can attach Kirigami actions to them. As with pages, set the [InlineMessage.actions](/docs/api/kirigami/qml-org-kde-kirigami-inlinemessage#actions-prop) property to a [Kirigami.Action](/docs/api/kirigami/qml-org-kde-kirigami-action) or an array of [Kirigami.Action](/docs/api/kirigami/qml-org-kde-kirigami-action) components.

```qml
ColumnLayout {

    Kirigami.InlineMessage {
        id: actionsMessage
        Layout.fillWidth: true
        visible: true

        readonly property string initialText: "Something is hiding around here..."
        text: initialText

        actions: [
            Kirigami.Action {
                enabled: actionsMessage.text == actionsMessage.initialText
                text: qsTr("Add text")
                icon.name: "list-add"
                onTriggered: {
                    actionsMessage.text = actionsMessage.initialText + " Peekaboo!";
                }
            },
            Kirigami.Action {
                enabled: actionsMessage.text != actionsMessage.initialText
                text: qsTr("Reset text")
                icon.name: "list-remove"
                onTriggered: actionsMessage.text = actionsMessage.initialText
            }
        ]
    }
}
```

## Close buttons

Inline messages have a close button for dismissing them easily. It is hidden by default; show it by setting the [showCloseButton](/docs/api/kirigami/qml-org-kde-kirigami-inlinemessage#showCloseButton-prop) property to `true`.

```qml
Kirigami.InlineMessage {
    Layout.fillWidth: true
    text: "Please don't dismiss me..."
    showCloseButton: true
    visible: true
}
```
