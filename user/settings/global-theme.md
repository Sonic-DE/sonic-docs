---
title: Global Theme
description: Change the look and feel of many desktop components at once.
source_url: https://invent.kde.org/plasma/plasma-workspace/-/blob/master/doc/kcontrol/lookandfeel/index.docbook
source_authors: [Natalie Clarius]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-workspace (kcms/lookandfeel), sonic-silver (look-and-feel, layout-templates); read from code, not clicked through"
---

# Global Theme

Global themes provide a common look and feel for many components at once:

- **Desktop layout:** An arrangement of panels and widgets, for example a bottom panel with a task manager and application launcher.
- **Colors:** The color palette used throughout the desktop and applications.
- **Application Style:** The appearance of interface elements such as buttons, menus and scroll bars.
- **Window Decoration Style**, **Window Decoration Size** and **Titlebar Buttons layout:** Window borders and titlebar buttons.
- **Icons:** The icons used throughout the desktop and applications.
- **Desktop Style:** The appearance of panels and widgets.
- **Pointers:** Mouse pointers.
- **Fonts:** The fonts used throughout the desktop and applications.
- **Task Switcher:** The overlay for switching between open windows, usually opened with Alt+Tab.
- **Splash Screen:** The loading screen shown when the desktop starts.

Applying a global theme can change all of these together, or only some of them. You can also apply individual components using the other System Settings modules.

## The Silver themes

SonicDE's own look is Silver, and **Silver Light - Bottom Panel** is the default global theme. SonicDE comes with these Silver global themes:

- **Silver Light - Bottom Panel:** Light theme with a traditional panel at the bottom and labelled tasks.
- **Silver Light - Left Panel:** Light theme with the panel on the left.
- **Silver Dark - Bottom Panel:** Dark theme with a traditional panel at the bottom and labelled tasks.
- **Silver Dark - Left Panel:** Dark theme with the panel on the left.

The light themes use the Silver Light colors, Silver icons, Silver Light pointers and the Silver Light desktop style; the dark themes use Silver Dark, Silver Dark icons, Silver pointers and the Silver Dark desktop style. All of them use the Silver application style, Silver window borders and the Silver splash screen.

The panel layouts of these themes are also available on their own, as **Silver Bottom Panel** and **Silver Left Panel**, when you add a panel to the desktop. Each has an application launcher, a task manager and a system tray.

Breeze and its themes are an optional extra in SonicDE, from the separate `sonic-breeze` package.

![The Global Theme module](images/global-theme/main.png)

## Applying a global theme

Themes that include a desktop layout say **Contains Desktop layout** under their name. If a theme comes with a full-screen preview, hovering over it offers **Preview Theme**, which shows it.

Click a theme and a dialog asks which parts to apply: **Appearance settings** and **Desktop and window layout**.

![Choosing what to apply](images/global-theme/component-chooser_1.png)

> [!WARNING]
> Applying a desktop layout deletes your current set of desktops, panels, docks and widgets, and replaces them with the theme's.

**Choose what to apply…** shows every component, so you can choose them individually.

![Choosing individual components](images/global-theme/component-chooser_2.png)

Click **Apply** to confirm your choice.

## Switching to dark mode at night

**Switch to Dark Mode at Night** uses one global theme during the day and another at night. It's off by default. Choose the **Light** and **Dark** themes, which are **Silver Light - Bottom Panel** and **Silver Dark - Bottom Panel** by default, and **Configure Day/Night Cycle…** sets the times.

**Wait until idleness before switching** waits until the computer has been idle for a set time, so the theme doesn't change while you're working.

## Saving your own theme

**Save Current Theme…** saves your current appearance and theme settings as a new global theme. Give it a name, and add a preview image or take a screenshot.

## Installing and removing themes

**Get New…** installs new global themes from third-party providers, which needs an Internet connection. Click **Install** on a theme, and it's available as soon as you close the dialog. See [Getting new add-ons](../dialogs/get-new-stuff.md) for the window's filters, sorting, updates and uninstalling.

![Getting new global themes](images/global-theme/get-new-stuff.png)

To remove a theme, hover over its thumbnail and click the trash button, then confirm with **Delete Permanently**. You can only remove themes you've installed yourself, and not the active one.

If you'd like to create your own theme, see [Themes and plugins](../../developer/plasma/index.md).
