---
title: Keyboard
description: Set your keyboard model, layouts, key repeat and special key options.
source_url: https://invent.kde.org/plasma/plasma-desktop/-/blob/master/doc/kcontrol/keyboard/index.docbook
source_authors: [Mike McBride]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-desktop-interface fad996458a (kcms/keyboard); read from code, not clicked through"
---

# Keyboard

This module lets you choose how your keyboard works. The effect of these options depends on the features of your keyboard and the X server.

## Model and repeat

- **Model:** Your keyboard's hardware model, which is independent of your layout. Modern keyboards usually have two extra keys and are called “104-key” models, which is the default and probably what you want if you don't know what kind you have.
- **NumLock on startup:** **Turn on**, **Turn off** or **Leave unchanged** when the desktop starts.
- **Key repeat:** When this is on, holding down a key produces the same character repeatedly until you release it. Almost everyone will want this, because it makes moving through documents with the arrow keys much easier. **Delay** sets how long before it starts, and **Rate** how fast it repeats.
- **Test area:** Type here to check your settings.

## Layouts

**Layouts** lists the keyboard layouts you can switch between. **Enable** lets you change the list.

**Add…** opens a dialog to choose a layout, its variant, a short name shown in the system tray and a shortcut. The list can be narrowed down by language, and **Preview** shows the layout in a separate window.

**Move Up** and **Move Down** set the order, with the top one being the default. **Remove** takes a layout off the list.

### Spare layouts

You can have up to 4 main layouts, and all the others are spare. Spare layouts aren't included when cycling through the layouts, but you can choose them from the layout indicator's menu.

They let you toggle between a few layouts easily while keeping more close by. For example, you might use English, Ukrainian and German, but only the first two often. Set 2 main layouts and German as spare, and switching only moves between the first two.

A spare layout replaces the last main layout when it's chosen.

### Switching

**Configure Switching…** has these settings:

- **Switching layout affects:** **All windows**, **All windows on current desktop**, **All windows of current application** or **Current window only**.
- **Show OSD popup on layout change.**
- **Shortcuts:** **Change layout** and **Switch to last used layout**.
- **Legacy Shortcuts:** **Change layout** and **Alternative symbols**, which are handled by X11. They allow finer control of modifier-only shortcuts and have slightly better support on X11 in edge cases. Modifier keys can be used to type additional characters, symbols and diacritical marks.

## Key bindings

**Key Bindings** opens the special key settings. **Configure keyboard options** lets you set options for some special keys. Expand a group, choose your settings, and use **Reset** to clear a group.

For more about keyboard layouts on X11, see the [XKeyboardConfig page](https://www.freedesktop.org/wiki/Software/XKeyboardConfig) on freedesktop.org.
