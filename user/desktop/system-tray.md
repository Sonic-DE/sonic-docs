---
title: System Tray
description: The widget that displays system information, notifications and background services.
source_url: https://userbase.kde.org/Plasma/SystemTray
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-workspace (applets/systemtray/qml/ConfigGeneral.qml); read from code, not clicked through"
---

# System Tray

![The System Tray](images/system-tray.png)

The System Tray widget displays system information, notifications and services.

## Features

- Displays system information
- Holds the [Disks & Devices](device-notifier.md) and [Notifications](notifications.md) widgets
- Lets you interact with applications that run in the background
- Lets you interact with devices connected to your computer
- Shows information about an application's status when you hover over its icon

## The System Tray widget

The System Tray is a widget normally found at the right of the standard panel. It typically holds the [Notifications](notifications.md) widget, [Disks & Devices](device-notifier.md), the [Clipboard](../applications/clipboard.md), [Audio Volume](../settings/sound.md#the-widget), [Power & Battery](power-and-battery.md), [Brightness & Color](brightness-and-color.md), [Networks](../settings/wifi-networking.md), [Display Configuration](../settings/display-configuration.md#the-display-configuration-widget), and external equipment such as [Bluetooth](../settings/bluetooth.md#in-the-system-tray) devices and [printers](../settings/printers.md#the-printers-widget). Other applications may also use it.

When you have more than one keyboard layout, the **Keyboard Layout** entry shows the current one, as a country code or a flag. With only one layout it stays hidden. See [The Keyboard Layout widget](../settings/keyboard.md#the-keyboard-layout-widget).

The [Trashcan](trashcan.md) can also be shown in the tray, under System Services.

To interact with an application in the System Tray, left-click its icon. To open its settings, right-click it. Some icons may be hidden, either because the service isn't active or because it's been set to hide. You can always bring up a hidden icon by clicking the arrow in the tray.

## Settings

Since the System Tray is a widget, you can place it in another panel or on the desktop. To open its settings, right-click somewhere in the System Tray outside the service icons, for example on the arrow.

![The System Tray settings](images/system-tray-general.png)

![The entries in the System Tray settings](images/system-tray-entries.png)

The top of the **General** page sets how the icons look in the panel:

- **Panel icon size:** **Small** keeps the icons small. **Scale with Panel height** (in a vertical panel, **Scale with Panel width**) makes them grow with the panel.
- **Spacing:** The space between the icons: **Small**, **Normal** or **Large**.
- **Direction:** Which way the icons line up from the arrow that expands the tray: **Right-to-left** or **Left-to-right** in a horizontal panel, **Bottom-to-top** or **Top-to-bottom** in a vertical one.

Below that, the **Entries** list shows all the services that can show up in the System Tray, grouped into Application Status, Communications, System Services, Hardware Control and Miscellaneous. Check **Always show all** at the top of the list to show every entry in the panel, with nothing hidden behind the arrow. Otherwise, choose for each entry when it should appear:

- **Show when relevant:** You only see the icon when the service is active.
- **Always show:** The icon is shown even when the service isn't active.
- **Show only in popup:** The item only appears in the expanded popup.
- **Never show (disabled):** The icon is always hidden.

Entries that are widgets, such as the Clipboard or Disks & Devices, also have a field for a global keyboard shortcut that opens them, and a button that opens their own settings.

Some entries warn you before you hide them:

- For an application's icon, the tray suggests looking for a setting in the application itself first, since some applications don't expect their tray icon to be turned off and may then behave unexpectedly. Click **I understand the risks** to close the warning.
- Hiding the Clipboard means copied data is lost when the application you copied from closes. Only do this if you've added a separate Clipboard widget elsewhere, or use another clipboard manager.
- Hiding Notifications means applications' notifications are no longer shown, unless you've added a separate Notifications widget elsewhere or use another notification manager.
