---
title: Autostart
description: Manage the programs and scripts that run when you log in or out.
source_url: https://invent.kde.org/plasma/plasma-workspace/-/blob/master/doc/kcontrol/autostart/index.docbook
source_authors: [Anne-Marie Mahfouf]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-workspace e4f0096493 (kcms/autostart, startkde); read from code, not clicked through"
---

# Autostart

This module manages which programs start with your session. You can add programs or scripts that run automatically when you log in or out.

> [!NOTE]
> All changes in this module are applied immediately.

It looks in `$HOME/.config/autostart/` for applications and login scripts, `$HOME/.config/plasma-workspace/env` for pre-startup scripts and `$HOME/.config/plasma-workspace/shutdown` for logout scripts, and displays what it finds, grouped into **Applications**, **Login Scripts**, **Pre-startup Scripts** and **Logout Scripts**.

Login scripts are `.desktop` files with an `X-KDE-AutostartScript=true` key. Pre-startup scripts run earlier and can be used to set environment variables.

See also [Desktop Session](session.md) and [Background Services](background-services.md) for how to configure startup.

Some applications handle autostart on their own. You might turn it on or off in their settings, or need to quit them with **File > Quit**, because otherwise they keep running in the system tray and restart on your next login.

## Managing items

Each entry shows the icon and name of the program or script. Hover over it to reveal these buttons:

- **See properties:** Changes the properties of a program or login script. The default command comes from the `Exec` key of its `.desktop` file. A logout script's command is its path and can't be changed.
- **Remove entry:** Immediately removes the `.desktop` file for the program, or the script or symbolic link.

If a script isn't executable, the module says so and offers **Make Executable**.

## Adding items

**Add New** at the top lets you choose the type of item:

- **Application…:** Opens the application chooser. After you choose one, its properties appear. Its `.desktop` file is copied to your autostart folder.
- **Login Script…:** Asks for the location of the script. It gets a `.desktop` file in your autostart folder and runs when the session starts.
- **Logout Script…:** Asks for the location of the script. It's copied or symlinked into `$HOME/.config/plasma-workspace/shutdown` and runs after you've logged out.

## Status and logs

On systems using systemd, selecting an application shows details of its systemd unit: its **Name**, its **Status**, when it was **Last activated** and its logs from the journal, with **Start** and **Stop** buttons. If it hasn't been started yet, details become available after a restart.

## Turning off items from your distribution

To turn off an autostart item, copy its `.desktop` file to your personal autostart folder. Anything of the same name in `$HOME/.config/autostart` overrides the `.desktop` file in the default package. Add this line to the copy:

    Hidden=true
