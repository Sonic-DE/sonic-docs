---
title: Breeze settings
description: The settings of the Breeze application style and window decoration.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-breeze (kstyle/config/main.cpp, kstyle/config/ui/breezestyleconfig.ui, kdecoration/config/ui/breezeconfigurationui.ui, kdecoration/config/ui/breezeexceptiondialog.ui); written from the code, not clicked through"
---

# Breeze settings

Breeze is KDE's look, which SonicDE also includes. SonicDE's own default is [Silver](silver-settings.md). If you prefer Breeze, choose it in [Application Style](application-style.md) and [Window Decorations](window-decorations.md).

To change Breeze's settings, click **Configure Style…** on the Breeze preview in Application Style, or the edit button on the Breeze preview in Window Decorations. To see both pages in one window, run `breeze-settings6`.

## Breeze Widget Style

### General

- **Windows' drag mode:** Where you can grab a window to move it: **Drag windows from titlebar only**, **Drag windows from titlebar, menubar and toolbars** or **Drag windows from all empty areas**.
- **Draw focus indicator in lists:** Marks the item that has the keyboard focus in a list.
- **Keyboard accelerators visibility:** When the underlined letters in menus and buttons show: **Always hide**, **Show when Alt key is pressed** or **Always show**.
- **Center tabbar tabs:** Centers the tabs in a tab bar.
- **Draw toolbar item separators:** Shows the separator lines between groups of toolbar buttons.
- **Draw slider tick marks:** Shows the scale marks along sliders.
- **Enable extended resize handles:** Makes the handles between resizable parts of a window easier to grab.

### Frames

- **Draw frame around dockable panels**
- **Draw frame around side panels**
- **Draw a thin line to indicate focus in menus and menubars**

### Scrollbars

**Top arrow button type:** and **Bottom arrow button type:** choose **No buttons**, **One button** or **Two buttons** at each end of a scroll bar.

### Transparency

How see-through menus are is set in [Transparency](transparency.md#menus), shared with the Silver style.

## Breeze Window Decoration

### General

- **Title alignment:** **Left**, **Center**, **Center (Full Width)** or **Right**.
- **Button size:** **Tiny**, **Small**, **Medium**, **Large** or **Very Large**.
- **Draw a circle around close button**
- **Draw border on maximized and tiled windows:** Lets you resize maximized and tiled windows from the edges of the screen. Scroll bars and the close button then move in a little, so they no longer touch the screen edge.
- **Draw titlebar background gradient**
- **Round bottom corners of windows with no borders**

### Shadows and Outline

**Shadow size:** (**None**, **Small**, **Medium**, **Large** or **Very Large**), **Shadow strength:**, **Shadow color:** and **Draw window outline**.

### Window-Specific Overrides

Different settings for particular windows. **Add** a new override, then match windows by **Window Class Name** or **Window Title** with a regular expression; **Detect Window Properties…** lets you click a window to fill these in. Under **Decoration Options**, choose a **Border size:** for those windows, or **Hide window title bar**. **Edit**, **Remove**, **Move Up** and **Move Down** manage the list. The check box on each override turns it on and off.
