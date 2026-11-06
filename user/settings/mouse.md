---
title: Mouse
description: Configure your mouse or other pointing device.
source_url: https://invent.kde.org/plasma/plasma-desktop/-/blob/master/doc/kcontrol/mouse/index.docbook
source_authors: [Mike McBride, Brad Hards]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-desktop-interface fad996458a (kcms/mouse); read from code, not clicked through"
---

# Mouse

This module configures your pointing device, which may be a mouse, a trackball or another piece of hardware that does a similar job. The options available depend on your device and driver. Single-click or double-click for opening files is set in [General Behavior](general-behavior.md).

- **Device:** Selects which device to configure. **Enable device** turns it on or off.
- **Left and right buttons:**
  - **Swap (left-handed mode):** Swaps the functions of the left and right buttons. If your device has more than two buttons, the others aren't affected.
  - **Press both simultaneously to middle-click:** Useful if you don't have a middle button. It adds 50 ms to each click, which is needed to detect simultaneous presses.
- **Pointer speed:** Changes how far the pointer moves on the screen for a given movement of the device.
- **Enable pointer acceleration:** The pointer travels further the faster you move it.
- **Scrolling speed:** From slower to faster.
- **Scrolling:**
  - **Invert scroll direction:** The scroll wheel works in the opposite direction.
  - **Hold down middle button and move mouse to scroll:** A substitute for a scroll wheel. It interferes with applications that use middle-button drag, such as some image editors, document viewers and games.

Some drivers show these instead:

- **Legacy X11 acceleration** and **Acceleration threshold**
- **Double-click interval**, **Drag start time** and **Drag start distance**
- **Mouse wheel scrolls by**

## Extra buttons

**Configure Extra Buttons…** binds extra mouse buttons to keys. Click **Add Binding…**, press the mouse button, then enter the new key combination.
