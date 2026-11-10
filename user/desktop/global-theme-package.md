---
title: Creating a global theme package
description: Save your desktop's look as a global theme with the Global Theme Explorer.
source_url: https://userbase.kde.org/Plasma/Create_a_Global_Theme_Package
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-theme-sdk 04a38e6f (lookandfeelexplorer/qml/Main.qml, lookandfeelexplorer/qml/MetadataEditor.qml, lookandfeelexplorer/lnflogic.cpp, lookandfeelexplorer/org.kde.plasma.lookandfeelexplorer.desktop); read from code, not clicked through"
---

# Creating a global theme package

A global theme bundles your desktop's look: the panel layout, the application and desktop styles, colors, icons, cursors and window decoration. You can save your own setup as a global theme with the Global Theme Explorer.

First, install the `sonic-theme-sdk` package, which gives you the Global Theme Explorer. The package name may differ between distributions. Open **Plasma Global Theme Explorer** from the application launcher, or run `lookandfeelexplorer`.

## Making a new theme

1. Arrange your desktop the way you want the theme to look.
2. In the Global Theme Explorer's sidebar, click **New Theme…**.
3. Fill in **Theme Plugin Name:**, a unique internal name, then **Theme Name:**, **Comment:**, **Author:**, **Email:**, **Website:** and **License:**, and click **OK**.

The theme is created in `~/.local/share/plasma/look-and-feel/<plugin name>/`, with its `metadata.json`. It also saves:

- your current panel and desktop layout;
- your current defaults: the application style, color scheme, icon theme, desktop style, cursor theme, window switcher and desktop switcher layouts, and window decoration.

The splash screen isn't saved.

## Changing a theme

Choose a theme in the list at the top of the sidebar. You can edit themes in your own folder; themes installed for the whole system are shown but can't be changed.

- Click the preview area (**Click to open an image**) to pick a preview image, or drop an image on it. It's used as the theme's thumbnail and full-screen preview.
- Change **Name:**, **Comment:**, **Author:**, **Email:**, **Website:** and **License:**.
- **Layout from current Plasma setup** replaces the theme's layout with your current panels and desktop.
- **Defaults from current setup** replaces the theme's defaults with your current styles, colors, icons, cursors and window decoration.
- Click **Save** to write the changes. The layout and defaults are only copied when you save.

**Open Theme Folder** opens the theme's folder in your file manager, if you want to add more to it by hand.

Choose the theme in System Settings' [Global Theme](../settings/global-theme.md) module.
