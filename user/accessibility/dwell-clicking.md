---
title: Dwell clicking
description: Click by holding the mouse pointer still, without pressing a mouse button.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-win (src/dwellclicker.cpp, src/plugins/dwellclicker), sonic-desktop-interface (applets/dwellclicker, kcms/access/ui/DwellClicker.qml); written from the code, not clicked through"
---

# Dwell clicking

Dwell clicking is for people who find pressing mouse buttons hard or tiring. Move the pointer to where you want to click and hold it still: after a moment the click happens by itself. You can also double-click, right-click, middle-click and drag this way.

Dwell clicking is off by default.

## Turning dwell clicking on and off

There are three ways:

- In [System Settings](../settings/index.md), go to the [Accessibility](../settings/accessibility.md) module, open the **Dwell Clicker** page and check **Enable** next to **Click when pointer remains still**.
- Open the **Dwell Clicker** widget in the [System Tray](../desktop/system-tray.md) and use the **Dwell clicking** switch.
- Use a keyboard shortcut. There's none by default: set one in the [Shortcuts](../settings/shortcuts.md) module under **Toggle Dwell Clicking**. Each time you use it, a message on the screen says whether dwell clicking is now on or off.

All three change the same setting, so it doesn't matter which one you use. The setting is kept when you log out.

## Making a click

1. Move the pointer to where you want to click.
2. Hold it still. After a short delay, a ring appears around the pointer and fills up.
3. When the ring is full, the click happens.

Moving the pointer while the ring is filling starts the wait again from the new position. Small, shaky movements don't count: the pointer only has to stay within a few pixels of where it stopped, and you can change how many on the settings page.

After a click, nothing more happens until you move the pointer again, so leaving the pointer in one place doesn't keep clicking.

Clicks work with desktop effects turned off too, but the ring is only drawn when desktop effects are on.

## Choosing the type of click

The **Dwell Clicker** widget in the system tray lists the types of click under **Choose the next type of click**:

- **Left-click**
- **Double-click**
- **Click-and-drag**
- **Middle-click**
- **Right-click**

Choose one, and the next click is of that type. After that click, it goes back to a left-click.

**Click-and-drag** takes two dwells: the first presses the button down where you hold the pointer, then you move to where you want to drop and hold the pointer still again to let go. If you choose another type of click or turn dwell clicking off in the middle of a drag, the drag is cancelled rather than dropped.

Choosing the type that's already selected deselects it, and no clicks happen until you choose one again. This is useful when you want to rest the mouse or read without clicking anything by accident.

## Settings

The **Dwell Clicker** page of the [Accessibility](../settings/accessibility.md) module has these settings:

- **Motion Threshold:** How far, in pixels, the pointer can wander while you hold it still. Raise it if your hand isn't steady and the ring keeps starting again. The default is 5 pixels.
- **Delay Time:** How long the pointer has to be still before the ring appears, in milliseconds. The default is 150 milliseconds.
- **Dwell Time:** How long the ring takes to fill up, in milliseconds. A longer time gives you more chance to move away if you didn't mean to click. The default is 500 milliseconds; with 0, the click happens as soon as the delay is over, without a ring.
- **Dwell Color:** The color of the ring.

The page also reminds you where to set the shortcut that turns dwell clicking on and off.

### Keeping the type of click

Two more options aren't on the settings page. You can set them in the `[Effect-dwellclicker]` group of `~/.config/kwinrc`:

- `DefaultButton` is the type of click to go back to after each click: `10` left-click (the default), `11` double-click, `12` click-and-drag, `13` middle-click, `14` right-click, or `0` for none.
- `ButtonLocked=true` keeps the type of click you chose instead of going back to `DefaultButton` after each click.

They take effect the next time the window manager reloads its settings, for example when you apply a change on the **Dwell Clicker** settings page, or when you log in again.
