---
title: Plasma Theme Explorer
description: Look through a desktop theme's graphics and colors, and make your own theme.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-theme-sdk 04a38e6f (themeexplorer/src/qml/Main.qml, themeexplorer/src/qml/MetadataEditor.qml, themeexplorer/src/qml/ColorEditor.qml, themeexplorer/src/thememodel.cpp, themeexplorer/src/org.kde.plasma.themeexplorer.desktop), sonic-workspace (kcms/desktoptheme/kcm.cpp); written from the code, not clicked through"
---

# Plasma Theme Explorer

Plasma Theme Explorer shows every graphic of a desktop theme, the theme that draws panels, widgets and their pop-ups, and lets you edit them. It's for people who make themes. It comes with the `sonic-theme-sdk` package, whose name may differ between distributions.

Open it from the application launcher or by running `plasmathemeexplorer`. In System Settings' [Desktop Style](../settings/desktop-style.md) module, hovering over a style offers **Edit Theme…**, which opens that style here.

## Browsing a theme

Choose a theme in **Theme:** at the top. The window lists the theme's elements, such as panel backgrounds, buttons and dialogs, each drawn with the theme. Type in **Search…** to find an element.

Select an element to see its details beside the list: its image path, a description, and whether it's **Present in this theme** or **Missing from this theme**, in which case it comes from the default theme. **Show Margins** marks the element's margins, and the slider below changes the preview size.

Themes installed for the whole system are read-only: the window says so, and the editing buttons are turned off.

## Making and editing a theme

- **New Theme…** creates a theme of your own, in `~/.local/share/plasma/desktoptheme/`. Fill in **Theme Name:**, **Author:**, **Email:**, **License:** and **Website:**.
- **Edit Metadata…** changes these details later. Don't change the author or license of a theme you didn't make.
- **Edit Colors…** sets the theme's colors: the text, background, highlight and link colors, the colors of buttons and text views (normal, mouse over and focus), and the colors of the complementary area, which some panels and pop-ups use. A preview shows the result.
- **Open In Editor…** opens the selected element's graphic in Inkscape, which needs to be installed. For an element the theme doesn't have yet, the button reads **Create with Editor…**, and copies the default theme's graphic into your theme first.
- **Open Folder** opens the theme's folder in your file manager.

**Help** opens KDE's guide to the theme format.
