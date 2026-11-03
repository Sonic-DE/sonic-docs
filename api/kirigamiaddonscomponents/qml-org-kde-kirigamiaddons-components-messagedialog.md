---
title: "MessageDialog QML Type"
description: "A message dialog with success, warning, error, and information styles."
---

# MessageDialog QML Type

A message dialog with success, warning, error, and information styles. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.components

## Detailed Description {#details}

Set the `title` and [subtitle](qml-org-kde-kirigamiaddons-components-messagedialog.md#subtitle-prop) to describe the message, choose a [dialogType](qml-org-kde-kirigamiaddons-components-messagedialog.md#dialogType-prop), and set `standardButtons` for the available actions. Add extra content as child items; it appears below the title and subtitle.

```qml
import QtQuick.Controls as Controls
import org.kde.kirigamiaddons.components as Components

Controls.ApplicationWindow {
    visible: true

    Components.MessageDialog {
        id: errorDialog

        dialogType: Components.MessageDialog.Error
        title: "Unable to connect"
        subtitle: "Check your network connection and try again."
        dontShowAgainName: "connectionError"
        standardButtons: Controls.Dialog.Ok
    }

    Controls.Button {
        text: "Show message"
        onClicked: errorDialog.openDialog()
    }
}
```

Call [openDialog](qml-org-kde-kirigamiaddons-components-messagedialog.md#openDialog-method)() to show the dialog and honor any saved choice. Set [dontShowAgainName](qml-org-kde-kirigamiaddons-components-messagedialog.md#dontShowAgainName-prop) to offer a persistent "Do not show again" checkbox.

## Property Documentation {#property-documentation}

### \[default: "Notification Messages"\] configGroupName : string {#configGroupName-prop}

The configuration group used to store the "Do not show again" choice.

### \[default: MessageDialog.Success\] dialogType : int {#dialogType-prop}

Selects the message style and its default icon and title. It can be:

| Constant | Description |
| --- | --- |
| MessageDialog.Success | For a success message. |
| MessageDialog.Warning | For a warning message. |
| MessageDialog.Error | For an error message. |
| MessageDialog.Information | For an informational message. |

### \[default: ""\] dontShowAgainName : string {#dontShowAgainName-prop}

The configuration key used to store the "Do not show again" choice.

When this property is non-empty, a checkbox is shown for supported standard button combinations. The choice is saved in the application configuration under [configGroupName](qml-org-kde-kirigamiaddons-components-messagedialog.md#configGroupName-prop).

Call [openDialog](qml-org-kde-kirigamiaddons-components-messagedialog.md#openDialog-method)() to show the dialog. A saved choice can suppress it and emit its corresponding result signal. A positive choice emits `accepted()` or `applied()`, depending on the button. A negative choice emits `rejected()` or `discarded()`. Accepted and rejected button actions close the dialog. A choice is remembered only when a supported result button is clicked. Cancel and dismissing the dialog do not save a preference. Supported combinations have exactly one positive button (Ok, Open, Save, Save All, Yes, Yes to All, Apply, Retry, or Ignore), at most one negative button (No, No to All, or Discard), and optionally Cancel, Close, or Abort. Other combinations open normally without the checkbox.

> **Warning:** Replacing [contentItem](https://doc.qt.io/qt-6/qml-qtquick-controls-popup.html#contentItem-prop) or [footer](https://doc.qt.io/qt-6/qml-qtquick-controls-dialog.html#footer-prop), or setting [header](https://doc.qt.io/qt-6/qml-qtquick-controls-dialog.html#header-prop), is unsupported. The dialog logs an error if any of these properties is changed.

### iconName : string {#iconName-prop}

The name of the icon shown beside the message. By default, this is selected from [dialogType](qml-org-kde-kirigamiaddons-components-messagedialog.md#dialogType-prop). Set it to an empty string to hide the icon.

### \[default\] mainContent : QtObject {#mainContent-prop}

The default property for additional content items. Child items appear below the title and subtitle. Do not replace the dialog's [contentItem](https://doc.qt.io/qt-6/qml-qtquick-controls-popup.html#contentItem-prop).

### subtitle : string {#subtitle-prop}

The message text shown below the title. For additional content, add child items to the dialog.

## Method Documentation {#method-documentation}

### openDialog() {#openDialog-method}

Open the dialog only if the user didn't check the "Do not remind me" checkbox previously. If a stored choice suppresses the dialog, its corresponding result signal is emitted instead.

### AbstractButton standardButton(StandardButton *button*) {#standardButton-method}

Returns the standard button matching `button`, or `null` if that button is not present in `standardButtons`.
