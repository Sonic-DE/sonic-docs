---
title: Desktop Effects
description: Turn on and configure desktop effects.
source_url: https://invent.kde.org/plasma/kwin-x11/-/blob/master/doc/kwineffects-x11/index.docbook
source_authors: [Mike McBride]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-win a4e76b52c5 (src/kcms/effects, src/kcms/common, src/debug_console.cpp); read from code, not clicked through"
---

# Desktop Effects

This module turns on and configures desktop effects.

The main part of the page lists the available effects, grouped by category, such as Accessibility, Appearance, Focus and Window Management.

The animations for opening, closing, maximizing, minimizing and full-screen windows, for peeking at the desktop and for switching virtual desktops aren't in this list. Neither are the popup, login and logout animations. Choose those in the [Animations](animations.md) module.

Use the search field above the list to find items.

Check an effect to turn it on. If it has settings, the **Configure…** button to its right opens them. [Effect settings](effect-settings.md) describes them. Click an effect to see its author and license below its description.

Some effects are mutually exclusive, because using two at once would break the animations. These effects use radio buttons, so only one can be on. Click the selected one again to turn it off.

Effects that the current compositing backend doesn't support are hidden, such as OpenGL effects when using the software renderer. To show them anyway, click the **Configure Filter** button next to the search field and uncheck **Exclude unsupported effects**.

Effects that SonicWin uses internally, such as Zoom, Invert and Present Windows, aren't listed at all. Zoom and Invert are set in the [Accessibility](accessibility.md) module.

**Get New…** opens a dialog listing effects from the Internet, where you can install and uninstall them.

## Effects for finding problems

Two effects help developers find drawing problems: **Show FPS** shows how fast SonicWin draws in a corner of the screen, and **Show Paint** highlights the parts of the screen that have just been redrawn. They aren't in this module. Turn them on in SonicWin's Debug Console instead:

1. Open [KRunner](../desktop/krunner.md) and type `kwin debug console`.
2. Choose **Open KWin debug console**.
3. Go to the **Effects** tab, where these two effects are at the top of the list, under their short names `showfps` and `showpaint`.
4. Click **Load** next to an effect to turn it on, and **Unload** to turn it off again.

The **Effects** tab lists every effect SonicWin knows, including the internal ones. Loading an effect there isn't saved in your settings, so it's off again the next time you log in.
