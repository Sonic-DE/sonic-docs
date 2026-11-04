---
title: Dialog types
description: Various ways to show and input data.
source_url: https://develop.kde.org/docs/getting-started/kirigami/components-dialogs/
source_authors: [Nicolas Fella, Roshani Kumari, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "Kirigami dialogs module (Dialog.qml, PromptDialog.qml, MenuDialog.qml), Action.qml; each example run with the qml tool and its dialog opened, plus a PromptDialog subtitle-and-child check"
---

# Dialog types

A [Kirigami.Dialog](/docs/api/kirigami/qml-org-kde-kirigami-dialogs-dialog) is a simple component you can use to supplement the content shown on an application's page. It can display non-interactive content (only text) and interactive content (forms, list views and buttons).

Dialogs can be dismissed by clicking or tapping outside their area, by pressing Escape, or by clicking the close button in the header.

### Dialog

A standard [Kirigami.Dialog](/docs/api/kirigami/qml-org-kde-kirigami-dialogs-dialog) is used to create custom dialogs. They are very easy to extend:

```qml
import QtQuick
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Dialog"
    width: 400
    height: 400
    pageStack.initialPage: Kirigami.Page {
        id: page
        actions: Kirigami.Action {
            icon.name: "list-add"
            text: "Show dialog"
            onTriggered: dialog.open()
        }

        Kirigami.Dialog {
            id: dialog
            title: "A simple dialog"
            padding: Kirigami.Units.largeSpacing
            showCloseButton: false
            standardButtons: Kirigami.Dialog.NoButton
            flatFooterButtons: false
            Controls.Label {
                text: "A generic, easy to make dialog!"
            }
            customFooterActions: Kirigami.Action {
                text: "Copy"
                icon.name: "clipboard"
            }
        }
    }
}
```

As shown in the [introduction to dialogs](dialog.md), you can also get a button with `standardButton(button)` and give it some behavior, such as a binding that enables it only under certain conditions.

This type of dialog is generic and fits most use cases, and it works well with complex interactive content (especially views):

```qml
import QtQuick
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "Scrollable Dialog"
    width: 600
    height: 600
    pageStack.initialPage: Kirigami.Page {
        id: page
        actions: Kirigami.Action {
            icon.name: "list-add"
            text: scrollableDialog.title
            onTriggered: scrollableDialog.open()
        }

        Kirigami.Dialog {
            id: scrollableDialog
            title: i18n("Select Number")

            ListView {
                id: listView
                // hints for the dialog dimensions
                implicitWidth: Kirigami.Units.gridUnit * 16
                implicitHeight: Kirigami.Units.gridUnit * 16

                model: 20
                delegate: Controls.RadioDelegate {
                    topPadding: Kirigami.Units.smallSpacing * 2
                    bottomPadding: Kirigami.Units.smallSpacing * 2
                    implicitWidth: listView.width
                    text: modelData
                }
            }
        }

    }
}
```

In most cases, though, you will likely want one of its derived dialog types, [Kirigami.PromptDialog](/docs/api/kirigami/qml-org-kde-kirigami-dialogs-promptdialog) or [Kirigami.MenuDialog](/docs/api/kirigami/qml-org-kde-kirigami-dialogs-menudialog).

### PromptDialog

A [Kirigami.PromptDialog](/docs/api/kirigami/qml-org-kde-kirigami-dialogs-promptdialog) is essentially a dialog with a built-in label and a default [contentPadding](/docs/api/kirigami/qml-org-kde-kirigami-dialogs-promptdialog#contentPadding-prop), used to prompt the user for some information. Use it only for simple yes/no prompts or brief requests for user input.

Its main property is [subtitle](/docs/api/kirigami/qml-org-kde-kirigami-dialogs-promptdialog#subtitle-prop), which holds the text. QML components added as children of the prompt dialog are shown below the subtitle; leave the subtitle empty if a child should take its place.

```qml
import QtQuick
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "PromptDialog"
    width: 400
    height: 400
    pageStack.initialPage: Kirigami.Page {
        id: page
        actions: Kirigami.Action {
            icon.name: "list-add"
            text: promptDialog.title
            onTriggered: promptDialog.open()
        }

        Kirigami.PromptDialog {
            id: promptDialog
            title: i18n("Delete file")
            subtitle: i18n("Are you sure you'd like to delete this file?")

            standardButtons: Kirigami.Dialog.Ok | Kirigami.Dialog.Cancel
            onAccepted: console.info("File deleted")
        }
    }
}
```

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "PromptDialog with a textfield"
    width: 600
    height: 600
    pageStack.initialPage: Kirigami.Page {
        id: page
        actions: Kirigami.Action {
            icon.name: "list-add"
            text: textPromptDialog.title
            onTriggered: textPromptDialog.open()
        }

        Kirigami.PromptDialog {
            id: textPromptDialog
            title: "New Folder"

            standardButtons: Kirigami.Dialog.NoButton
            customFooterActions: [
                Kirigami.Action {
                    text: "Create Folder"
                    icon.name: "dialog-ok"
                    onTriggered: {
                        showPassiveNotification("Created");
                        textPromptDialog.close();
                    }
                },
                Kirigami.Action {
                    text: "Cancel"
                    icon.name: "dialog-cancel"
                    onTriggered: {
                        textPromptDialog.close();
                    }
                }
            ]
            ColumnLayout {
                Controls.TextField {
                    Layout.fillWidth: true
                    placeholderText: "Folder name…"
                }
            }
        }
    }
}
```

### MenuDialog

A [Kirigami.MenuDialog](/docs/api/kirigami/qml-org-kde-kirigami-dialogs-menudialog) is a specialized dialog that lists a selection of clickable options for the user, set with its [actions](/docs/api/kirigami/qml-org-kde-kirigami-dialogs-menudialog#actions-prop) property.

```qml
import QtQuick
import QtQuick.Controls as Controls
import org.kde.kirigami as Kirigami

Kirigami.ApplicationWindow {
    title: "MenuDialog"
    width: 400
    height: 600
    pageStack.initialPage: Kirigami.Page {
        id: page
        actions: Kirigami.Action {
            icon.name: "list-add"
            text: menuDialog.title
            onTriggered: menuDialog.open()
        }

        Kirigami.MenuDialog {
            id: menuDialog
            title: i18n("Track options")
            showCloseButton: false

            actions: [
                Kirigami.Action {
                    icon.name: "media-playback-start"
                    text: i18n("Play")
                    tooltip: i18n("Start playback of the selected track")
                },
                Kirigami.Action {
                    enabled: false
                    icon.name: "document-open-folder"
                    text: i18n("Show in folder")
                    tooltip: i18n("Show the file for this song in the file manager")
                },
                Kirigami.Action {
                    icon.name: "documentinfo"
                    text: i18n("View details")
                    tooltip: i18n("Show track metadata")
                },
                Kirigami.Action {
                    icon.name: "list-add"
                    text: i18n("Play next")
                    tooltip: i18n("Add the track to the queue, right after the current track")
                },
                Kirigami.Action {
                    icon.name: "list-add"
                    text: i18n("Add to queue")
                    tooltip: i18n("Enqueue current track")
                }
            ]
        }
    }
}
```
