---
title: Desktop startup sequence
description: How the desktop session starts and what the main background services do.
source_url: https://userbase.kde.org/KDE_System_Administration/Startup
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-workspace (startkde/startplasma.cpp, startkde/plasma-session/startup.cpp, startkde/kcminit, ksmserver/), the stage's binaries; the source page describes kdeinit, klauncher and DCOP, which are gone, so this describes the current sequence; read from code, not clicked through"
---

# Desktop startup sequence

## The start script

The startup sequence begins with `startplasma-x11`, which the login manager normally calls once you've been authenticated. It sets up the environment, including running your [session environment scripts](session-environment-variables.md), and then hands control to `plasma_session`.

`plasma_session` starts the desktop's core in order:

1. `kcminit_startup` runs the initialization services.
2. `kded6` starts the background services.
3. The window manager starts. This is SonicWin, unless `KDEWM` is set.
4. `ksmserver`, the session manager, starts.
5. The desktop shell and autostart applications follow.

## Background services

All these background services are specific to a user. Unlike system daemons, they aren't shared between users.

### dbus-daemon: inter-process communication

`dbus-daemon` provides inter-process communication to applications as well as several other system components, such as NetworkManager, power management and applications from other desktops. It's a portable, cross-desktop project hosted at freedesktop.org. SonicDE is also gradually moving some of its communication to its own framework, `sonic-frameworks-ipc`.

D-Bus services can be reached from the shell with the `qdbus6` command-line tool.

### kded6: background services

`kded6` is a generic daemon that loads various service modules and runs them in the background. The [Background Services](../settings/background-services.md) module in System Settings shows the status of these modules and can disable some of them.

### kcminit: initialization services

`kcminit` runs initialization services during startup. Modules declare them with the `X-KDE-Init` line. They're typically used to initialize hardware based on your settings.

`kcminit --list` shows all the initialization services, and `kcminit <service>` runs a single one. This can be useful when investigating startup problems.

### ksmserver: session management

`ksmserver` is the session manager, which determines the lifetime of the session. It restores applications from the previous session.

The session manager restores one of the previous sessions. A session is a collection of applications, along with application-specific information that reflects their state when the session was saved. Sessions are stored in the `ksmserverrc` configuration file, with references to each application's state information.

For example, `ksmserverrc` may contain lines like these, and the application-specific information is stored in files named after each of these identifiers:

```ini
restartCommand1=kwin_x11,-session,110a0a0002000106760689100000019360000_1083342151_608625
restartCommand2=konsole,-session,10378ac070000108334204700000277690000_1083342151_552722
```

The state information of the window manager contains the location of the windows of all the other applications in the session.

### Autostart

Applications to start automatically are given by `.desktop` files in the `autostart` folder of your [configuration directories](xdg-filesystem-hierarchy.md#configuration). The [Autostart](../settings/autostart.md) module manages these.

A `.desktop` file can make its start conditional with the `X-KDE-autostart-condition` entry:

```ini
X-KDE-autostart-condition=ktiprc:TipOfDay:RunOnStart:true
```

This means the `ktiprc` configuration file is checked for a `RunOnStart` entry in the `[TipOfDay]` group. If there is no such entry, `true` is assumed, so the application starts by default.

## Desktop components

The main components of the desktop are the window manager, the command runner and the workspace, which is the desktop and its panels.

### SonicWin: window manager

The window manager is responsible for managing all the windows across the virtual desktops, including their initial placement, minimizing, maximizing, raising, lowering and switching focus between them.

By default, SonicWin is started as the window manager. To override this, set the `KDEWM` environment variable to the name of another window manager.

### KRunner: run dialog

[KRunner](../desktop/krunner.md) provides the Alt+F2 search and run dialog.

### sonicshell: desktop and panels

`sonicshell` provides the desktop and panels. See [Restarting the shell](../desktop/overview.md#restarting-the-shell).
