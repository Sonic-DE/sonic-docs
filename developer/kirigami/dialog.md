---
title: Adding a dialog
description: Getting to grips with Kirigami dialogs.
source_url: https://develop.kde.org/docs/getting-started/kirigami/introduction-dialogs/
source_authors: [Antti Savolainen, Michael Rostom, Nicolas Fella, Oliver Omega, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-quick-ui (dialogs/Dialog.qml, FormLayout), Qt 6.11 (ListModel stores the Date; checked with the qml tool); the example was built into the tutorial application and loaded offscreen without QML errors
---

# Adding a dialog

## Making our application useful

We have a window, cards and actions, but still no way to enter a name, description and date of our choice.

We could create a new page with the input fields, but a whole page just for a name, description and date seems excessive. Instead, we use a dialog.

## Opening the dialog

```qml
pageStack.initialPage: Kirigami.ScrollablePage {
    // ...
    actions: [
        Kirigami.Action {
            id: addAction
            icon.name: "list-add"
            text: i18nc("@action:button", "Add kountdown")
            onTriggered: addDialog.open()
        }
    ]
}
```

First we change the action from the previous step: it is now just a [Kirigami.Action](/docs/api/kirigami/qml-org-kde-kirigami-action) that calls the dialog's [open()](https://doc.qt.io/qt-6/qml-qtquick-controls-popup.html#open-method) function.

## A dialog for adding countdowns

The new component is a [Kirigami.Dialog](/docs/api/kirigami/qml-org-kde-kirigami-dialogs-dialog). Dialogs appear in the middle of the window and are used for short tasks and extra information about the current content. They can't be moved, and they adapt their size to the window.

```qml
Kirigami.ApplicationWindow {
    // ...
    Kirigami.Dialog {
        id: addDialog
        title: i18nc("@title:window", "Add kountdown")
        standardButtons: Kirigami.Dialog.Ok | Kirigami.Dialog.Cancel
        padding: Kirigami.Units.largeSpacing
        preferredWidth: Kirigami.Units.gridUnit * 20

        // Form layouts help align and structure a layout with several inputs
        Kirigami.FormLayout {
            // Textfields let you input text in a thin textbox
            Controls.TextField {
                id: nameField
                // Provides a label attached to the textfield
                Kirigami.FormData.label: i18nc("@label:textbox", "Name*:")
                // What to do after input is accepted (i.e. pressed Enter)
                // In this case, it moves the focus to the next field
                onAccepted: descriptionField.forceActiveFocus()
            }
            Controls.TextField {
                id: descriptionField
                Kirigami.FormData.label: i18nc("@label:textbox", "Description:")
                placeholderText: i18n("Optional")
                // Again, it moves the focus to the next field
                onAccepted: dateField.forceActiveFocus()
            }
            Controls.TextField {
                id: dateField
                Kirigami.FormData.label: i18nc("@label:textbox", "ISO Date*:")
                // D means a required number between 1-9,
                // 9 means a required number between 0-9
                inputMask: "D999-99-99"
                // Here we confirm the operation just like
                // clicking the OK button
                onAccepted: addDialog.accepted()
            }
            Controls.Label {
                text: "* = required fields"
            }
        }
        // The dialog logic goes here
    }
    // ...
}
```

A dialog has a [header](https://doc.qt.io/qt-6/qml-qtquick-controls-dialog.html#header-prop) and a [footer](https://doc.qt.io/qt-6/qml-qtquick-controls-dialog.html#footer-prop), inherited from Qt Quick Controls' Dialog.

By default the header shows the [title](https://doc.qt.io/qt-6/qml-qtquick-controls-dialog.html#title-prop) and a close button, which you can hide with [showCloseButton](/docs/api/kirigami/qml-org-kde-kirigami-dialogs-dialog#showCloseButton-prop). The footer shows the buttons set with [standardButtons](https://doc.qt.io/qt-6/qml-qtquick-controls-dialog.html#standardButtons-prop) (and `customFooterActions`); by default there are none.

We give our dialog an "OK" and a "Cancel" button, some padding, and a reasonable [preferredWidth](/docs/api/kirigami/qml-org-kde-kirigami-dialogs-dialog#preferredWidth-prop): the size the dialog expects to have, which can grow if needed. We use the [Kirigami.Units](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-units) we met before.

Then comes a [Kirigami.FormLayout](/docs/api/kirigami/qml-org-kde-kirigami-layouts-formlayout). Unlike a [ColumnLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-columnlayout.html), it arranges its children automatically and centered, with optional labels. As the name says, it is made for input forms.

Form layouts work with many kinds of input, but we stick to simple [Controls.TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html)s, plain text boxes.

The text fields are inputs for:

1. the countdown's name;
2. its description;
3. the date we count down to, in the form `YYYY-MM-DD`.

On each [Controls.TextField](https://doc.qt.io/qt-6/qml-qtquick-controls-textfield.html) we set [Kirigami.FormData.label](/docs/api/kirigami/qml-org-kde-kirigami-layouts-formdata#label-attached-prop), the field's label. The form shows the labels to the left of the fields.

We also use [onAccepted](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#accepted-signal) to call [forceActiveFocus()](https://doc.qt.io/qt-6/qml-qtquick-item.html#forceActiveFocus-method) on the next field, so pressing Enter moves to the next field, which makes the form easier to use.

The date field has an [inputMask](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#inputMask-prop). `D999-99-99` keeps users from entering anything that might break the application (such as text): only digits are allowed, which we can then try to turn into a date.

With the dialog's user interface done, we define its behavior. We need three things:

1. enable the OK button only when the required fields are filled in;
2. add the input to the model;
3. clear the form.

```qml
Kirigami.Dialog {
    // ...
    // Once the Kirigami.Dialog is initialized,
    // we want to create a custom binding to only
    // make the Ok button visible if the required
    // text fields are filled.
    // For this we use Kirigami.Dialog.standardButton(button):
    Component.onCompleted: {
        const button = standardButton(Kirigami.Dialog.Ok);
        // () => is a JavaScript arrow function
        button.enabled = Qt.binding( () => requiredFieldsFilled() );
    }
    onAccepted: {
        // The binding is created, but we still need to make it
        // unclickable unless the fields are filled
        if (!addDialog.requiredFieldsFilled()) return;
        appendDataToModel();
        clearFieldsAndClose();
    }
}
```

First we bind the OK button's `enabled` property to a check of whether the fields are filled in. In JavaScript this needs [Qt.binding()](https://doc.qt.io/qt-6/qtqml-syntax-propertybinding.html#creating-property-bindings-from-javascript). In effect, the line

```qml
button.enabled = Qt.binding( () => requiredFieldsFilled() );
```

works like the QML bindings we have seen so far, as in this pseudo-code:

```qml
enabled: requiredFieldsFilled()
```

[onAccepted](https://doc.qt.io/qt-6/qml-qtquick-controls-dialog.html#accepted-signal) handles the OK button. If the required fields aren't filled in, it returns without doing anything; otherwise it adds the input to the model and clears the dialog for the next time it is opened.

```qml
Kirigami.Dialog {
    // ...
    // We check that the nameField is not empty and that the
    // dateField (which has an inputMask) is completely filled
    function requiredFieldsFilled() {
        return (nameField.text !== "" && dateField.acceptableInput);
    }
    function appendDataToModel() {
        kountdownModel.append({
            name: nameField.text,
            description: descriptionField.text,
            date: new Date(dateField.text)
        });
    }
    function clearFieldsAndClose() {
        nameField.text = ""
        descriptionField.text = ""
        dateField.text = ""
        addDialog.close();
    }
}
```

For the required name field, we just check that its text isn't empty. The date field has an input mask, so we check [acceptableInput](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#acceptableInput-prop) instead, which is only true once the whole field is filled with acceptable characters.

Then the [append()](https://doc.qt.io/qt-6/qml-qtqml-models-listmodel.html#append-method) method of `kountdownModel` adds a JavaScript object with these properties; the date is stored as a JavaScript `Date`.

Finally we clear the text fields by setting their [text](https://doc.qt.io/qt-6/qml-qtquick-textinput.html#text-prop) to an empty string, and [close()](https://doc.qt.io/qt-6/qml-qtquick-controls-popup.html#close-method) the dialog.

Save the files and build the program, and you can add your own countdowns! A few finishing touches improve the interface. First, remove the placeholder countdown from the previous steps; the model now starts empty:

```qml
    ListModel {
        id: kountdownModel
    }
```

Second, now that we have a real date, show how many days are left until it:

```qml
                    Kirigami.Heading {
                        level: 1
                        text: i18n("%1 days", Math.round((date-Date.now())/86400000))
                    }
```

Third, make the window bigger, so there is more room for the new cards:

```qml
    width: 600
    height: 400
```

Much nicer.

## Our application so far

`Main.qml`:

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    id: root

    width: 600
    height: 400

    title: i18nc("@title:window", "Day Kountdown")

    globalDrawer: Kirigami.GlobalDrawer {
        isMenu: true
        actions: [
            Kirigami.Action {
                text: i18n("Quit")
                icon.name: "application-exit-symbolic"
                shortcut: StandardKey.Quit
                onTriggered: Qt.quit()
            }
        ]
    }

    ListModel {
        id: kountdownModel
    }

    Component {
        id: kountdownDelegate
        Kirigami.AbstractCard {
            contentItem: Item {
                implicitWidth: delegateLayout.implicitWidth
                implicitHeight: delegateLayout.implicitHeight
                GridLayout {
                    id: delegateLayout
                    anchors {
                        left: parent.left
                        top: parent.top
                        right: parent.right
                    }
                    rowSpacing: Kirigami.Units.largeSpacing
                    columnSpacing: Kirigami.Units.largeSpacing
                    columns: root.wideScreen ? 4 : 2

                    Kirigami.Heading {
                        level: 1
                        text: i18n("%1 days", Math.round((date-Date.now())/86400000))
                    }

                    ColumnLayout {
                        Kirigami.Heading {
                            Layout.fillWidth: true
                            level: 2
                            text: name
                        }
                        Kirigami.Separator {
                            Layout.fillWidth: true
                            visible: description.length > 0
                        }
                        Controls.Label {
                            Layout.fillWidth: true
                            wrapMode: Text.WordWrap
                            text: description
                            visible: description.length > 0
                        }
                    }
                    Controls.Button {
                        Layout.alignment: Qt.AlignRight
                        Layout.columnSpan: 2
                        text: i18n("Edit")
                    }
                }
            }
        }
    }

    Kirigami.Dialog {
        id: addDialog
        title: i18nc("@title:window", "Add kountdown")
        standardButtons: Kirigami.Dialog.Ok | Kirigami.Dialog.Cancel
        padding: Kirigami.Units.largeSpacing
        preferredWidth: Kirigami.Units.gridUnit * 20

        // Form layouts help align and structure a layout with several inputs
        Kirigami.FormLayout {
            // Textfields let you input text in a thin textbox
            Controls.TextField {
                id: nameField
                // Provides a label attached to the textfield
                Kirigami.FormData.label: i18nc("@label:textbox", "Name*:")
                // What to do after input is accepted (i.e. pressed Enter)
                // In this case, it moves the focus to the next field
                onAccepted: descriptionField.forceActiveFocus()
            }
            Controls.TextField {
                id: descriptionField
                Kirigami.FormData.label: i18nc("@label:textbox", "Description:")
                placeholderText: i18n("Optional")
                // Again, it moves the focus to the next field
                onAccepted: dateField.forceActiveFocus()
            }
            Controls.TextField {
                id: dateField
                Kirigami.FormData.label: i18nc("@label:textbox", "ISO Date*:")
                // D means a required number between 1-9,
                // 9 means a required number between 0-9
                inputMask: "D999-99-99"
                // Here we confirm the operation just like
                // clicking the OK button
                onAccepted: addDialog.accepted()
            }
            Controls.Label {
                text: "* = required fields"
            }
        }
        // Once the Kirigami.Dialog is initialized,
        // we want to create a custom binding to only
        // make the Ok button visible if the required
        // text fields are filled.
        // For this we use Kirigami.Dialog.standardButton(button):
        Component.onCompleted: {
            const button = standardButton(Kirigami.Dialog.Ok);
            // () => is a JavaScript arrow function
            button.enabled = Qt.binding( () => requiredFieldsFilled() );
        }
        onAccepted: {
            // The binding is created, but we still need to make it
            // unclickable unless the fields are filled
            if (!addDialog.requiredFieldsFilled()) return;
            appendDataToModel();
            clearFieldsAndClose();
        }
        // We check that the nameField is not empty and that the
        // dateField (which has an inputMask) is completely filled
        function requiredFieldsFilled() {
            return (nameField.text !== "" && dateField.acceptableInput);
        }
        function appendDataToModel() {
            kountdownModel.append({
                name: nameField.text,
                description: descriptionField.text,
                date: new Date(dateField.text)
            });
        }
        function clearFieldsAndClose() {
            nameField.text = ""
            descriptionField.text = ""
            dateField.text = ""
            addDialog.close();
        }
    }

    pageStack.initialPage: Kirigami.ScrollablePage {
        title: i18nc("@title", "Kountdown")

        // Kirigami.Action encapsulates a UI action. Inherits from Controls.Action
        actions: [
            Kirigami.Action {
                id: addAction
                // Name of icon associated with the action
                icon.name: "list-add-symbolic"
                // Action text, i18n function returns translated string
                text: i18nc("@action:button", "Add kountdown")
                // What to do when triggering the action
                onTriggered: addDialog.open()
            }
        ]

        Kirigami.CardsListView {
            id: cardsView
            model: kountdownModel
            delegate: kountdownDelegate
        }
    }
}
```
