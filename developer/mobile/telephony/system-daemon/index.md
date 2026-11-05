---
title: System daemon
description: ModemManager and oFono, the system daemons that give a single interface to different modems.
source_url: https://develop.kde.org/docs/packaging/plasma-mobile/telephony/system-daemon-userland-dbus-ipc-level/
source_authors: [Alessio Mattiazzi, Alexey Andreyev, Carl Schwan, Mikhail Zolotukhin]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "ModemManagerQt uses in sonic-mobile-interface and sonic-network-manager, and SonicDE's repository list. No SonicDE code uses oFono. The descriptions of ModemManager, oFono and other systems are from the source page. The upstream project's migration history and status are left out."
---

# System daemon

Even when the kernel gives access to a modem, its device-specific messages have to be handled in userland. A daemon can unify access to different devices and track modem events. There are two similar open source projects for this, ModemManager and oFono, and both offer their API over D-Bus.

SonicDE uses ModemManager, through ModemManagerQt (`sonic-frameworks-modemmanager`). No SonicDE code uses oFono.

## ModemManager

[ModemManager](modem-manager.md) is a freedesktop.org project, started in 2008 to support USB dongles on desktops. It integrates with the higher-level NetworkManager daemon. It is also used by other desktops for USB modems, and by Phosh for telephony.

## oFono

[oFono](ofono.md) is a project from Nokia and Intel, started in 2009 with the Nokia N900. It integrates with the higher-level ConnMan connection manager. It is used by projects such as Ubuntu Touch and Sailfish OS, which maintain their own patches on top of it.

## Why ModemManager

The two share the goal of a single D-Bus API for modems. ModemManager has been developed more actively, new devices are added to it upstream, and on mainline devices such as the PinePhone and OnePlus 6 it has handled the modem more reliably. It is also what SonicDE's network management already uses, on the desktop as well. Projects such as [eg25-manager](https://gitlab.com/mobian1/eg25-manager), for the PinePhone's Quectel EG25 modem, depend on it and add support for low-power modes.

The main drawback is that oFono is the only option for Halium devices, but these [aren't supported](../../porting.md).

## What the daemon doesn't do

A system daemon tracks modem events and gives unified access to devices with different command sets. Handling call and message history, managing contacts and interacting with the rest of the user's environment are outside its scope. Its API is exported on the system bus so that [the session side](../session-daemons.md) can handle those.
