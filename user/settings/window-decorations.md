---
title: Window Decorations
description: Select a style for window borders and titlebar buttons.
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
- **Application menu button style:** How the **Application menu** button shows the menus (File, Edit, View…) of the application whose window it's in:
  - **Single menu button:** one button that drops down the menus as a list. This is the default.
  - **Always shown:** the menus sit as labels in the titlebar where the button is, left or right. The title moves aside to make room; menus that don't fit go into a menu button at the end.
  - **Shown on hover:** the same labels, but they only appear while the pointer is over the titlebar or a menu is open. The title fades out while they fade in.

  Click a label to open its menu. While one is open, Left and Right open the next menu, and moving the pointer over another label opens that one.
- **Show a search button with the application menu:** Adds a magnifier next to the menus. Type at least three letters to find any menu item by name, then click the result, or press Down and Enter.

The application's own menu bar is hidden while its menus are in the titlebar. These two options need the **Application menu** button in the titlebar, and a window decoration style that supports them, such as Silver; otherwise they're greyed out with a note saying why. Other styles keep showing the single button.

### Titlebar transparency

How see-through the titlebar is, and its per-application exceptions, are set in
[Transparency](transparency.md#titlebars), for window decoration styles that support it, such as Silver.
