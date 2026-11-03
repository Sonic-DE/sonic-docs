---
title: "FormFileDelegate QML Type"
description: "A Form delegate that let the user select a file."
---

# FormFileDelegate QML Type

A Form delegate that let the user select a file. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.formcard
- Inherits: [AbstractFormDelegate](qml-org-kde-kirigamiaddons-formcard-abstractformdelegate.md)

## Detailed Description {#details}

```qml
FormCard.FormHeader {
    title: "Information"
}

FormCard.FormCard {
    FormCard.FormFileDelegate {
        label: "Important document"
        currentFolder: StandardPaths.standardLocations(StandardPaths.DocumentsLocation)[0]
    }
}
```

## Property Documentation {#property-documentation}

### acceptLabel : string {#acceptLabel-prop}

The [acceptLabel](https://doc.qt.io/qt-6/qml-qtquick-dialogs-filedialog.html#acceptLabel-prop) of the file dialog.

### currentFolder : url {#currentFolder-prop}

The [currentFolder](https://doc.qt.io/qt-6/qml-qtquick-dialogs-filedialog.html#currentFolder-prop) of the file dialog.

### defaultSuffix : string {#defaultSuffix-prop}

The [defaultSuffix](https://doc.qt.io/qt-6/qml-qtquick-dialogs-filedialog.html#defaultSuffix-prop) of the file dialog.

### \[default: ""\] description : string {#description-prop}

A label containing secondary text that appears under the inherited text property.

This provides additional information shown in a faint gray color.

### fileMode : enumeration {#fileMode-prop}

The [fileMode](https://doc.qt.io/qt-6/qml-qtquick-dialogs-filedialog.html#fileMode-prop) of the file dialog.

### \[required\] label : string {#label-prop}

A label containing primary text that appears next to the selected file or folder name.

### nameFilters : string {#nameFilters-prop}

The [nameFilters](https://doc.qt.io/qt-6/qml-qtquick-dialogs-filedialog.html#nameFilters-prop) of the file dialog.

### options : flags {#options-prop}

The [options](https://doc.qt.io/qt-6/qml-qtquick-dialogs-filedialog.html#options-prop) of the file dialog.

### rejectLabel : string {#rejectLabel-prop}

The [rejectLabel](https://doc.qt.io/qt-6/qml-qtquick-dialogs-filedialog.html#rejectLabel-prop) of the file dialog.

### selectedFile : url {#selectedFile-prop}

The [selectedFile](https://doc.qt.io/qt-6/qml-qtquick-dialogs-filedialog.html#selectedFile-prop) of the file dialog.

### selectedFiles : url {#selectedFiles-prop}

The [selectedFiles](https://doc.qt.io/qt-6/qml-qtquick-dialogs-filedialog.html#selectedFiles-prop) of the file dialog.

> **Note:** In case, {FileDialog::OpenFiles} is set, only the first url will be displayed.

### \[read-only\] selectedNameFilter : var {#selectedNameFilter-prop}

The [selectedNameFilter](https://doc.qt.io/qt-6/qml-qtquick-dialogs-filedialog.html#selectedNameFilter-prop) of the file dialog.

## Signal Documentation {#signal-documentation}

### accepted() {#accepted-signal}

This signal is emitted when a valid file is selected

> **Note:** The corresponding handler is `onAccepted`.
