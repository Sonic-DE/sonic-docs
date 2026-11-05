---
title: Telephony stack
description: The layers between a phone's modem and its applications, and which of them SonicDE ships.
source_url: https://develop.kde.org/docs/packaging/plasma-mobile/telephony/
source_authors: [Alexey Andreyev, Carl Schwan, Mikhail Zolotukhin, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "SonicDE's repository list for each named project, and ModemManager uses in sonic-mobile-interface and sonic-network-manager. The source page's architecture diagram, hosted on an image site with no stated license, is replaced by the list of layers."
---

# Telephony stack

Telephony on a phone passes through several layers, from the kernel up to the applications:

1. The [kernel layer](kernel-layer.md) gives userland access to the modem.
2. The [system daemon](system-daemon/index.md), ModemManager, gives a single interface to different modems over D-Bus.
3. [Session daemons](session-daemons.md) handle calls, messages and history for the user.
4. The [QML plugin](qml-plugin.md) gives applications an interface to those daemons.
5. [Applications](applications.md) are what the user sees.

## What SonicDE ships

SonicDE includes the parts that handle mobile data and the modem's state:

- `sonic-frameworks-modemmanager`, the Qt interface to ModemManager (ModemManagerQt).
- `sonic-network-manager`, which manages mobile connections and shows the SIM PIN dialog.
- `sonic-mobile-interface`, with its signal strength indicator, mobile data quick setting, cellular step in the initial setup, and detection of access point settings.

**SonicDE doesn't ship the session daemons, the QML plugin, or a dialer or messaging application.** They belong to upstream KDE projects, and these pages describe them so that you can see how the stack fits together.

## Similar projects

- [Cellular Telephony Architecture](https://docs.sailfishos.org/Reference/Core_Areas_and_APIs/Networking/Cellular_Telephony_Architecture/) in the Sailfish OS documentation
