---
title: Thunderbolt
description: Allow Thunderbolt devices to connect, once or every time.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-thunderbolt 1c4937a (src/kcm/kcm_bolt.json, src/kcm/ui/main.qml, DeviceView.qml, src/kded/kded_bolt.cpp, src/lib/dbushelper.cpp); written from the code, not clicked through"
---

# Thunderbolt

Thunderbolt devices, such as docks and external graphics cards, get direct access to your computer's memory. For your safety, a new Thunderbolt device has to be authorized before it works. This module, under **Connected Devices** in System Settings, lists your Thunderbolt devices and lets you authorize them.

The module works with the `bolt` system service, which your distribution provides. Without it, or on a computer without Thunderbolt, the module says **Thunderbolt subsystem is disabled or unavailable**. If Thunderbolt is turned off in your computer's firmware settings, it says **Thunderbolt support has been disabled in BIOS**; see your computer's manual for how to turn it on.

## Turning Thunderbolt on and off

The **Enable** switch at the top turns the Thunderbolt subsystem on or off.

## When you plug in a device

When an unauthorized device is connected, a **New Thunderbolt Device Detected** notification asks whether you want to authorize it:

- **Authorize Now** lets the device work until it's unplugged.
- **Authorize Permanently** also trusts it, so it's authorized by itself every time you plug it in.

## Device details

Click a device in the list to see its **Vendor:**, **UID:**, **Status:**, when it was **Authorized at:**, **Connected at:** and **Enrolled at:**, and whether it's **Trusted:**.

- **Authorize:** Lets a connected device work for now. It appears while the device is connected but not yet authorized.
- **Trust this Device:** Remembers an authorized device, so it's authorized automatically the next time it's connected.
- **Revoke Trust:** Forgets a trusted device. It then has to be authorized by hand each time it's connected.
