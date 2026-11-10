---
title: Device Auto-Mount
description: Configure automatic mounting of disks and volumes.
source_url: https://invent.kde.org/plasma/plasma-desktop/-/blob/master/doc/kcontrol/solid-device-automounter/index.docbook
source_authors: [Trever Fischer]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-desktop-interface fad996458a (solid-device-automounter/kcm); read from code, not clicked through"
---

# Device Auto-Mount

This module configures automatic mounting of disks and volumes. With it turned on, you don't need to use the Disks & Devices widget or the file manager's places panel to get to a device you've just plugged in.

The list contains the storage devices known to the system, grouped into **Attached Devices** and **Disconnected Devices**, under a top entry for all of them. That entry is called **All Devices** while **Automatically mount removable media that have never been mounted before** is checked, and **All Known Devices** while it isn't.

- **On Login:** The device is automatically mounted when you log in.
- **On Attach:** The device is automatically mounted when it's plugged in.

**Automatically mount removable media that have never been mounted before:** When this isn't checked, only remembered devices are automatically mounted. A device is “remembered” if it has ever been mounted before. Plugging in a USB media player just to charge it isn't enough, for example: if its files aren't accessed, it won't be mounted automatically next time.

**Forget Device** makes the system forget that the selected devices ever existed. This is only useful when the option above is unchecked. A forgotten device won't be automatically mounted until it's been mounted again.
