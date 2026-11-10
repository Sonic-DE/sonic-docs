---
title: Brightness & Color
description: Change screen and keyboard brightness, Night Light and dark mode from the system tray.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-power-management f835ef7d3 (applets/brightness: main.qml, PopupDialog.qml, BrightnessItem.qml, KeyboardColorItem.qml, NightLightItem.qml, DarkModeItem.qml), sonic-win a4e76b52c5 (src/colors/colormanager.cpp); written from the code, not clicked through"
---

# Brightness & Color

The Brightness & Color widget sits in the [System Tray](system-tray.md). Click its icon to open it. It only shows the parts your computer supports.

## In the widget

- **Brightness:** One slider for each display whose brightness can be changed, labelled with the display's name when there's more than one. Displays without hardware brightness control are dimmed in software, and their slider says "(software dimming)" after the display's name; see [Displays without a backlight](../settings/power-management.md#displays-without-a-backlight).
- **Keyboard Backlight:** Changes the brightness of your keyboard's backlight, if it has one.
- **Keyboard Color:** On keyboards whose backlight color can be changed, **Follow accent color** makes the backlight use your [accent color](../settings/colors.md).
- **Night Light:** Shows whether [Night Light](../settings/night-light.md) is on, its current color temperature and when the next change happens. The **Suspend** switch pauses it until you turn the switch off again. **Configure…** opens the Night Light settings; when Night Light is off, the button reads **Enable and Configure…**, and you turn Night Light on there.
- **Theme:** The **Dark Mode** switch moves between the light and dark versions of your theme, and the line underneath says which one it will switch to. **Configure…** opens Quick Settings, where you choose those two themes.

## Using the icon

- Scroll over the icon to change the screen brightness. Hold Shift while scrolling with a mouse wheel to change it in smaller steps.
- Middle-click the icon to suspend Night Light, or resume it. This only works while Night Light is turned on.
- Hover over it to see the current brightness and Night Light status.

Right-click the icon for **Configure Night Light…**, which opens the [Night Light](../settings/night-light.md) module, and **Configure Power Management…**, which opens [Power Management](../settings/power-management.md).
