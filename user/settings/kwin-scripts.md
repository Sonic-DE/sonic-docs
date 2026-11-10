---
title: KWin Scripts
description: Turn window manager scripts on and off, configure them, and install new ones.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-win a4e76b52c5 (src/kcms/scripts, src/scripting/scripting.cpp, src/plugins/desktopchangeosd, src/plugins/minimizeall, src/plugins/synchronizeskipswitcher, src/plugins/videowall), sonic-workspace-addons (kwin/scripts/virtualdesktopsonlyonprimary); written from the code, not clicked through"
---

# KWin Scripts

Scripts add small features to [SonicWin](../applications/sonicwin.md), the window manager. This module, under **Window Management** in [System Settings](index.md), lists the installed scripts.

- Check a script to turn it on, and uncheck it to turn it off. The change takes effect when you click **Apply**.
- If a script has settings, its configure button opens them.
- Use the search field above the list to find a script.
- **Delete…** marks a script you installed yourself for removal. It's removed when you click **Apply**; click the button again before that to keep it. Scripts that came with SonicDE can't be deleted.

**Install from File…** installs a script from a `.kwinscript` file on your computer. **Get New…** opens a dialog listing scripts from the Internet, where you can install and uninstall them.

## Scripts that come with SonicDE

- **Desktop Change OSD:** Shows the name of the virtual desktop when you switch. It's the same as **Show on-screen display when switching** in the [Virtual Desktops](virtual-desktops.md) module, which also has its settings.
- **MinimizeAll:** Adds a shortcut, Meta+Shift+D by default, that minimizes all windows on the current desktop. Press it again to restore the windows it minimized.
- **Synchronize Skip Switcher with Taskbar:** Leaves windows that don't appear in the task manager out of the task switcher (Alt+Tab) too.
- **Video Wall:** When a video player goes full screen, stretches it over all your screens, to make one big video wall. It works with the players in its list, which include VLC, SMPlayer and MPlayer.
- **Virtual Desktops Only on Primary:** With more than one screen, switching virtual desktops changes only the primary screen. Windows on the other screens are shown on all desktops. This script comes with the SonicDE add-ons package.

All of them are off by default.
