---
title: Desktop Session
description: Configure the session manager and logout settings.
source_url: https://invent.kde.org/plasma/plasma-desktop/-/blob/master/doc/kcontrol/kcmsmserver/index.docbook
source_authors: [Jost Schenck, Natalie Clarius]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-desktop-interface fad996458a (kcms/ksmserver); read from code, not clicked through"
---

# Desktop Session

This module configures the session manager and logout settings.

Session management is the desktop's ability to save the state of applications and windows when you log out, and restore them when you log back in.

## General

**Ask for confirmation** on shutdown, restart and logout shows the [logout confirmation screen](../desktop/logout-screen.md) when you do any of those. If it's off, your computer logs out, shuts down, and so on immediately after you click the button.

## Session Restore

**On login, launch apps that were open** has three choices:

- **On last logout:** Saves your session's state when you log out and restores it on the next login, so you can carry on with the desktop just as you left it.
- **When session was manually saved:** Restores a specific state you saved yourself. A **Save Session** button appears in the Application Launcher menu. Click it to remember the apps that are open and restore them on the next login. Click it again to replace the set of remembered apps.
- **Start with an empty session:** Never restores saved sessions.

**Ignored applications** lists applications to exclude from sessions, which won't be started when restoring one. Write their desktop file identifiers or, on X11, their executable names, separated by commas or colons.

## Firmware

**After next restart** you can choose **Enter UEFI firmware settings** or **Enter firmware setup screen**, depending on your system. The next time you restart, the computer enters its firmware setup, which may be easier than quickly pressing special keys during boot. **Restart Now** restarts right away.
