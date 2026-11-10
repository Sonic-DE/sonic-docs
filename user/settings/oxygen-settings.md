---
title: Oxygen settings
description: The settings of the Oxygen application style and window decoration.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-oxygen (kstyle/config/main.cpp, kstyle/config/ui/oxygenstyleconfig.ui, kstyle/config/oxygenanimationconfigwidget.cpp, kdecoration/config/ui/oxygenconfigurationui.ui, kdecoration/config/oxygenanimationconfigwidget.cpp, liboxygen/ui/); written from the code, not clicked through"
---

# Oxygen settings

Oxygen is the classic KDE look, which SonicDE includes for those who like it. Choose it in [Application Style](application-style.md) and [Window Decorations](window-decorations.md).

To change Oxygen's settings, click **Configure Style…** on the Oxygen preview in Application Style, or the edit button on the Oxygen preview in Window Decorations. To see both pages in one window, run `oxygen-settings6`.

## Oxygen Widget Style

### General

- **Windows' drag mode:** Where you can grab a window to move it: **Drag windows from titlebar only**, **Drag windows from titlebar, menubar and toolbars** or **Drag windows from all empty areas**.
- **Keyboard accelerators visibility:** When the underlined letters in menus and buttons show: **Always hide**, **Show when Alt key is pressed** or **Always show**.
- **Draw toolbar item separators**
- **Enable extended resize handles:** Makes the handles between resizable parts of a window easier to grab.
- **Draw window background gradient:** Draws Oxygen's soft gradient behind window content.

### Animations

**Enable animations** turns Oxygen's animations on and off. Each kind of animation can also be set on its own, with its duration: **Focus, mouseover and widget state transition**, **Toolbar highlight**, **Menu bar highlight**, **Menu highlight**, **Progress bar animation**, **Tab transitions**, **Label transitions**, **Text editor transitions**, **Combo box transitions** and **Progress bar busy indicator**.

### Views

- **Draw tree branch lines:** Draws lines connecting items in tree views.
- **Tree expander size:** **Tiny**, **Small** or **Normal**.
- **Draw focus indicator in lists**

### Scrollbars

- **Scrollbar width:** in pixels.
- **Top arrow button type:** and **Bottom arrow button type:** choose no buttons, one button or two buttons at each end of a scroll bar.

### Menu Highlight

How the item under the pointer is marked in menus: **Use dark color**, **Use selection color (plain)** or **Use selection color (subtle)**.

## Oxygen Window Decoration

### General

- **Title alignment:** **Left**, **Center**, **Center (Full Width)** or **Right**.
- **Button size:** **Small**, **Normal**, **Large** or **Very Large**.
- **Allow resizing maximized windows from window edges**
- **Use the same colors for title bar and window content**

### Animations

**Enable animations**, with **Button mouseover transition** (the highlight on titlebar buttons) and **Window active state change transitions** (the fade between shadow and glow when a window becomes active or inactive).

### Shadows

**Active Window Glow** and **Window Drop-Down Shadow** each have a **Size:**, a **Vertical Offset:**, an **Inner Color:** and an **Outer Color:**. **Follow accent color** takes the colors from your accent color instead.

### Window-Specific Overrides

Different settings for particular windows, matched by **Window Class Name** or **Window Title** with a regular expression. **Detect Window Properties** lets you click a window to fill these in. Under **Decoration Options**, an override can set a **Border size:** or **Hide window title bar**.
