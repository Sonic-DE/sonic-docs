---
title: Touchpad
description: Manage your touchpad's taps, scrolling, pointer motion and sensitivity.
source_url: https://userbase.kde.org/System_Settings/Touchpad
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-desktop-interface (kcms/touchpad/ui/main.qml, kcms/touchpad/org.kde.touchpadshortcuts.desktop); read from code, not clicked through"
---

# Touchpad

This module manages the settings of your touchpad. Which settings you can change depends on your touchpad and its driver: settings your touchpad doesn't support are greyed out or not shown.

If no touchpad is found, the module says **No touchpad found**.

## Device

If you have more than one touchpad, **Device:** chooses the one to configure. The settings below apply to that touchpad.

## General

- **Enable device:** Turns the touchpad on or off.
- **Disable while mouse is connected:** Turns the touchpad off while an external mouse is plugged in.
- **Disable while typing:** Ignores the touchpad while you type, so you don't move the pointer by accident. This can interfere with video games.

The touchpad keys on many laptops turn the touchpad on and off too. In [Shortcuts](shortcuts.md), the **Touchpad** entry has **Enable Touchpad**, **Disable Touchpad** and **Toggle Touchpad**, which you can give your own shortcuts.

## Buttons

**Left and right buttons:**

- **Swap (left-handed mode):** Swaps the left and right buttons.
- **Press both simultaneously to middle-click:** Pressing the left and right buttons together gives a middle click. This adds 50 ms to every click, so that simultaneous presses can be detected.

## Pointer motion

- **Pointer speed:** How fast the pointer moves. Set it with the slider or the number box next to it.
- **Enable pointer acceleration:** The pointer travels further the faster you move your finger.

## Scrolling

- **Scrolling speed:** A slider from **Slower** to **Faster**.
- **Scroll by:**
  - **Moving two fingers anywhere:** Slide two fingers on the touchpad to scroll.
  - **Moving one finger on edge:** Slide one finger along the edge of the touchpad to scroll.
- **Invert scroll direction (Natural scrolling):** The content moves the same way as your fingers, like on a touchscreen.
- **Disable horizontal scrolling:** Ignores sideways scrolling.

## Clicking

Many touchpads have no separate buttons: you press the touchpad itself.

- **Right-click by:**
  - **Pressing bottom-right corner:** Pressing the bottom-right corner of the touchpad is a right click.
  - **Pressing anywhere with two fingers:** Pressing with two fingers anywhere is a right click, and with three fingers a middle click.
- **Middle-click by:** shown when you right-click with the corner:
  - **Pressing bottom-middle edge**
  - **Pressing bottom-left and bottom-right corners**

## Tapping

- **Tap to click:** A short tap on the touchpad is a click, without pressing it down.
- **Allow dragging after tapping:** Tap, then tap again and slide your finger at once to drag. Lift your finger to drop.
- **Allow briefly lifting finger during tap-and-drag:** The drag continues if you lift your finger for a moment, so you can reposition it on a small touchpad.
- **Two-finger tap:** What tapping with two fingers does when **Tap to click** is on:
  - **Right-click**, and a three-finger tap is a middle click.
  - **Middle-click**, and a three-finger tap is a right click.
