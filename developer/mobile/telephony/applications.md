---
title: Applications
description: Applications and components related to telephony, and which of them SonicDE ships.
source_url: https://develop.kde.org/docs/packaging/plasma-mobile/telephony/kde-application-layer/
source_authors: [Alexey Andreyev, Carl Schwan, Michael Lang, Mikhail Zolotukhin]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "SonicDE's repository list, and in sonic-mobile-interface and sonic-network-manager: the signal strength data provider and indicator, the mobile data quick setting, and the PIN dialog in the network daemon. That the upstream repositories still exist was checked; the applications weren't run. Old merge request links are left out."
---

# Applications

## Upstream applications

SonicDE doesn't ship these applications. They are upstream KDE projects that use ModemManagerQt.

### Plasma Dialer

[plasma-dialer](https://invent.kde.org/plasma-mobile/plasma-dialer) is a phone dialer.

Similar projects:

- [GNOME Calls](https://gitlab.gnome.org/GNOME/calls)
- [Dialer App](https://github.com/ubports/dialer-app) from UBports
- [Glacier Dialer](https://github.com/nemomobile-ux/glacier-dialer) from Nemo Mobile

### Spacebar

[Spacebar](https://invent.kde.org/plasma-mobile/spacebar) is an SMS and MMS application.

Similar projects:

- [Chatty](https://source.puri.sm/Librem5/chatty) from Librem 5
- [Messaging App](https://github.com/ubports/messaging-app) from UBports
- [Glacier Messages](https://github.com/nemomobile-ux/glacier-messages) from Nemo Mobile

### Plasma Settings

[plasma-settings](https://invent.kde.org/plasma-mobile/plasma-settings) is a settings application for phones, with options for selecting networks, modes and access points.

## SonicDE components

These aren't applications as such, but they are the client side of telephony that SonicDE does ship. All of them use ModemManagerQt, directly or through the network libraries.

### Mobile interface

`sonic-mobile-interface` holds the shell, containments and applets. It shows a signal strength indicator in the status bar and has a mobile data quick setting.

A similar project is [Phosh](https://gitlab.gnome.org/World/Phosh/phosh).

### Network management

`sonic-network-manager` manages network connections, including mobile ones. Its background service shows the dialog for unlocking a SIM with a PIN.
