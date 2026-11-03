---
title: "Button QML Type"
description: "A button which when clicked will open a dialog with a NewStuff.Page at the base."
---

# Button QML Type

A button which when clicked will open a dialog with a NewStuff.Page at the base. [More...](#details)

- Import Statement: import org.kde.newstuff

## Detailed Description {#details}

This component is equivalent to the old Button.

*See also* [Button](qml-org-kde-newstuff-button.md)

## Property Documentation {#property-documentation}

### configFile : string {#configFile-prop}

The configuration file to use for this button

### downloadNewWhat : string {#downloadNewWhat-prop}

Set the text that should appear on the button. Will be set as i18nd("knewstuff6", "Download New %1…").

> **Note:** For the sake of consistency, you should NOT override the text property, just set this one

### engine : NewStuff.Engine {#engine-prop}

The engine which handles the content in this Button.

### viewMode : int {#viewMode-prop}

The view mode of the dialog spawned by this button, which overrides the default one (ViewMode.Tiles). This should be set using the NewStuff.Page.ViewMode enum. Note that ViewMode.Icons has been removed, and asking for it will return ViewMode.Tiles.

*See also* NewStuff.Page.ViewMode

### visibleWhenDisabled : bool {#visibleWhenDisabled-prop}

If this is true (default is false), the button will be shown when the Kiosk settings are such that Get Hot New Stuff is disallowed (and any other time enabled is set to false). Usually you would want to leave this alone, but occasionally you may have a reason to leave a button in place that the user is unable to enable.

## Signal Documentation {#signal-documentation}

### aboutToShowDialog() {#aboutToShowDialog-signal}

Emitted when the Hot New Stuff dialog is about to be shown, usually as a result of the user having click on the button.

> **Note:** The corresponding handler is `onAboutToShowDialog`.

### entryEvent(var *entry*, int *event*) {#entryEvent-signal}

This forwards the entryEvent from the [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) engine.

> **Note:** The corresponding handler is `onEntryEvent`.

*See also* Engine::entryEvent

## Method Documentation {#method-documentation}

### showDialog() {#showDialog-method}

Show the dialog (same as clicking the button), if allowed by the Kiosk settings.
