---
title: "PromptDialog QML Type"
description: "A simple dialog to quickly prompt a user with information, and possibly perform an action."
---

# PromptDialog QML Type

A simple dialog to quickly prompt a user with information, and possibly perform an action. [More...](#details)

- Import Statement: import org.kde.kirigami.dialogs
- Inherits: [Dialog](qml-org-kde-kirigami-dialogs-dialog.md)

## Detailed Description {#details}

Provides content padding (instead of padding outside of the scroll area). Also has a default preferredWidth, as well as the subtitle property.

> **Note:** If a mainItem is specified, it will replace the subtitle label, and so the respective property will have no effect.

Example usage:

```qml
Kirigami.PromptDialog {
    title: "Reset settings?"
    subtitle: "The stored settings for the application will be deleted, with the defaults restored."
    standardButtons: Kirigami.Dialog.Ok | Kirigami.Dialog.Cancel

    onAccepted: console.log("Accepted")
    onRejected: console.log("Rejected")
}
```

Text field prompt dialog:

```qml
Kirigami.PromptDialog {
    id: textPromptDialog
    title: qsTr("New Folder")

    standardButtons: Kirigami.Dialog.NoButton
    customFooterActions: [
        Kirigami.Action {
            text: qsTr("Create Folder")
            icon.name: "dialog-ok"
            onTriggered: {
                showPassiveNotification("Created");
                textPromptDialog.close();
            }
        },
        Kirigami.Action {
            text: qsTr("Cancel")
            icon.name: "dialog-cancel"
            onTriggered: {
                textPromptDialog.close();
            }
        }
    ]

    QQC2.TextField {
        placeholderText: qsTr("Folder name…")
    }
}
```

*See also* [Dialog](qml-org-kde-kirigami-dialogs-dialog.md), [MenuDialog](qml-org-kde-kirigami-dialogs-menudialog.md)

## Property Documentation {#property-documentation}

### contentBottomPadding : real {#contentBottomPadding-prop}

The bottom padding of the content, within the scroll area.

### contentLeftPadding : real {#contentLeftPadding-prop}

The left padding of the content, within the scroll area.

### contentPadding : real {#contentPadding-prop}

The padding around the content, within the scroll area.

Default is Kirigami.Units.largeSpacing.

### contentRightPadding : real {#contentRightPadding-prop}

The right padding of the content, within the scroll area.

### contentTopPadding : real {#contentTopPadding-prop}

The top padding of the content, within the scroll area.

### dialogType : int {#dialogType-prop}

This property holds the dialogType. It can be either:

- [PromptDialog](qml-org-kde-kirigami-dialogs-promptdialog.md).Success: For a success message
- [PromptDialog](qml-org-kde-kirigami-dialogs-promptdialog.md).Warning: For a warning message
- [PromptDialog](qml-org-kde-kirigami-dialogs-promptdialog.md).Error: For an actual error
- [PromptDialog](qml-org-kde-kirigami-dialogs-promptdialog.md).Information: For an informational message
- [PromptDialog](qml-org-kde-kirigami-dialogs-promptdialog.md).None: No specific dialog type.

By default, the dialogType is [PromptDialog](qml-org-kde-kirigami-dialogs-promptdialog.md).None

### iconName : string {#iconName-prop}

This property holds the icon name used by the [PromptDialog](qml-org-kde-kirigami-dialogs-promptdialog.md).

### subtitle : string {#subtitle-prop}

The text to use in the dialog's contents.
