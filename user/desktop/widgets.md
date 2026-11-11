---
title: Widgets
description: A few useful widgets, including Disks & Devices, Weather, Sonic Menu, Terminal Panel, Terminal and the battery widget.
source_url: https://userbase.kde.org/Plasma/Plasmoids
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-workspace (applets/devicenotifier), sonic-workspace-addons (applets/weather, applets/sonicmenu, applets/terminalpanel, applets/terminalapplet), sonic-workspace (components/shellprivate, shell/shellcorona.cpp), sonic-desktop-interface (containments/panel, PanelConfiguration.qml), sonic-interface-libraries (plasmaquick/plasmawindow.cpp, plasma/containment.cpp), sonic-terminal (src/quick/TerminalHost.cpp), the stage's battery applet and module; read from code, not clicked through"
---

# Widgets

Here are some useful widgets. Others are available from a number of sources. If you need help installing them, see [Installing widgets](installing-widgets.md). For the smaller widgets that come with SonicDE, such as Sticky Note, Timer and Media Frame, see [More widgets](addon-widgets.md).

Some widgets have pages of their own: [Notifications](notifications.md), [Media Player](media-player.md), [Camera Indicator](camera-indicator.md), [Global Menu](global-menu.md), [Lock/Logout](lock-logout.md), [Activity Bar](activity-bar.md), [Icon](icon-widget.md), [System Monitor Sensor](system-monitor-widget.md), [Peek at Desktop and Minimize All Windows](desktop-buttons.md), [Trashcan](trashcan.md), [Input Method Panel](input-method-panel.md) and the [Search](search-widget.md) widget.

## System widgets

### Disks & Devices

The [Disks & Devices](device-notifier.md) widget handles pluggable devices such as USB sticks, digital cameras and external USB hard drives. It also comes into play when a medium such as a CD or DVD is loaded into an optical drive.

When you plug in an external device or load a medium, its window pops up. You can also open it by clicking its panel icon.

![The widget, in an older version](images/widget-device-notifier.png)

The window lists all the devices it currently knows about, with the actions available for each. A mounted device has a small icon to the right of it. Clicking this unmounts the device or ejects the medium. Unmounting or ejecting can fail if the device still has files open, for example if a large copy hasn't finished. In most cases you can just wait a while and try again.

### Sonic Menu

**Sonic Menu** is a compact system menu for a panel, like the menu in the corner of a Mac. Click its icon and a short menu drops down. Out of the box it has:

- **About This Computer**, which opens [Info Center](../applications/info-center.md).
- **System Settings...**, **System Monitor...** and **System Log...**, which open those applications.
- **Force Quit...**, which turns the pointer into a cross: click a window to close its application at once. It runs `xkill`, part of the X.Org tools, which your distribution may package separately.
- **Sleep**, **Restart...** and **Shut Down...**.
- **Lock Screen** and **Log Out**.

The sleep, restart, shut down, lock and log out entries go through SonicDE's session management, so they follow your [Session](../settings/session.md) settings, such as asking for confirmation. Any of them your system can't do, for example sleep on a machine that doesn't support it, is left out of the menu.

To change the menu, right-click the widget and choose **Configure Sonic Menu...**. The settings have three pages.

**General**:

- **Icon:** Click the button and choose **Choose…** to pick another icon or an image file, or **Clear Icon** to go back to the standard one. You can also drop an image file (PNG, XPM or SVG) on the button.
- **Show icons in the menu:** Shows each entry's icon next to its name. Off by default.
- **Menu Width:** The width of the menu in pixels. The default is 240.
- **Button Height:** The height of each entry in pixels. The default is 28.

**Edit Menu** shows the menu as a tree on the left. The buttons above it are **Add Item**, **Add Folder** and **Add Separator**, followed by buttons to move the selected entry up or down and to delete it. A folder becomes a submenu. When you select an entry, the right side shows its settings:

- **Name:** The text in the menu.
- An icon button, with **Choose…** and **Clear Icon**.
- **Runs:** What the entry does. **A command** runs the **Command:** you type through the shell. The other choices are session actions: **Lock Screen**, **Log Out**, **Leave… (all options)**, **Switch User**, **Sleep**, **Hibernate**, **Restart** and **Shut Down**.

**Edit JSON** shows the same menu as text in JSON format, for copying a menu to another computer or making many changes at once. Each entry can have a `name`, an `icon`, and either a `command` or an `action` (`lock`, `logout`, `leave`, `switchUser`, `suspend`, `hibernate`, `reboot` or `shutdown`). A folder has a `submenu` with its own list of entries, and a separator is `{"separator": true}`. If you empty the menu completely, the editor goes back to the standard menu.

### Terminal Panel

The **Terminal Panel** puts a full [Terminal](../applications/terminal.md), with its tabs, split views and toolbars, inside a panel. To get one, right-click the desktop, choose **Add Panel** and then **Terminal Panel**. That creates a panel at the top of the screen that hides itself and holds the terminal. It isn't in the Add Widgets list.

- Click the panel's terminal to type in it. When you click somewhere else, the keyboard goes back to your windows and the panel can hide again.
- While the terminal is in a panel, starting Terminal without a command, for example from the application launcher, doesn't open a new window. The panel comes out instead, with a new tab ready for typing. See [With the Terminal Panel widget](../applications/terminal.md#with-the-terminal-panel-widget) for which ways of starting Terminal still open a window.
- If you close the last tab, for example by typing `exit`, the panel closes, with a new terminal ready for next time.
- Your color scheme's transparency and blur apply behind the terminal text, while the tabs and toolbars keep the panel's look.
- The panel holds only the terminal: it offers no **Add Widgets**, widgets can't be dragged onto it, and it can't be cloned.
- You can have one Terminal Panel or one [Terminal](#terminal) widget, not both and not two of either. While one exists, neither is offered under Add Panel or Add Widgets.

Right-click the tab bar or a toolbar for a menu with the panel's settings and **Configure Terminal…**, which opens Terminal's own settings. The widget's settings, under **Configure Terminal Panel...** in the widget's context menu, are:

- **Minimum width:** The narrowest the terminal gets, in pixels, from 100 to 10000. The default is 480.
- **Profile:** The name of the Terminal profile to start with. Leave it empty to use your default profile.

### Terminal

The **Terminal** widget is the same terminal as the Terminal Panel, in a popup from a button in your panel. Add it from **Add Widgets**.

- Click the button to open the terminal and type in it. Click the button again, or somewhere else, to close it.
- Drag the popup's edges to resize it. It keeps that size the next time it opens.
- While the widget is in a panel, starting Terminal without a command opens the popup with a new tab ready for typing, as with the Terminal Panel.
- The popup stays open while Terminal's own menus and dialogs, such as editing a profile, are open, and has the keyboard again when you close them.
- If you close the last tab, for example by typing `exit`, the popup closes, with a new terminal ready for next time.
- Your color scheme's transparency and blur apply behind the terminal text.
- As with the Terminal Panel, only one Terminal Panel or Terminal widget can exist, and cloning a panel doesn't copy the widget.

Right-click the tab bar or a toolbar for **Configure Terminal…**, which opens Terminal's own settings. Right-click the widget's button and choose **Configure Terminal...** for the widget's settings:

- **General:** **Profile:**, the name of the Terminal profile to start with. Leave it empty to use your default profile.
- **Keyboard Shortcuts:** A shortcut that opens and closes the popup from anywhere. There is none until you set one; clear it to turn it off again.

## The world outside

### Weather

Weather widgets are especially popular if you live in a country with very changeable weather.

The Weather widget gets its information from a choice of sources, such as BBC Weather from the UK Met Office, NOAA's National Weather Service, Environment Canada and Deutscher Wetterdienst. If it can locate a weather station near you, it gives you a range of details about the current weather.

![The Weather widget, in an older version](images/widget-weather.png)

It can also go in the panel, where it shows a small display with the current outside temperature.

Until you choose a place, the widget says **Set up Weather Report…**. Click it to open its settings. The settings have these pages:

- **Weather Station:** Type a place into **Enter location** and choose a weather station from the results. Each result shows the place and the weather service it comes from, and the chosen ones appear as **Location:** and **Provider:**. **Update every:** sets how often the widget fetches new data, in minutes. The default is 30 minutes.
- **Appearance:** Only shown when the widget is in a panel. **Show temperature:** puts the current temperature **Over the widget icon**, **Beside the widget icon** (not on panels too narrow for it), or **Do not show**. **Show in tooltip:** chooses what the tooltip lists: **Temperature**, **Wind**, **Pressure** and **Humidity**. All but **Pressure** are on by default.
- **Units:** The units for **Temperature:**, **Pressure:**, **Wind speed:** and **Visibility:**.

The widget's window has up to three tabs: **Forecast** for the next days, **Details** for the current conditions such as dewpoint, pressure, visibility, humidity and wind gusts, and **Notices** when the weather service has issued warnings or watches for your area.

## Power

### Battery

A battery icon sits in your panel. It shows the remaining charge, on the icon or when you hover over it. Click the battery to get the summary display. Its configure button takes you to the [Power Management](../settings/power-management.md) module.

These older screenshots show how it has looked:

![The summary display](images/widget-power-summary.png)

![The configuration screen](images/widget-power-config.png)

![Editing profiles](images/widget-power-profiles.png)

![Power-saving capabilities](images/widget-power-capabilities.png)
