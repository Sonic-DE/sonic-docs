---
title: When an application stops responding
description: What happens when you close a window whose application has frozen, and how to end the application.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-win a4e76b52c5 (src/x11window.cpp, src/window.cpp, src/helpers/killer/killer.cpp, src/kwin.kcfg, src/plugins/frozenapp); written from the code, not clicked through"
---

# When an application stops responding

Sometimes an application freezes and stops reacting to anything you do. [SonicWin](../applications/sonicwin.md), the window manager, notices this when you try to close one of its windows, and offers to end the application for you.

## What you see

When you close a window, SonicWin asks the application whether it's still running normally. If there's no answer after a short while:

1. The window's title gets **(Not Responding)** added to it. With desktop effects on, the window also turns grey, from the **Desaturate Unresponsive Applications** effect in [Desktop Effects](../settings/desktop-effects.md).
2. If there's still no answer after the same time again, a **Not Responding** dialog opens.

By default, each of these steps takes 2.5 seconds.

If the application recovers at any point, the title goes back to normal and the dialog closes by itself.

This only works with applications that support SonicWin's check. For one that doesn't, the window stays as it is and no dialog appears.

## The Not Responding dialog

The dialog names the application, and the window if its title is different. It warns that ending the application closes all of its windows, and that any unsaved work is lost. Its details show the application's process ID, and the name of the computer it runs on if that isn't your own.

- **Terminate** followed by the application's name ends the application.
- **Wait Longer** closes the dialog and gives the application more time. Close the window again if it still doesn't recover.

When you terminate an application, SonicWin first ends it in a way that lets a crash report be recorded, so its developers can find out what went wrong. If that doesn't work, it ends the application by force.

## Changing the waiting time

The waiting time is the `KillPingTimeout` setting in the `[Windows]` group of `~/.config/kwinrc`, in milliseconds, for both steps together. It's 5000 by default. Set it to `0` to turn this check off, so that no dialog appears.
