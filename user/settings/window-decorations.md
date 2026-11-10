---
title: Window Decorations
description: Select a style for window borders, titlebar buttons and titlebar opacity.
source_url: https://invent.kde.org/plasma/kwin-x11/-/blob/master/doc/kwindecoration-x11/index.docbook
source_authors: [Rik Hemsley]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-win 4cf630dd38 (src/kcms/decoration, src/decorations/decorationbridge.cpp), sonic-frameworks-color-scheme (src/ktoolsarea.h, ktoolsarea.cpp), sonic-frameworks-quick-silver-style (style/qtquickcontrols), sonic-silver (kdecoration/breeze.json, libbreezecommon/autotests/presettoolsareatest.cpp); read from code, not clicked through"
---

# Window Decorations

This module lets you select a style for the buttons and borders around windows.

![The Window Decorations module](images/window-decorations/main.png)

## Choosing a style

Choose a style from the preview list, or download a new one with **Get New…**. SonicDE's default style is **Silver**; **Breeze** and **Oxygen** are also included.

Each style has a different look, but also a different feel. Some have sometimes invisible resize borders all around the edge, which make resizing easier but moving harder. Some have no borders on certain edges. Experiment with the styles to find one that suits how you work.

The preview of each style has an edit button, with the tooltip **Edit** *style name* **Theme…**, for example **Edit Silver Theme…**, to open its settings. These apply to all windows. For different options on particular windows, see [Window Rules](window-rules.md), or the style's own window-specific overrides. The settings of SonicDE's styles are described in [Silver Settings](silver-settings.md#window-decoration), [Breeze settings](breeze-settings.md#breeze-window-decoration) and [Oxygen settings](oxygen-settings.md#oxygen-window-decoration).

> [!TIP]
> For accessibility, some styles support extra wide borders. If yours does, **Window border size:** lets you choose one here. **Theme default** uses the size the style recommends. Large borders are easier to see for low-vision users, and easier to grab for people with limited mobility or difficulty using a mouse.

> [!TIP]
> To create your own window decoration, see [Aurorae window decorations](../../developer/plasma/aurorae/index.md).

![A style's decoration options](images/window-decorations/decoration.png)

## Configuring the titlebar

**Configure Titlebar…** has these settings, which apply to every style.

### Titlebar buttons

![Titlebar button options](images/window-decorations/button.png)

This part sets where the buttons are on the titlebar. Drag buttons between the list and the titlebar, or around the titlebar until you have the order you want. To remove one, drop it back in the list.

- **Close windows by double clicking the menu button:** An extra way of closing, useful if you've removed the Close button. When you turn it on, a tip reminds you: **Click and hold on the menu button to show the menu.**
- **Show titlebar button tooltips:** Shows tooltips when you hover over the buttons.

### Titlebar opacity

These settings make the titlebar see-through. They're shared by every window decoration that supports them, and by the toolbars and menu bars of applications, including modern applications drawn with Qt Quick, so a window's whole top area looks the same. Open applications follow your changes straight away.

Titlebar transparency is off until you change one of these settings and apply it, or load a [Silver preset](silver-settings.md#presets) that uses it.

Titlebar opacity needs a style that supports it, such as Silver. Choosing a style without it, such as Breeze, turns these settings off. Going back to a style that supports them turns them on again, as you left them.

- **Active window** and **Inactive window:** How transparent the titlebar is, from **Transparent** to **Opaque**.
- **Always make maximized titlebars opaque.**
- **Blur titlebars that have transparency.**
- **Apply these opacity settings to the entire header area (toolbars and menu bars).**
- **Match the titlebar to the application colour.**

Loading a Silver preset sets these settings for you, and saving a preset records them. If you set titlebar transparency in Silver's own settings before, those settings were moved here automatically.

### Exceptions

An exception changes only the titlebar opacity settings above, for the applications it matches.

**Add Exception** adds one. Enter an application name or window class as a regular expression, then check each setting you want to change for those applications: **Active window opacity:** and **Inactive window opacity:** with their own percentages, and **Override:** for each of the other settings. Settings you leave unchecked follow the settings above.

The check box at the start of each exception, **Use this exception**, turns it on and off without deleting it. **Remove Exception** deletes it.

Exceptions marked **Default** come with SonicDE. You can't change or remove them, only switch them off with **Use this exception**.
