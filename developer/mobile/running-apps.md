---
title: Execute applications
description: The environment for running and debugging applications and the shell on the mobile interface.
source_url: https://develop.kde.org/docs/packaging/plasma-mobile/running-apps/
source_authors: [Carl Schwan, Devin Lin, Mikhail Zolotukhin, Pixie A, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "startplasmamobile.in, startplasma.cpp and startplasma-x11.cpp, the options in sonic-workspace/shell/main.cpp, settings.cpp in sonic-frameworks-quick-ui. QT_QUICK_CONTROLS_MOBILE was run through Kirigami.Settings.isMobile with all three values, and sonicshell with -p on a private X server and bus. The environment loop was run in bash. startplasmamobile itself wasn't run."
---

# Execute applications

This page describes the environment variables and steps for running and debugging applications on the mobile interface. Users don't need any of this, because applications start from the application drawer, but it's useful for development.

## Setting up the environment

To run an application on the device, set up your environment like the one the shell is running in:

```bash
while IFS= read -r -d '' variable; do
    export "$variable"
done < "/proc/$(pidof sonicshell)/environ"
```

If the shell isn't running, these are the variables the mobile session sets. `startplasmamobile` sets most of them, and `startplasma-x11` sets the rest:

```bash
export QT_QPA_PLATFORM='xlibre;xcb'
export QT_QPA_PLATFORMTHEME=KDE
export QT_QUICK_CONTROLS_STYLE=org.kde.breeze
export QT_QUICK_CONTROLS_MOBILE=true
export PLASMA_PLATFORM=phone:handset
export QT_IM_MODULE=sonicvirtualkeyboard
export XDG_CURRENT_DESKTOP=SonicDE:KDE
export KDE_FULL_SESSION=true
export KDE_SESSION_VERSION=6
```

`xlibre;xcb` prefers the QXLibre platform plugin and falls back to the `xcb` one.

## Starting the shell manually

The whole session is started by `startplasmamobile`. To start only the shell, with a new D-Bus session and without restarting automatically if it crashes:

```bash
dbus-run-session sonicshell -p org.kde.plasma.mobileshell --no-respawn
```

It needs an X server and a window manager, and exits if the activity manager, `kactivitymanagerd`, can't be started. On a running system, add `--replace` to replace the running shell instead.

## Forcing a user interface for one application

To start an application with its desktop user interface, if it has one, rather than the mobile one:

```bash
QT_QUICK_CONTROLS_MOBILE=false program-to-run
```

The inverse also works. To run an application on a desktop system with its mobile interface, set the variable to `true`. This sets what Kirigami applications see in `Kirigami.Settings.isMobile`.
