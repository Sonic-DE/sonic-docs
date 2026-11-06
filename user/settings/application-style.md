---
title: Application Style
description: Configure how buttons, menus and other interface elements are drawn.
source_url: https://invent.kde.org/plasma/plasma-workspace/-/blob/master/doc/kcontrol/kcmstyle/index.docbook
source_authors: [Mike McBride]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-workspace e4f0096493 (kcms/style); read from code, not clicked through"
---

# Application Style

This module configures how individual widgets are drawn.

> [!NOTE]
> A *widget* here means a user interface element such as a button, menu or scroll bar: the fundamental pieces an application is assembled from.

To change the colors of widgets, see [Colors](colors.md).

The grid shows previews of the available styles. Hover over one to see a brief description.

**Configure Style…** on a style's preview opens its own settings, if it has any. Depending on the style, you can change almost every aspect of it, such as tab bar alignment, toolbar separators, focus indicators, slider tick marks, keyboard accelerator visibility, window dragging, scrollbar buttons and menu transparency.

## Icons and toolbars

**Configure Icons and Toolbars…** below the grid opens further settings:

- **Show icons, On buttons:** Action buttons, like OK and Apply, have a small icon. Otherwise they only have text.
- **Show icons, In menus:** Applications show small icons beside most menu items. Otherwise menus only have text. This only affects newly started applications.
- **Main toolbar label** and **Secondary toolbar label:** Where each button's name appears by default. **None** shows no text, **Text only** replaces the icon with the name, **Beside icons** puts the name to the right of the icon and **Below icon** puts it underneath.

> [!TIP]
> These only set the *default*. Each application can override them.

## GNOME/GTK applications

**Configure GNOME/GTK Application Style…** lets you choose a GTK theme, install one from a file, or get new ones from the Internet with **Get New GNOME/GTK Application Styles…**.
