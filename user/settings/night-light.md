---
title: Night Light
description: Make the colors on your screen warmer, always or between sunset and sunrise.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-workspace 5bd2c2047e (kcms/nightlight/ui/main.qml, kcms/nighttime/ui/), sonic-win 4cf630dd38 (src/plugins/nightlight/nightlightmanager.cpp, nightlightsettings.kcfg), sonic-power-management (applets/brightness); written from the code, not clicked through"
---

# Night Light

Night Light is a blue light filter that makes the colors on your screen warmer. It's off by default.

## Settings

- **Switching times:**
  - **Always off** turns Night Light off.
  - **Always on** applies the night temperature all the time.
  - **Sunrise and sunset** follows the day-night cycle. The **Configure…** button next to it opens the [Day-Night Cycle](#day-night-cycle) settings.
- **Day light temperature:** The color temperature during the day, from **Warm** to **Cool (no filter)**. The default is 6500 K. This only applies with **Sunrise and sunset**.
- **Night light temperature:** The color temperature at night, from **Warm** to **Cool (no filter)**. The default is 4500 K.

While you move a temperature slider, the screen briefly previews that color, and the current value appears in kelvin.

## Suspending it for a while

The Night Light section of the Brightness & Color widget in the system tray can suspend the filter and resume it, for example while you work on images. You can also give **Suspend/Resume Night Light** a key in the [Shortcuts](shortcuts.md) module, as it has none by default. A message on the screen tells you when Night Light is suspended or resumed.

## Day-Night Cycle

This separate module, under **Language & Time**, sets the times that Night Light and other time-based features, such as dynamic wallpapers, follow.

**Determine sunrise and sunset times** can be:

- **Based on device's location:** Choose **Automatically detect location**, which uses a location service such as GeoClue2 to update your location from time to time, or **Use manual location**, then enter a latitude and longitude or click your location on the map. Times can't be worked out during polar day or polar night, and the module tells you to choose custom times instead.
- **Using custom times:** Enter **Sunrise** and **Sunset** times, and a **Transition duration**, in minutes, for the change between them.
