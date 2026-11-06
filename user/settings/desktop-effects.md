---
title: Desktop Effects
description: Turn on and configure desktop effects.
source_url: https://invent.kde.org/plasma/kwin-x11/-/blob/master/doc/kwineffects-x11/index.docbook
source_authors: [Mike McBride]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-win 4cf630dd38 (src/kcms/effects, src/kcms/common); read from code, not clicked through"
---

# Desktop Effects

This module turns on and configures desktop effects.

The main part of the page lists all available effects, grouped by Accessibility, Appearance, Focus, Peek at Desktop Animation, Tools, Virtual Desktop Switching Animation, Window Management and Window Open/Close Animation.

Use the search field above the list to find items.

Check an effect to turn it on. Each item has buttons to the right:

- An info button shows its author and license.
- A configure button, if it has settings, opens them.
- A video button, if it has a preview, plays it.

Some effects are mutually exclusive. For example, you'd only want Maximize or Magic Lamp, because both at once break the animations. These effects use radio buttons, so only one can be on.

All effects that aren't supported by the current compositing backend are hidden by default, such as OpenGL effects when using the software renderer. So are internal or helper effects, which replace core window manager functions or interact with other parts of the desktop. Normally there's no reason to change this, but **Configure Filter** can show them.

> [!NOTE]
> Changing these defaults can break your system.

**Get New…** opens a dialog listing effects from the Internet, where you can install and uninstall them.
