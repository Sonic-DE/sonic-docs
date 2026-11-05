---
title: QML plugin
description: The upstream org.kde.telephony QML plugin, which SonicDE doesn't ship.
source_url: https://develop.kde.org/docs/packaging/plasma-mobile/telephony/qml-declarative-plugin-layer/
source_authors: [Alexey Andreyev, Carl Schwan, Michael Lang, Mikhail Zolotukhin]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "The current plasma-dialer source (commit a7a1369): the plugin's registration of org.kde.telephony 1.0, its singletons and USSD signals, and modem-daemon's install paths. The example is corrected to match: deviceUniList is a property, and there is no requestReceived signal. It was read, not built, so the example wasn't run. The source page's Future Work section is left out because it refers to repositories and plans that have since changed."
---

# QML plugin

**SonicDE doesn't ship this plugin.** It's part of the upstream [plasma-dialer](https://invent.kde.org/plasma-mobile/plasma-dialer) project, which you would need to build yourself.

[kde-telephony-plugin-declarative](https://invent.kde.org/plasma-mobile/plasma-dialer/-/tree/master/kde-telephony-plugin-declarative) provides the `org.kde.telephony` QML module, a set of QML interfaces to the [session daemons'](session-daemons.md) D-Bus APIs.

## Getting started

A minimal setup needs these parts of plasma-dialer:

- **kde-telephony-meta**, the D-Bus API descriptions.
- **modem-daemon**, for calls and history, which provides a D-Bus adaptor following those descriptions.
- **kde-telephony-plugin-declarative**, the QML plugin, which uses them through a D-Bus interface.

Once these are built, with `modem-daemon` running, you should be able to try USSD through QML. It's started from its `libexec` directory by the `org.kde.modem.daemon.desktop` autostart file.

```qml
import QtQuick
import org.kde.telephony

Item {
    Component.onCompleted: {
        const deviceUni = DeviceUtils.deviceUniList[0]
        const number = "*100#"
        UssdUtils.initiate(deviceUni, number)
    }

    Connections {
        target: UssdUtils

        function onNotificationReceived(deviceUni, message) {
            console.log(message)
        }

        function onErrorReceived(deviceUni, error) {
            console.log(error)
        }

        function onInitiated(deviceUni, command) {
            console.log("initiated")
        }
    }
}
```

USSD is probably the simplest part of the API to start with. The same logic can be found in the plasma-dialer application itself.
