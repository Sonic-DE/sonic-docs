---
title: Themes and plugins
description: How to customize SonicDE with widgets, themes and icons.
source_url: https://develop.kde.org/docs/plasma/
source_authors: [Alessio Mattiazzi, Carl Schwan, Chris Holland, Felipe Kinoshita, Mikhail Zolotukhin, Natalie Clarius, Nate Graham, Thiago Sueto, Tobias Fella, Zren (Chris Holland)]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "the data directories installed by the SonicDE build (share/plasma, share/kwin-x11, share/kwin, share/color-schemes), SonicWin's KWIN_DATADIR and tabbox and effect loaders, sonic-silver, sonic-login-manager's greeter and settings module, KNewStuff's default provider"
---

# Themes and plugins

The SonicDE desktop is very modular, made up of themable widgets that can be added, removed, rearranged and customized. Pre-installed widgets and themes are in `/usr/share/plasma/`, while third-party ones are in the user's home directory, in `~/.local/share/plasma/`. The directory is still called `plasma` for compatibility.

SonicDE's "Get New" dialogs download from the [KDE Store](https://store.kde.org), so that's where the store categories below point.

## Global theme

Formerly called a "Look and Feel", it bundles a [panel layout template](#panel-layout-template), an [icon theme](#icon-theme), a [desktop theme](#desktop-theme) (and its [color scheme](#color-scheme)), a [task switcher](#task-switcher), a [splash screen](#splash-screen), a lock screen theme, or any combination of these.

* System/default: `/usr/share/plasma/look-and-feel/` ([Silver on GitHub](https://github.com/Sonic-DE/sonic-silver/tree/master/look-and-feel))
* User installed: `~/.local/share/plasma/look-and-feel/` ([KDE Store category](https://store.kde.org/browse/cat/121/order/latest/))

## Desktop theme

Also called a Desktop Style, it controls the visual styling of panels, widgets, OSD popups, the lock screen and the logout screen. A desktop theme can include its own color scheme, which overrides the system color scheme for desktop elements.

* System/default: `/usr/share/plasma/desktoptheme/` ([GitHub](https://github.com/Sonic-DE/sonic-interface-libraries/tree/master/src/desktoptheme))
* User installed: `~/.local/share/plasma/desktoptheme/` ([KDE Store category](https://store.kde.org/browse/cat/104/order/latest/))

## Color scheme

A list of colors in plain INI format that define the colors of user interface elements that follow the system color scheme. These are typically Qt applications, GTK applications themed with SonicDE's GTK theme, and desktop elements when the desktop theme respects the system color scheme.

* Usually set in the `colors` file of a desktop theme.
* System/default: `/usr/share/color-schemes/` ([Silver on GitHub](https://github.com/Sonic-DE/sonic-silver/tree/master/colors))
* User installed: `~/.local/share/color-schemes/` ([KDE Store category](https://store.kde.org/browse/cat/112/order/latest/))
* When a color scheme is applied, its values are copied to `~/.config/kdeglobals`, and [sonic-gtk-theme-bridge](https://github.com/Sonic-DE/sonic-gtk-theme-bridge) syncs the colors to the GTK theme in `~/.config/gtk-3.0/colors.css`.

## Icon theme

A collection of icon files in different sizes that follows the [freedesktop specification](https://specifications.freedesktop.org/icon-theme-spec).

* System/default: `/usr/share/icons/` ([Silver on GitHub](https://github.com/Sonic-DE/sonic-silver-icons))
* User installed: `~/.local/share/icons/` ([KDE Store category](https://store.kde.org/browse/cat/132/order/latest/))

## Panel layout template

A JavaScript desktop script that defines a specific panel layout, used when you right-click the desktop and select "Add Panel".

* System/default: `/usr/share/plasma/layout-templates/` ([Silver on GitHub](https://github.com/Sonic-DE/sonic-silver/tree/master/layout-templates))
* User installed: `~/.local/share/plasma/layout-templates/`

## Task switcher

A visual representation of the windows you can switch to with Alt+Tab, written in QML.

* System/default: `/usr/share/kwin-x11/tabbox/`, then `/usr/share/kwin/tabbox/` ([GitHub](https://github.com/Sonic-DE/sonic-workspace-addons/tree/master/kwin/windowswitchers))
* User installed: `~/.local/share/kwin-x11/tabbox/` ([KDE Store category](https://store.kde.org/browse/cat/211/order/latest/))
* Can also be bundled in a global theme.

## Desktop widget

Also known as a plasmoid, it is an interactive and self-contained piece of functionality: essentially a small application embedded in the current desktop layout, on the desktop or in a panel. Widgets are written in QML.

* System/default: `/usr/share/plasma/plasmoids/`
* User installed: `~/.local/share/plasma/plasmoids/` ([KDE Store category](https://store.kde.org/browse/cat/418/order/latest/))

## Wallpaper plugin

A plugin written in QML that draws the desktop wallpaper. You choose and configure it in the wallpaper settings window, with the "Wallpaper Type" combobox.

* System/default: `/usr/share/plasma/wallpapers/`
* User installed: `~/.local/share/plasma/wallpapers/`

## Window decoration

Handles the theme and button style of the window titlebar. A window decoration can be created by editing SVG files (Aurorae) or by writing a C++ plugin with [KDecoration](https://github.com/Sonic-DE/sonic-decoration).

* System/default: `/usr/share/aurorae/themes/` (usually empty)
* User installed: `~/.local/share/aurorae/themes/` ([KDE Store category](https://store.kde.org/browse/cat/114/order/latest/))
* The default [Silver decoration](https://github.com/Sonic-DE/sonic-silver/tree/master/kdecoration) is a C++ plugin.
* Aurorae is a theming engine for window decorations based on SVGs. It can also load QML-based themes.

## SonicWin effect

Also known as a desktop effect, it applies visual changes to any area of the screen. Effects can be purely visual (for example an animation when a window is minimized), or interactive with their own rich user interface (for example the Overview effect).

* System/default: `/usr/share/kwin-x11/effects/` ([GitHub](https://github.com/Sonic-DE/sonic-win/tree/master/src/effects))
* User installed: `~/.local/share/kwin-x11/effects/` ([KDE Store category](https://store.kde.org/browse/cat/209/order/latest/))

## SonicWin script

A script written in JavaScript or QML that manages windows, for example to [arrange them in a grid automatically](https://store.kde.org/p/1281790/).

* System/default: `/usr/share/kwin-x11/scripts/` ([GitHub](https://github.com/Sonic-DE/sonic-win/tree/master/src/plugins))
* User installed: `~/.local/share/kwin-x11/scripts/` ([KDE Store category](https://store.kde.org/browse/cat/210/order/latest/))

## Login screen

The screen you see before you log in, shown by [Sonic Login Manager](https://github.com/Sonic-DE/sonic-login-manager). It is not the lock screen; lock screen themes are part of global themes.

The greeter is built into Sonic Login Manager rather than installed as a separate theme. You configure it in System Settings, under "Login Screen", where "Apply Desktop Settings…" makes it use your current desktop theme and other desktop settings, and "Configure Appearance…" sets the greeter's own appearance.

* Testing: `/usr/lib/soniclogin-greeter --test`

## Splash screen

The animated screen you see after you log in. It is written in QML and can use images like PNGs, SVGs or GIFs.

* System/default: `/usr/share/plasma/look-and-feel/<theme_name>/contents/splash/`
* User installed: `~/.local/share/plasma/look-and-feel/<theme_name>/contents/splash/` ([KDE Store category](https://store.kde.org/browse?cat=488&ord=latest))
