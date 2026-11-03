---
title: "MenuDialog QML Type"
description: "A dialog that prompts users with a context menu, with list items that perform actions."
---

# MenuDialog QML Type

A dialog that prompts users with a context menu, with list items that perform actions. [More...](#details)

- Import Statement: import org.kde.kirigami.dialogs
- Inherits: [Dialog](qml-org-kde-kirigami-dialogs-dialog.md)

## Detailed Description {#details}

Example usage:

```qml
Kirigami.MenuDialog {
    title: i18n("Track Options")

    actions: [
        Kirigami.Action {
            icon.name: "media-playback-start"
            text: i18nc("Start playback of the selected track", "Play")
            tooltip: i18n("Start playback of the selected track")
        },
        Kirigami.Action {
            enabled: false
            icon.name: "document-open-folder"
            text: i18nc("Show the file for this song in the file manager", "Show in folder")
            tooltip: i18n("Show the file for this song in the file manager")
        },
        Kirigami.Action {
            icon.name: "documentinfo"
            text: i18nc("Show track metadata", "View details")
            tooltip: i18n("Show track metadata")
        },
        Kirigami.Action {
            icon.name: "list-add"
            text: i18nc("Add the track to the queue, right after the current track", "Play next")
            tooltip: i18n("Add the track to the queue, right after the current track")
        },
        Kirigami.Action {
            icon.name: "list-add"
            text: i18nc("Enqueue current track", "Add to queue")
            tooltip: i18n("Enqueue current track")
        }
    ]
}
```

*See also* [Dialog](qml-org-kde-kirigami-dialogs-dialog.md), [PromptDialog](qml-org-kde-kirigami-dialogs-promptdialog.md)

## Property Documentation {#property-documentation}

### actions : list\<Action\> {#actions-prop}

This property holds the actions displayed in the context menu.

### contentHeader : Item {#contentHeader-prop}

This property holds the content header, which appears above the actions. but below the header bar.

### contentHeaderControl : Control {#contentHeaderControl-prop}

This property holds the content header.

This makes it possible to access its internal properties to, for example, change its padding: contentHeaderControl.topPadding
