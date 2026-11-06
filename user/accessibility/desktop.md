---
title: Accessibility on the desktop
description: Turn on the screen reader and visual aids, and use the desktop from the keyboard.
source_url: https://userbase.kde.org/Accessibility/Plasma
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-desktop-interface (kaccess/kaccess.cpp, kcms/access), sonic-win (src/plugins/invert/invert.cpp, src/plugins/zoom/zoom.cpp, src/virtualdesktops.cpp, src/useractions.cpp), sonic-workspace (shell/shellcorona.cpp), sonic-screenlocker (ksldapp.cpp); read from code, not clicked through"
---

# Accessibility on the desktop

The desktop has a number of features for improved accessibility. To use them, you must first turn them on. The zoom function is an exception: it's on by default, but can be turned off.

To turn an accessibility function on or off, go to System Settings and find the page for it in the [Accessibility](../settings/accessibility.md) module or the [Desktop Effects](../settings/desktop-effects.md) module.

## Turning on accessibility

### Starting the Orca screen reader

When Orca is properly installed, there are two ways to start it.

#### Shortcut

After logging in, press Meta+Alt+S to turn the screen reader on or off.

#### Autostart

To start Orca after logging in:

1. Open [System Settings](../settings/index.md).
2. Go to the [Accessibility](../settings/accessibility.md) module.
3. Go to the **Screen Reader** page.
4. Check **Enable Screen Reader**.
5. Log out and start your desktop session again.

### Turning on visual aids

Desktop effects include several accessibility features, including full-screen zoom, color inversion and help with finding the mouse pointer.

You'll find the settings for these in the [Desktop Effects](../settings/desktop-effects.md) module.

#### Full-screen magnification

Meta++ and Meta+- zoom in and out.

The scale factor and mouse pointer tracking can be adjusted in the effect's settings. For a fixed-size zoom window, use the Magnifier effect rather than the Zoom effect.

#### Inverting colors

- Meta+Ctrl+I inverts colors for the entire screen.
- Meta+Ctrl+U inverts colors for the current window.

## Keyboard navigation

### Opening the application launcher

- Alt+F1 or Meta opens the application launcher.
- Alt+Space opens [KRunner](../desktop/krunner.md). You can just type to search for applications, documents and more. Move through the list with the up and down arrow keys, and activate an entry with Return.

### Reaching the panels

Meta+Alt+P moves between the panels. Navigate the panel with the arrow keys, and activate an entry with Space or Return.

### Window management

- Alt+Tab switches between windows.
- Alt+F4 closes the current window.

### Virtual desktops

- Ctrl+F*number* switches to a virtual desktop. For example, Ctrl+F2 goes to the second virtual desktop.
- Meta+D shows the desktop.

### Lock screen

The lock screen is accessible.

- Ctrl+Alt+L or Meta+L locks the screen.
- Use Tab to move around the lock screen when it's active. There is one text field for the password. Type your password and press Enter to unlock.
- There are additional buttons for shutting down and restarting.
- The username can be navigated with the left and right arrow keys to switch between users and start new sessions.
