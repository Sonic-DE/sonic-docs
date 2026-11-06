---
title: Environment variables
description: The environment variables that influence SonicDE and its applications.
source_url: https://userbase.kde.org/KDE_System_Administration/Environment_Variables
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "a search of sonic-frameworks-*, sonic-workspace, sonic-win and sonic-desktop-interface for each variable (sonic-workspace startkde/startplasma.cpp, sonic-frameworks-crash-handler kcrash.cpp, sonic-frameworks-app-info ksycoca.cpp, sonic-frameworks-settings ksharedconfig.cpp); variables no code reads any more were left out"
---

# Environment variables

Many environment variables are useful for managing and controlling SonicDE. These are the supported ones. To set one for your whole session, see [Session environment variables](session-environment-variables.md).

## Automatically set variables

### KDE_FULL_SESSION

Set to true at startup. Some programs use it to tell whether they're running inside a full session. If you use this variable to detect a running session, check that its value isn't empty rather than checking that it equals true, because the value might change in future.

### KDE_SESSION_VERSION

Set at startup to the major version number of the desktop framework being run. This lets you find out, for example, which `kreadconfig` to run: `kreadconfig${KDE_SESSION_VERSION}`, which is `kreadconfig6` here.

## Display and window management

### KDEWM

If `KDEWM` is set, its value is used as the window manager at startup, instead of SonicWin.

## File system

### KDE_HOME_READONLY

Set this variable to indicate that your home folder is mounted read-only.

### KDESYCOCA

Lets you set the path and name of the generated [configuration cache](caches.md#ksycoca) file.

## Troubleshooting and debugging

### KDE_DEBUG

Setting this variable turns off the crash handler and lets the application create a [core dump](https://en.wikipedia.org/wiki/Core_dump) instead, which allows debugging after the fact. `ulimit -c 0` will also prevent core dumps.

## Look and feel

These variables influence the look and feel of the user interface.

### QT_QUICK_CONTROLS_MOBILE

Makes Kirigami applications behave as if they're running on a mobile device such as a phone.

### KDE_KIRIGAMI_TABLET_MODE

Makes Kirigami applications behave as if they're running on a tablet or a transformable laptop, preferring touch input to the mouse and keyboard.

## freedesktop.org compliance

These variables are defined in the [freedesktop.org base directory specification](https://specifications.freedesktop.org/basedir-spec/latest/) and are supported by all compliant environments and applications, including SonicDE. See also the [XDG filesystem hierarchy](xdg-filesystem-hierarchy.md) page.

### XDG_DATA_HOME

The base directory for data files specific to a user. If it's not set or is empty, `$HOME/.local/share` is used.

### XDG_CONFIG_HOME

The base directory for configuration files specific to a user. If it's not set or is empty, `$HOME/.config` is used.

### XDG_DATA_DIRS

The preference-ordered set of base directories to search for data files, in addition to `$XDG_DATA_HOME`. Separate the directories with a colon. If it's not set or is empty, `/usr/local/share/:/usr/share/` is used.

### XDG_CONFIG_DIRS

The preference-ordered set of base directories to search for configuration files, in addition to `$XDG_CONFIG_HOME`. Separate the directories with a colon. If it's not set or is empty, `/etc/xdg` is used.
