---
title: "Dialog QML Type"
description: "A dialog which has a NewStuff.Page at the base."
---

# Dialog QML Type

A dialog which has a NewStuff.Page at the base. [More...](#details)

- Import Statement: import org.kde.newstuff
- Inherits: [Window](https://doc.qt.io/qt-6/qml-qtquick-window.html)

## Detailed Description {#details}

This component is equivalent to the old DownloadDialog, but you should consider using NewStuff.Page instead for a more modern style of integration into your application's flow.

*See also* KNewStuff::DownloadDialog

## Property Documentation {#property-documentation}

### configFile : alias {#configFile-prop}

The configuration file to use for this button

### \[default: The name defined by your knsrc config file\] downloadNewWhat : string {#downloadNewWhat-prop}

Set the text that should appear as the dialog's title. Will be set as i18nd("knewstuff6", "Download New %1").

> **Note:** For the sake of consistency, you should NOT override the title property, just set this one

### engine : alias {#engine-prop}

The engine which handles the content in this dialog

### viewMode : alias {#viewMode-prop}

The default view mode of the dialog spawned by this button. This should be set using the NewStuff.Page.ViewMode enum.

*See also* NewStuff.Page.ViewMode

## Signal Documentation {#signal-documentation}

### aboutToShowDialog() {#aboutToShowDialog-signal}

Emitted when the Hot New Stuff dialog is about to be shown, usually as a result of the user having click on the button.

> **Note:** The corresponding handler is `onAboutToShowDialog`.

### entryEvent(var *entry*, int *event*) {#entryEvent-signal}

This forwards the entryEvent from the [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) engine

> **Note:** The corresponding handler is `onEntryEvent`.

*See also* Engine::entryEvent

## Method Documentation {#method-documentation}

### showEntryDetails(*providerId*, *entryId*) {#showEntryDetails-method}

Show the details page for a specific entry. If you call this function before the engine initialisation has been completed, the action itself will be postponed until that has happened.

`providerId` The provider ID for the entry you wish to show details for

`entryId` The unique ID for the entry you wish to show details for
