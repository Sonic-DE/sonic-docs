---
title: Display Configuration
description: Configure your monitors' size, orientation and arrangement.
source_url: https://userbase.kde.org/System_Settings/Display_and_Monitor
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-screen 1a141e82 (kcm/kcm_kscreen.json, kcm/ui/main.qml, Panel.qml, OutputPanel.qml, Orientation.qml, ScreenView.qml, plasmoid/, osd/, common/osdaction.cpp, kded/daemon.cpp), sonic-screen-library (backends/xrandr); read from code, not clicked through"
---

# Display Configuration

![The monitor settings, in an older version](images/display-configuration/overview.png)

Here you can configure the physical characteristics of your screens, such as their size and orientation, and how several monitors are arranged.

After you apply a change, the module asks **Keep display configuration?**, with **Keep** and **Revert** buttons. If you don't answer, it goes back to the previous configuration after 15 seconds, so an unusable setting can't leave you stuck.

These related modules sit next to it in the **Display & Monitor** category:

- [Night Light](night-light.md) makes the colors on your screen warmer.
- [Gamma](monitor-gamma.md) tweaks the way your monitor displays colors.
- [Compositor](compositor.md) sets up the desktop effects and how windows are drawn.

## Arranging screens

The top of the module shows your screens as they're arranged. Click a screen to choose it; its settings appear underneath.

With more than one screen, **Edit Arrangement** lets you **Drag screens to re-arrange them**, and **Collapse** shrinks the view again. All screens must touch each other: the module won't save an arrangement with gaps between them.

**Identify Screens**, at the top of the module, briefly shows each screen's name on that screen, so you know which is which. It's only there when you have more than one screen.

## Screen settings

- **Device:** **Enabled** turns the chosen screen on or off. At least one screen must stay on.
- **Primary:** With two screens, makes the chosen one the primary screen. Your main desktop and its panels appear on it, and some older games use it to decide where to appear. It doesn't change where notifications or other windows appear. With three or more screens, **Change Screen Priorities…** opens a list where you **Raise priority** or **Lower priority** of each screen; the first is the primary one.
- **Resolution:** The screen's resolution. If the screen supports only one, it's shown without a list.
- **Refresh rate:** How many times per second the picture is redrawn, from the rates the screen supports at the chosen resolution.
- **Orientation:** Rotates the picture: **No Rotation**, **90° Clockwise**, **Upside Down** or **90° Counterclockwise**.
- **Replica of:** Shows the same picture as another screen, for example a projector mirroring your laptop.

## Global settings

- **Global scale:** Makes everything on the screen bigger or smaller, with a slider and a box where you can type a percentage. After you apply it, the module explains that the change takes effect once the computer restarts, and offers a **Restart** button. If you pick a value that isn't a multiple of 25%, a note explains that it's limited to multiples of 6.25% to avoid visual glitches.

## The Display Configuration widget

The Display Configuration widget sits in the [System Tray](../desktop/system-tray.md). Its icon only shows in the tray itself while presentation mode is on; otherwise it's among the hidden items.

- **Screen Layout:** Buttons to switch quickly between ways of using two screens. They're the same as in the [display switcher](#when-you-connect-a-screen) below. With only one screen plugged in, the widget explains that you need more than one.
- **Enable Presentation Mode:** Stops the screen and computer turning off by themselves, for example while you give a talk. The widget also lists any applications that have turned presentation mode on.

Right-click the icon for **Configure Display Settings…**, which opens this module.

## When you connect a screen

When you plug in a screen that SonicDE hasn't seen before, a display switcher appears on the screen with these choices:

- **Only use external screen**
- **Only use built-in screen**
- **Mirror screens**
- **Extend to left of built-in screen**
- **Extend to right of built-in screen**
- **Leave unchanged**

The settings button in the switcher, **Configure displays in more detail**, opens this module. Screens you've set up before go straight back to the arrangement you used last time.

You can open the switcher at any time with the **Switch Display** shortcut: Meta+P, or the display key that some laptops have. Change it in [Shortcuts](shortcuts.md).
