---
title: Disks & Devices
description: Handle USB sticks, cameras, external drives and optical media from the system tray.
source_url: https://userbase.kde.org/Plasma/DeviceNotifier
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-workspace (applets/devicenotifier/qml/); read from code, not clicked through"
---

# Disks & Devices

![The widget, in an older version](images/widget-device-notifier.png)

The Disks & Devices widget, once called the Device Notifier, handles pluggable devices such as USB sticks, digital cameras and external USB hard drives. It also comes into play when a medium such as a CD or DVD is loaded into an optical drive.

When you plug in an external device or load a new medium, its window pops up. You can also open it by clicking its panel icon.

Right-click the icon for its context menu:

- **Remove All** safely removes all removable devices at once. It's shown while at least one device can be removed. When more than one removable device is in use, the same button also appears at the top of the window.
- **Removable Devices**, **Non Removable Devices** and **All Devices** choose which devices the window lists.
- **Show popup when new device is plugged in** turns the automatic pop-up on or off.
- **Configure Removable Devices…** opens the [Device Auto-Mount](../settings/device-automount.md) module.

The window lists all the devices it currently knows about. For a device that's in use, the line under its name shows how much space is free, for example "12 GB free of 32 GB". Moving the pointer over a device highlights the actions available for it.

![A device's actions, in an older version](images/device-notifier-actions.png)

Clicking anywhere in the box around the device name, but not on the eject or unmount icon if there is one, expands the entry to show its possible actions. The actions depend on the device, and you can configure them in the [Device Actions](../settings/device-actions.md) module. Select one with the mouse or keyboard to start it.

A small icon to the right of each entry shows whether that device is currently accessible, or *mounted*. It's only safe to physically disconnect a device when it isn't mounted. Clicking the icon unmounts the device or ejects the medium if it's mounted, and mounts it if it isn't. Unmounting or ejecting can fail if the device still has files open, for example if a large copy hasn't finished. In most cases you can just wait a while and try again.
