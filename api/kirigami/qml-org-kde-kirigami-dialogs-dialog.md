---
title: "Dialog QML Type"
description: "Popup dialog that is used for short tasks and user interaction."
---

# Dialog QML Type

Popup dialog that is used for short tasks and user interaction. [More...](#details)

- Import Statement: import org.kde.kirigami.dialogs
- Inherited By: [MenuDialog](qml-org-kde-kirigami-dialogs-menudialog.md) and [PromptDialog](qml-org-kde-kirigami-dialogs-promptdialog.md)

## Detailed Description {#details}

Dialog consists of three components: the header, the content, and the footer.

By default, the header is a heading with text specified by the title property.

By default, the footer consists of a row of buttons specified by the standardButtons and [customFooterActions](qml-org-kde-kirigami-dialogs-dialog.md#customFooterActions-prop) properties.

The implicitHeight and implicitWidth of the dialog contentItem is the primary hint used for the dialog size. The dialog will be the minimum size required for the header, footer and content unless it is larger than [maximumHeight](qml-org-kde-kirigami-dialogs-dialog.md#maximumHeight-prop) and [maximumWidth](qml-org-kde-kirigami-dialogs-dialog.md#maximumWidth-prop). Use [preferredHeight](qml-org-kde-kirigami-dialogs-dialog.md#preferredHeight-prop) and [preferredWidth](qml-org-kde-kirigami-dialogs-dialog.md#preferredWidth-prop) in order to manually specify a size for the dialog.

If the content height exceeds the maximum height of the dialog, the dialog's contents will become scrollable.

If the contentItem is a [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html), the dialog will take care of the necessary scrollbars and scrolling behaviour. Do not attempt to nest ListViews (it must be the top level item), as the scrolling behaviour will not be handled. Use [ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html)'s header and footer instead.

Example for a selection dialog:

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami

Kirigami.Dialog {
    title: i18n("Dialog")
    padding: 0
    preferredWidth: Kirigami.Units.gridUnit * 16

    standardButtons: Kirigami.Dialog.Ok | Kirigami.Dialog.Cancel

    onAccepted: console.log("OK button pressed")
    onRejected: console.log("Rejected")

    ColumnLayout {
        spacing: 0
        Repeater {
            model: 5
            delegate: QQC2.CheckDelegate {
                topPadding: Kirigami.Units.smallSpacing * 2
                bottomPadding: Kirigami.Units.smallSpacing * 2
                Layout.fillWidth: true
                text: modelData
            }
        }
    }
}
```

Example with scrolling ([ListView](https://doc.qt.io/qt-6/qml-qtquick-listview.html) scrolling behaviour is handled by the Dialog):

```qml
import QtQuick
import QtQuick.Layouts
import QtQuick.Controls as QQC2
import org.kde.kirigami as Kirigami

Kirigami.Dialog {
    id: scrollableDialog
    title: i18n("Select Number")

    ListView {
        id: listView
        // hints for the dialog dimensions
        implicitWidth: Kirigami.Units.gridUnit * 16
        implicitHeight: Kirigami.Units.gridUnit * 16

        model: 100
        delegate: QQC2.RadioDelegate {
            topPadding: Kirigami.Units.smallSpacing * 2
            bottomPadding: Kirigami.Units.smallSpacing * 2
            implicitWidth: listView.width
            text: modelData
        }
    }
}
```

There are also sub-components of the Dialog that target specific usecases, and can reduce boilerplate code if used.

*See also* [PromptDialog](qml-org-kde-kirigami-dialogs-promptdialog.md), [MenuDialog](qml-org-kde-kirigami-dialogs-menudialog.md)

## Property Documentation {#property-documentation}

### \[read-only\] absoluteMaximumHeight : real {#absoluteMaximumHeight-prop}

This property sets the absolute maximum height the dialog can have.

The height restriction is solely applied on the content, so if the maximum height given is not larger than the height of the header and footer, it will be ignored.

This is the window height, subtracted by largeSpacing on both the top and bottom.

### \[read-only\] absoluteMaximumWidth : real {#absoluteMaximumWidth-prop}

This property holds the absolute maximum width the dialog can have.

By default, it is the window width, subtracted by largeSpacing on both the top and bottom.

### customFooterActions : list\<T.Action\> {#customFooterActions-prop}

This property holds the custom actions displayed in the footer.

Example usage:

```cpp
import QtQuick
import org.kde.kirigami as Kirigami

Kirigami.PromptDialog {
    id: dialog
    title: i18n("Confirm Playback")
    subtitle: i18n("Are you sure you want to play this song? It's really loud!")

    standardButtons: Kirigami.Dialog.Cancel
    customFooterActions: [
        Kirigami.Action {
            text: i18n("Play")
            icon.name: "media-playback-start"
            onTriggered: {
                //...
                dialog.close();
            }
        }
    ]
}
```

*See also* [Action](qml-org-kde-kirigami-action.md)

### dialogChildren : Item {#dialogChildren-prop}

This property holds the content items of the dialog.

The initial height and width of the dialog is calculated from the implicitWidth and implicitHeight of the content.

### \[default\] dialogData : QtObject {#dialogData-prop}

This property holds the dialog's contents; includes Items and QtObjects.

### flatFooterButtons : bool {#flatFooterButtons-prop}

This property sets whether the footer button style should be flat.

### footerLeadingComponent : Component {#footerLeadingComponent-prop}

This property holds the component to the left of the footer buttons.

### footerTrailingComponent : Component {#footerTrailingComponent-prop}

his property holds the component to the right of the footer buttons.

### maximumHeight : real {#maximumHeight-prop}

This property holds the maximum height the dialog can have (including the header and footer).

The height restriction is solely enforced on the content, so if the maximum height given is not larger than the height of the header and footer, it will be ignored.

By default, this is [absoluteMaximumHeight](qml-org-kde-kirigami-dialogs-dialog.md#absoluteMaximumHeight-prop).

### maximumWidth : real {#maximumWidth-prop}

This property holds the maximum width the dialog can have.

By default, this is [absoluteMaximumWidth](qml-org-kde-kirigami-dialogs-dialog.md#absoluteMaximumWidth-prop).

### preferredHeight : real {#preferredHeight-prop}

This property holds the preferred height of the dialog.

The content will receive a hint for how tall it should be to have the dialog to be this height.

If the content, header or footer require more space, then the height of the dialog will expand to the necessary amount of space.

### preferredWidth : real {#preferredWidth-prop}

This property holds the preferred width of the dialog.

The content will receive a hint for how wide it should be to have the dialog be this wide.

If the content, header or footer require more space, then the width of the dialog will expand to the necessary amount of space.

### showCloseButton : bool {#showCloseButton-prop}

This property sets whether to show the close button in the header.
