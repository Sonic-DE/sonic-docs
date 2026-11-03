---
title: "StatefulWindow QML Type"
description: "StatefulWindow takes care of providing standard functionalities for your application main window."
---

# StatefulWindow QML Type

[StatefulWindow](qml-org-kde-kirigamiaddons-actions-statefulwindow.md) takes care of providing standard functionalities for your application main window. [More...](#details)

- Import Statement: import org.kde.kirigamiaddons.actions
- Inherits: [ApplicationWindow](../kirigami/qml-org-kde-kirigami-applicationwindow.md)

## Detailed Description {#details}

This includes:

- Restoration of the window size accross restarts
- Handling some of the standard actions defined in your [AbstractKirigamiApplication](abstractkirigamiapplication.md) (AboutKDE and AboutApp)
- A command bar to access all the defined actions
- A shortcut editor

```qml
import org.kde.kirigamiaddons.actions as StatefulApp
import org.kde.kirigamiaddons.settings as Settings

StatefulApp.StatefulWindow {
    id: root

    windowName: 'Main'
    application: MyApplication {
        configurationView: Settings.ConfigurationView { ... }
    }
}
```

## Property Documentation {#property-documentation}

### application : AbstractKirigamiApplication {#application-prop}

This property holds the [AbstractKirigamiApplication](abstractkirigamiapplication.md) of your application.

The default [AbstractKirigamiApplication](abstractkirigamiapplication.md) provides the following actions:

- [KStandardActions::quit](../kconfiggui/kstandardactions.md#quit)
- [KStandardActions::keyBindings](../kconfiggui/kstandardactions.md#keyBindings)
- "Open Command Bar"
- "About App"
- "About KDE" (if your application id starts with org.kde.)

If you need more actions provide your own [AbstractKirigamiApplication](abstractkirigamiapplication.md) and overwrite [AbstractKirigamiApplication::setupActions](abstractkirigamiapplication.md#setupActions).

*See also* [AbstractKirigamiApplication](abstractkirigamiapplication.md)

### windowName : string {#windowName-prop}

This property holds the window's name.

This needs to be an unique identifier for your application and will be used to store the state of the window in your application config.

*See also* [WindowStateSaver](../kconfigqml/qml-org-kde-config-windowstatesaver.md)
