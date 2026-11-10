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

To turn an accessibility function on or off, go to System Settings and find the page for it in the [Accessibility](../settings/accessibility.md) module. A few aids for finding the mouse pointer are in the [Desktop Effects](../settings/desktop-effects.md) module.

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

The window manager has several visual aids, including zoom, color inversion and help with finding the mouse pointer. They need desktop effects to be on.

Zoom and color inversion are set in the [Accessibility](../settings/accessibility.md) module, on its **Zoom & Magnifier** and **Invert** pages. The aids for finding the mouse pointer, such as **Track Mouse** and **Mouse Click Animation**, are in the [Desktop Effects](../settings/desktop-effects.md) module, and their settings are described in [Effect settings](../settings/effect-settings.md).

#### Magnification

On the **Zoom & Magnifier** page, **Zoom:** chooses how the screen is enlarged:

- **Full screen** enlarges the whole screen. This is on by default.
- **Magnify region** enlarges only a box around the mouse pointer, whose **Width:** and **Height:** you can set.
- **Disabled** turns magnification off.

The page also sets the **Zoom factor:**, how the pointer looks and how the enlarged area follows it. See [Accessibility](../settings/accessibility.md) for all its settings. Its **Configure Shortcuts…** button changes the keys below.

- Meta++ (or Meta+=) zooms in, and Meta+- zooms out.
- Meta+0 goes back to normal size with **Full screen**. With **Magnify region**, it turns the magnifier on and off.

Full-screen zoom has more shortcuts:

- Meta+F5 moves the mouse pointer to the part of the screen that has the focus, and Meta+F6 to the center of the enlarged area.
- Four more shortcuts move the enlarged area left, right, up and down without moving the pointer. They have no keys by default; set them with **Configure Shortcuts…**.

#### Inverting colors

Color inversion is off by default. To use it, check **Enable** next to **Invert:** on the **Invert** page of the Accessibility module. Then:

- Meta+Ctrl+I inverts colors for the entire screen.
- Meta+Ctrl+U inverts colors for the current window.

**Configure Shortcuts…** on the same page changes these keys.

## Keyboard navigation

### Opening the application launcher

- Alt+F1 or Meta opens the application launcher.
- Alt+Space opens [KRunner](../desktop/krunner.md). You can just type to search for applications, documents and more. Move through the list with the up and down arrow keys, and activate an entry with Return.

### Reaching the panels

Meta+Alt+P moves between the panels. Navigate the panel with the arrow keys, and activate an entry with Space or Return.

Each panel can also have its own **Focus shortcut:**, set in its Panel Settings. It gives the keyboard to that panel, and pressing it again gives the keyboard back to your window.

- A panel that hides itself appears at once, and stays until you press the shortcut again, press Escape or click somewhere else.
- While one of the panel's menus is open, the panel keeps the keyboard, so the keys go to that menu.
- Escape goes first to the menu or widget that's using it, and only then closes the panel.

See [Using a panel with the keyboard](../desktop/panels.md#using-a-panel-with-the-keyboard).

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
- The **Virtual Keyboard** button at the bottom opens the on-screen keyboard. When more than one keyboard layout is set up, a button next to it, **Switch layout**, changes the layout. See [Unlocking](../settings/screen-locking.md#unlocking).
- The username can be navigated with the left and right arrow keys to switch between users and start new sessions.
