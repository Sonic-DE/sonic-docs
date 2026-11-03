---
title: "Action QML Type"
description: "An action which when triggered will open a NewStuff.Dialog or a NewStuff.Page, depending on settings."
---

# Action QML Type

An action which when triggered will open a NewStuff.Dialog or a NewStuff.Page, depending on settings. [More...](#details)

- Import Statement: import org.kde.newstuff

## Detailed Description {#details}

This component is equivalent to the old Button component, but functions in more modern applications

The following is a simple example of how to use this Action to show wallpapers from the KDE Store, on a system where Plasma has been installed (and consequently the wallpaper knsrc file is available). This also shows how to make the action push a page to a [pageStack](qml-org-kde-newstuff-action.md#pageStack-prop) rather than opening a dialog:

```qml
import org.kde.newstuff as NewStuff

NewStuff.Action {
    configFile: "wallpaper.knsrc"
    text: i18n("&Get New Wallpapers…")
    pageStack: applicationWindow().pageStack
    onEntryEvent: function(entry, event) {
        if (event === NewStuff.Entry.StatusChangedEvent) {
            // A entry was installed, updated or removed
        } else if (event === NewStuff.Entry.AdoptedEvent) {
            // The "AdoptionCommand" from the knsrc file was run for the given entry.
            // This should not require refreshing the data for the model
        }
    }
}
```

*See also* NewStuff.Button

## Property Documentation {#property-documentation}

### configFile : string {#configFile-prop}

The configuration file to use for the Page created by this action

### \[read-only\] engine : NewStuff.Engine {#engine-prop}

The engine which handles the content in this Action This will be null until the action has been triggered the first time

### pageStack : Item {#pageStack-prop}

If this is set, the action will push a NewStuff.Page onto this page stack (and request it is made visible if triggered again). If you do not set this property, the action will spawn a NewStuff.Dialog instead.

> **Note:** If you are building a KCM, set this to your \`\`\`kcm\`\`\` object.

### \[since 6.1\] transientParent : Window {#transientParent-prop}

The parent window for the dialog created by invoking the action

This property was introduced in Qt 6.1.

### viewMode : int {#viewMode-prop}

The view mode of the page spawned by this action, which overrides the default one (ViewMode.Tiles). This should be set using the NewStuff.Page.ViewMode enum. Note that ViewMode.Icons has been removed, and asking for it will return ViewMode.Tiles.

*See also* Page::ViewMode

### visibleWhenDisabled : bool {#visibleWhenDisabled-prop}

If this is true (default is false), the action will be shown when the Kiosk settings are such that Get Hot New Stuff is disallowed (and any other time enabled is set to false). Usually you would want to leave this alone, but occasionally you may have a reason to leave a action in place that the user is unable to enable.

## Signal Documentation {#signal-documentation}

### entryEvent(var *entry*, int *event*) {#entryEvent-signal}

This forwards the `entry` changed `event` from the [QtQuick](https://doc.qt.io/qt-6/qtquick-qmlmodule.html) engine.

> **Note:** The corresponding handler is `onEntryEvent`.

*See also* Engine::entryEvent

## Method Documentation {#method-documentation}

### showHotNewStuff() {#showHotNewStuff-method}

Show the page/dialog (same as activating the action), if allowed by the Kiosk settings
