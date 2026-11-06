---
title: Pointer settings for large displays
description: Get a larger mouse pointer and better acceleration on a big screen.
source_url: https://userbase.kde.org/Tutorials/Mouse_pointer_settings_for_large_displays
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "the Pointers and Mouse pages in sonic-docs, as checked against their modules; xinput property from the source page, not retested"
---

# Pointer settings for large displays

## A larger pointer

Open the [Pointers](../settings/pointers.md) module and choose a larger value in the **Size** field, if your theme offers one.

To set it by hand instead, open `~/.config/kcminputrc` in a text editor. In the `[Mouse]` section, add this line and save the file:

```ini
cursorSize=32
```

The pointer is larger the next time you log in.

## Better acceleration

The [Mouse](../settings/mouse.md) module has the pointer speed and acceleration settings, including **Legacy X11 acceleration** and **Acceleration threshold**. You can set a really fast acceleration there, for example 20x, and a threshold of 2 pixels.

That acceleration should be fine at medium distances but too fast over longer ones. Here's the trick to get better acceleration:

Press Alt+F2, enter `konsole` and press Return. In the console window, find the name of your mouse with:

```sh
xinput list
```

Then, in the [Autostart](../settings/autostart.md) module, add a login script containing this line, replacing `Logitech USB-PS/2 Optical Mouse` with the name of your mouse:

```sh
xinput --set-prop "Logitech USB-PS/2 Optical Mouse" "Device Accel Constant Deceleration" 1.2
```

Your mouse acceleration is better the next time you log in.
