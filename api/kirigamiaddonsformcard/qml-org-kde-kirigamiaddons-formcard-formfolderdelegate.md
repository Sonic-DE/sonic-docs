---
title: "FormFolderDelegate QML Type"
description: "A Form delegate that let the user select a folder."
---

# FormFolderDelegate QML Type

A Form delegate that let the user select a folder. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard
- Inherits: [AbstractFormDelegate](qml-org-kde-kirigamiaddons-formcard-abstractformdelegate.md)

## Detailed Description {#details}

```qml
FormCard.FormHeader {
    title: "Information"
}

FormCard.FormCard {
    FormCard.FormFolderDelegate {
        label: "Important document"
        currentFolder: StandardPaths.standardLocations(StandardPaths.DocumentsLocation)[0]
    }
}
```

## Property Documentation {#property-documentation}

### acceptLabel : string {#acceptLabel-prop}

The [acceptLabel](https://doc.qt.io/qt-6/qml-qtquick-dialogs-folderdialog.html#acceptLabel-prop) of the folder dialog.

### currentFolder : url {#currentFolder-prop}

The [currentFolder](https://doc.qt.io/qt-6/qml-qtquick-dialogs-folderdialog.html#currentFolder-prop) of the folder dialog.

### \[default: ""\] description : string {#description-prop}

A label containing secondary text that appears under the inherited text property.

This provides additional information shown in a faint gray color.

### \[required\] label : string {#label-prop}

A label containing primary text that appears next to the selected folder or folder name.

### options : flags {#options-prop}

The [options](https://doc.qt.io/qt-6/qml-qtquick-dialogs-folderdialog.html#options-prop) of the folder dialog.

### rejectLabel : string {#rejectLabel-prop}

The [rejectLabel](https://doc.qt.io/qt-6/qml-qtquick-dialogs-folderdialog.html#rejectLabel-prop) of the folder dialog.

### selectedFile : url {#selectedFile-prop}

The [selectedFolder](https://doc.qt.io/qt-6/qml-qtquick-dialogs-folderdialog.html#selectedFolder-prop) of the folder dialog.

### selectedFolder : url {#selectedFolder-prop}

The [selectedFolder](https://doc.qt.io/qt-6/qml-qtquick-dialogs-folderdialog.html#selectedFolder-prop) of the folder dialog.

## Signal Documentation {#signal-documentation}

### accepted() {#accepted-signal}

This signal is emitted when a valid folder is selected

> **Note:** The corresponding handler is `onAccepted`.
