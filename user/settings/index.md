---
title: System Settings
description: Configure your desktop from one place.
source_url: https://invent.kde.org/plasma/systemsettings/-/blob/master/doc/index.docbook
source_authors: [Richard A. Johnson]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-system-settings 2bfb209b (app/main.cpp, app/SettingsBase.cpp, app/SidebarMode.cpp, app/ModuleView.cpp, app/MenuProxyModel.cpp, app/kcmmetadatahelpers.h, categories), sonic-frameworks-settings-utils src/kcmshell/main.cpp, and the module metadata in the SonicDE repos; read from code, not clicked through"
---

# System Settings

System Settings gives you a central, convenient way to configure your desktop. It's made up of multiple modules, which it organizes into categories in one window. You can also [run each module on its own](#running-individual-modules).

## Starting System Settings

You can start System Settings in three ways:

1. Select it from the application launcher.
2. Press Alt+F2 or Alt+Space to bring up KRunner, type `systemsettings`, and press Enter.
3. Type `systemsettings &` at any command prompt.

All three do the same thing. To quit, press Ctrl+Q or close the window.

## The window

The sidebar lists the categories, with a search field at the top. Selecting a category shows its modules, and selecting a module shows its options in the main area. Some categories contain subcategories, and **Back** returns from one. [Quick Settings](quick-settings.md) is the page that appears when System Settings starts.

To find a setting, type keywords into the search field. Only the matching modules stay in the list.

The menu button next to the search field has these items:

- **Highlight Changed Settings** marks the settings you've changed from their defaults.
- **Show Inapplicable Pages** also lists modules that don't apply to your system, which are normally hidden.
- **Report a Bug in the Current Page…** and the usual help items.

## Module buttons

Each module has some or all of these buttons:

- **Help:** Opens help for the current module.
- **Defaults:** Restores the module's default values. You must click **Apply** to save them.
- **Reset:** Returns the module to its previous settings.
- **Apply:** Saves all changes and makes them take effect.

If you switch to another module with unsaved changes, you're asked whether to apply or discard them.

## Categories and modules

The modules you see depend on what's installed and on your hardware.

### Input & Output

- **Mouse & Touchpad:** [Mouse](mouse.md), [Touchpad](touchpad.md), [Screen Edges](screen-edges.md)
- **Keyboard:** [Keyboard](keyboard.md), [Shortcuts](shortcuts.md), [On-Screen Keyboard](on-screen-keyboard.md)
- **Touchscreen:** [Touchscreen Gestures](touchscreen-gestures.md)
- **Display & Monitor:** [Display Configuration](display-configuration.md), [Compositor](compositor.md), [Gamma](monitor-gamma.md), [Night Light](night-light.md)
- [Accessibility](accessibility.md), [Drawing Tablet](drawing-tablet.md), [Game Controller](game-controller.md), [Sound](sound.md)

### Connected Devices

- **Disks & Cameras:** [Device Actions](device-actions.md), [Device Auto-Mount](device-automount.md)
- [Bluetooth](bluetooth.md), [Printers](printers.md), [Thunderbolt](thunderbolt.md)

### Networking

- **Wi-Fi & Internet:** [Wi-Fi & Networking](wifi-networking.md) (with [VPN connections](vpn.md)), [Connection Preferences](connection-preferences.md), [Proxy](proxy.md), [Firewall](firewall.md)
- [Online Accounts](online-accounts.md)

### Appearance & Style

- **Colors & Themes:** [Global Theme](global-theme.md), [Colors](colors.md), [Transparency](transparency.md), [Application Style](application-style.md), [Desktop Style](desktop-style.md), [Window Decorations](window-decorations.md), [Icons](icons.md), [Pointers](pointers.md), [System Sounds](system-sounds.md), [Splash Screen](splash-screen.md). The Silver, Breeze and Oxygen styles have their own settings, opened from Application Style and Window Decorations: [Silver Settings](silver-settings.md), [Breeze settings](breeze-settings.md) and [Oxygen settings](oxygen-settings.md).
- **Text & Fonts:** [Fonts](fonts.md), [Font Management](font-management.md)
- [Animations](animations.md), [Wallpaper](wallpaper.md)

### Apps & Windows

- **Default Applications:** [Default Applications](default-applications.md), [File Associations](file-associations.md)
- **Window Management:** [Window Behavior](window-behavior.md), [Task Switcher](task-switcher.md), [Desktop Effects](desktop-effects.md), [Effect settings](effect-settings.md), [Virtual Desktops](virtual-desktops.md), [Window Rules](window-rules.md), [KWin Scripts](kwin-scripts.md)
- [Activities](activities.md), [Notifications](notifications.md)

### Workspace

- **Search:** [File Search](file-search.md), [Search](search.md), [Web Search Keywords](web-shortcuts.md)
- [General Behavior](general-behavior.md), [Trash](trash.md)

### Security & Privacy

[Login Screen](login-screen.md), [Recent Files](recent-files.md), [Screen Locking](screen-locking.md)

### Language & Time

[Date & Time](date-time.md), [Day-Night Cycle](night-light.md#day-night-cycle), [Region & Language](region-language.md), [Spell Check](spell-check.md)

### System

- **Session:** [Desktop Session](session.md), [Locations](locations.md), [Background Services](background-services.md)
- About this System, [Autostart](autostart.md), [Power Management](power-management.md), [Users](users.md)

## Running individual modules

You can run a module without opening the whole window using `kcmshell6`. Type `kcmshell6 --list` to see the available modules, and `kcmshell6` with a module's name to open it, for example `kcmshell6 kcm_kscreen`.

Some modules only open this way, because they aren't listed in the System Settings window. One is [Plasma Renderer](plasma-renderer.md) (`kcmshell6 kcm_qtquicksettings`).

To open a module in the System Settings window instead, use `systemsettings` with its name, for example `systemsettings kcm_kscreen`.

You can also start KRunner and type keywords, which lists matching modules.
