---
title: General Behavior
description: Configure tooltips, clicking, scrolling, drag and drop and tablet mode.
source_url: https://invent.kde.org/plasma/plasma-desktop/-/blob/master/doc/kcontrol/workspaceoptions/index.docbook
source_authors: [Burkhard Lück, Natalie Clarius]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-desktop-interface fad996458a (kcms/workspaceoptions); read from code, not clicked through"
---

# General Behavior

This module configures general workspace behavior.

## Plasma

**Allow Plasma to show:**

- **Panel and widget tooltips:** Tooltips appear when you hover over items in a panel or on the desktop.
- **OSD popups for status changes:** Widgets can show on-screen popups for changes like volume and brightness level, or switching audio devices.

## Scrolling

- **Clicking in scrollbar track:**
  - **Scrolls to the clicked location:** The scroll handle jumps to where you clicked. This is the default.
  - **Scrolls one page up or down:** Clicking moves by one page, and middle-clicking scrolls to the clicked location.
- **Prefer smooth scrolling:** Animates transitions when scrolling with a mouse wheel or the keyboard. Some applications may not honor this.

## Clicking

- **Clicking files or folders:**
  - **Selects them:** Files and folders must be double-clicked to open, and a single click selects them. This is the default.
  - **Opens them:** Files and folders open with a single click. To select them, click their selection markers, drag a rectangle around them or Ctrl+click.
- **Double-click interval:** Two clicks within this time count as a double-click. Some applications may not honor this. Double-click the test folder to check it: if it doesn't change its appearance, increase the interval.

## Drag and Drop

**When dragging files or folders:**

- **Always ask what to do:** Shows a dialog when you drop, unless you hold Shift to move, Ctrl to copy or Shift+Ctrl to create a symlink.
- **Move if on the same device:** Moves without asking. Hold Shift when dropping to see the other options.

## Touch

**Enable Tablet Mode:**

- **Never enabled:** Tablet mode stays off. Use this if you don't need tablet mode on your device.
- **Always enabled:** Tablet mode is always on. Use this if you mainly use the desktop with a touchscreen.
