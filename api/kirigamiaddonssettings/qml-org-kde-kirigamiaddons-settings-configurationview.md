---
title: "ConfigurationView QML Type"
description: "This is an abstract view to display the configuration of an application."
---

# ConfigurationView QML Type

This is an abstract view to display the configuration of an application. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.settings

## Detailed Description {#details}

The various configuration modules can be defined by providing [ConfigurationModule](qml-org-kde-kirigamiaddons-settings-configurationmodule.md) to the modules property.

On desktop, this will display the modules in a list view and displaying the actual page next to it. On mobile, only the list of modules will be initially displayed.

```qml
import QtQuick.Controls as Controls
import org.kde.kirigamiaddons.settings as KirigamiSettings

Controls.Button {
    id: button

    KirigamiSettings.ConfigurationView {
        id: configuration

        window: button.Controls.ApplicationWindow.window as Kirigami.ApplicationWindow

        modules: [
            KirigamiSettings.ConfigurationModule {
                moduleId: "appearance"
                text: i18nc("@action:button", "Appearance")
                icon.name: "preferences-desktop-theme-global"
                page: () => Qt.createComponent("org.kde.tokodon", "AppearancePage")
            },
            ...
            KirigamiSettings.ConfigurationModule {
                moduleId: "about"
                text: i18nc("@action:button", "About Tokodon")
                icon.name: "help-about"
                page: () => Qt.createComponent("org.kde.kirigamiaddons.formcard", "AboutPage")
                category: i18nc("@title:group", "About")
            },
            KirigamiSettings.ConfigurationModule {
                moduleId: "aboutkde"
                text: i18nc("@action:button", "About KDE")
                // Bundled, so icon themes without a SonicDE icon don't show another logo.
                icon.source: "qrc:/kirigamiaddons/settings/sonicde.svg"
                page: () => Qt.createComponent("org.kde.kirigamiaddons.formcard", "AboutKDE")
                category: i18nc("@title:group", "About")
            }
        ]
    }

    icon.name: 'settings-configure-symbolic'
    text: i18nc("@action:button", "Settings")

    onClicked: configuration.open()
}
```

This will result in the following dialog on desktop:

And the following page on mobile:

## Property Documentation {#property-documentation}

### configViewItem : QtObject {#configViewItem-prop}

The current config page/window depending on platform.

Null if one currently doesn't exist.

### modules : list\<ConfigurationModule\> {#modules-prop}

This property holds the list of pages for the settings.

### \[default: "Settings"\] title : string {#title-prop}

This property holds the title of the config view.

### window : Kirigami.ApplicationWindow {#window-prop}

This property holds the parent window.

This needs to be set before calling open.

## Method Documentation {#method-documentation}

### open(*defaultModule* = '') {#open-method}

Open the configuration window for the given `defaultModule`.

The defaultModule corresponds to the moduleId of the default configuration that should be preselected when opening the configuration view. By default it is not specified, this will choose the first module.
