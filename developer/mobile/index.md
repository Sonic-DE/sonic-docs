---
title: Mobile interface
description: SonicDE's interface for phones, what it needs, and how to develop for it.
source_url: https://develop.kde.org/docs/packaging/plasma-mobile/
source_authors: [Alexey Andreyev, Carl Schwan, Mikhail Zolotukhin, Phu Nguyen, ivan tkachenko]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-mobile-interface: its startplasmamobile script, CMake files and QML. The shell was started from the stage on a private X server with real SonicWin and a private bus and settings, using simulated mouse input. It hasn't run on a phone, with touch input, or as a full session from startplasmamobile."
---

# Mobile interface

The mobile interface is SonicDE's shell for phones, built with the same technologies as the desktop. It lives in the `sonic-mobile-interface` repository, which still uses its upstream name, Plasma Mobile, in places such as the session name.

To write an application for it, start with the [Kirigami](../kirigami/setup-cpp.md) tutorial. Kirigami applications adapt to the size of the screen, so the same application can run on the desktop and on a phone. To write a widget, see the [Plasma documentation](../plasma/index.md).

## Current status

The shell runs on X11, and its session starts through `startplasma-x11`. It hasn't been tried on a phone yet. Some things differ from the upstream Plasma Mobile:

- **Navigation uses the panel's buttons.** Touch gestures such as swiping up for the task switcher aren't available, because SonicWin's gesture handlers don't activate on X11.
- **The on-screen keyboard is Sonic Keyboard.** It runs inside each application and opens when a text field gets focus, so the panel's keyboard buttons only control a keyboard in the shell itself.
- **There is no Waydroid integration or screen recording quick setting,** as both depend on Wayland.
- **Quick settings can't appear over the lock screen.** Raising a window over the locker is a Wayland feature, and `RaiseLockscreen` does nothing here.

## In this section

- [Execute applications](running-apps.md) covers the environment for running and debugging applications and the shell.
- [Porting a new device](porting.md) explains what hardware support is needed and how to add a device's settings.
- [Telephony stack](telephony/index.md) describes the layers between the modem and the applications, and which of them SonicDE ships.
