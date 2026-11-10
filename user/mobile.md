---
title: Mobile interface
description: SonicDE's interface for tablets and phones, what works today, its home screen, quick settings and first-start setup, and devices it was reported to work on.
source_url: https://userbase.kde.org/Plasma_Mobile
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-mobile-interface (bin/, containments/homescreens/, quicksettings/, initialstart/, shell/contents/configuration/, kcms/navigation) and the developer/mobile pages in sonic-docs; the device table comes from a report on KDE's Plasma Mobile test image and hasn't been retested with SonicDE"
---

# Mobile interface

`sonic-mobile-interface` provides SonicDE's interface for touch devices such as tablets and phones. To use it, choose **SonicDE Mobile** from the list of sessions on the login screen. For its settings, see [Mobile settings](mobile-settings.md). For developers, see [Mobile interface](../developer/mobile/index.md).

> [!NOTE]
> The mobile session used to have another name on the login screen. If you used it before upgrading, choose **SonicDE Mobile** once more.

## Current status

The mobile interface runs on X11, like the rest of SonicDE. It hasn't been tried on a phone yet. Compared with other mobile interfaces, a few things are different:

- **You move around with the buttons on the navigation panel** at the bottom of the screen. Swiping gestures, such as swiping up to see your open applications, don't work yet.
- **The on-screen keyboard is Sonic Keyboard.** It opens by itself when you tap a text field.
- **There's no Waydroid support for Android apps, and no screen recording quick setting,** because both need Wayland.

## First start

The first time you start the mobile session, a setup wizard walks you through the basics:

- **Before we get started…:** the screen brightness, **Display Scaling** for the size of things on the screen, and **Dark Theme**.
- **Time and Date:** your time zone and **24-Hour Format**.
- **System Navigation:** for now there's nothing to choose here. You move around with the buttons on the navigation panel, because gestures don't work yet.
- **Network:** connect to a Wi-Fi network.
- **Cellular:** if your device has a modem, turn **Mobile Data** on and set up an APN with **Add APN**. Your carrier can tell you what to enter.

## Home screen

The home screen is called **Folio**. It holds pages of application icons, folders and widgets, with a favorites bar along the edge.

Press and hold an empty part of the home screen to edit it. Three buttons appear: **Wallpapers** to choose a wallpaper, **Settings** for the home screen's settings, and **Widgets** to add widgets.

Folio's settings are:

- **Icons:** **Number of rows** and **Number of columns** on each page (they swap when you rotate the screen), and **Size of icons on homescreen**.
- **Homescreen:** **Show labels on homescreen**, **Show labels in favorites bar**, **Lock layout** to stop icons being moved by accident, **Page transition effect** (**Slide**, **Cube**, **Fade**, **Stack** or **Rotation**) and **Double tap to lock device**.
- **Favorites Bar:** **Show background** behind the favorites bar.
- **Wallpaper:** **Wallpaper blur effect**: **None**, **Simple** or **Full**.
- **General:** **Export layout** saves your home screen layout to a file, and **Import layout** loads one, replacing your current layout after asking you to confirm.

The settings window also has **Change Homescreen**, where **Select Homescreen** lets you switch to **Halcyon**, a home screen focused on simplicity and ease of use. Your current home screen's settings are kept, and come back if you switch again. Halcyon's settings are **Wallpaper blur effect** and **Double tap to lock device**.

## Quick settings

Pull down from the top of the screen for the action drawer with your quick settings: **Wi-Fi**, **Mobile Data**, **Hotspot**, **Bluetooth**, **Airplane Mode**, **Sound**, **Battery**, **Flashlight**, **Night Color**, **Do Not Disturb**, **Caffeine** (stops the device going to sleep), **Auto-rotate**, **Display Config**, **Screenshot**, **Docked Mode**, **Auto Hide Panels**, **Virtual Keyboard**, **Settings** and **Shut Down**.

To change their order, hide some, or choose how the drawer opens, see [Mobile settings](mobile-settings.md#shell).

## Devices reported to work

These reports come from KDE's Plasma Mobile test image for x86_64 tablets with 32-bit UEFI support. They haven't been tested with SonicDE.

| Device | Wi-Fi | Touchscreen | Dock | Auto rotation |
| --- | --- | --- | --- | --- |
| HP Stream 8 | Yes | Yes | Unknown | Unknown |
| Dell Venue 8 Pro | Yes, as Alpha6 | Yes | Unknown | Unknown |
| Wacom Cintiq Companion 2 | Yes | Yes | Unknown | Unknown |
| ASUS Transformer T100TAL | Yes | Yes | Yes | No |
| Acer One S1003 (N16H1) | No | Yes | Yes | No |
