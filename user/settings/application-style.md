---
title: Application Style
description: Configure how buttons, menus and other interface elements are drawn.
source_url: https://invent.kde.org/plasma/plasma-workspace/-/blob/master/doc/kcontrol/kcmstyle/index.docbook
source_authors: [Mike McBride]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-workspace e4f0096493 (kcms/style), sonic-qt-theme-bridge (platformtheme/khintssettings.cpp), sonic-frameworks-settings-ui (kstylemanager.cpp), sonic-silver (look-and-feel defaults), sonic-gtk-theme-bridge (kded/gtkconfig.cpp, kconf_update/gtktheme.cpp); read from code, not clicked through"
---

# Application Style

This module configures how individual widgets are drawn.

> [!NOTE]
> A *widget* here means a user interface element such as a button, menu or scroll bar: the fundamental pieces an application is assembled from.

To change the colors of widgets, see [Colors](colors.md).

The grid shows previews of the available styles. Hover over one to see a brief description.

SonicDE's own style, **Silver**, is the default. If no style is set, or the chosen one isn't installed, applications use Silver. **Breeze** and **Oxygen** are also available.

When you apply a different style, applications that are already open switch to it straight away; you don't need to restart them.

**Configure Style…** on a style's preview opens its own settings, if it has any. Depending on the style, you can change almost every aspect of it, such as tab bar alignment, toolbar separators, focus indicators, slider tick marks, keyboard accelerator visibility, window dragging, scrollbar buttons and menu transparency. See [Silver Settings](silver-settings.md), [Breeze settings](breeze-settings.md) and [Oxygen settings](oxygen-settings.md) for what each of SonicDE's styles offers.

## Icons and toolbars

**Configure Icons and Toolbars…** below the grid opens further settings:

- **Show icons, On buttons:** Action buttons, like OK and Apply, have a small icon. Otherwise they only have text.
- **Show icons, In menus:** Applications show small icons beside most menu items. Otherwise menus only have text. This only affects newly started applications.
- **Main toolbar label** and **Secondary toolbar label:** Where each button's name appears by default. **None** shows no text, **Text only** replaces the icon with the name, **Beside icons** puts the name to the right of the icon and **Below icon** puts it underneath.

> [!TIP]
> These only set the *default*. Each application can override them.

## GNOME/GTK applications

GNOME and other GTK applications use the **Silver** GTK theme by default, so they match the rest of the desktop. If you were using the Breeze GTK theme, or no GTK theme was set, SonicDE switches you to Silver, and from Breeze Dark to Silver Dark.

**Configure GNOME/GTK Application Style…** lets you choose another **GTK theme:**. **Preview…** opens a window showing what the chosen theme looks like. You can also install a theme with **Install from File…**, or get new ones from the Internet with **Get New GNOME/GTK Application Styles…**.

You don't need to set anything else up for GTK applications. The **GNOME/GTK Settings Synchronization Service**, which runs in the background, passes your SonicDE settings on to them: the GTK theme and dark mode, fonts and text scaling, the icon, pointer and sound themes, colors, titlebar button order, toolbar style, icons on buttons and in menus, double-click interval, cursor blinking and animations. You can turn it off under [Background Services](background-services.md), but GTK applications then stop following your changes.
