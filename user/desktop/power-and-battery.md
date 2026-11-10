---
title: Power & Battery
description: Check your battery, switch power profiles and stop the computer sleeping, from the system tray.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-power-management f835ef7d3 (applets/batterymonitor: main.qml, main.xml, BatteryItem.qml, InhibitionItem.qml, PowerProfileItem.qml); written from the code, not clicked through"
---

# Power & Battery

The Power & Battery widget sits in the [System Tray](system-tray.md). On a computer without a battery it's called Power Management. Click its icon to open it.

## Batteries

Each battery is listed with its charge and whether it's **Charging**, **Discharging**, **Fully Charged** or **Not Charging**. Batteries in other devices, such as a wireless mouse, are listed too. Where the system can tell, you also see:

- **Remaining Time:** How long the battery lasts at the current rate, or **Time To Full:** while it charges.
- **Battery Health:** How much of its original capacity the battery still holds. When this is low, a message suggests replacing the battery.

If you've set a charge limit in [Power Management](../settings/power-management.md#charge-limit), the widget reminds you how far the battery charges.

## Power Profile

The **Power Profile** slider moves between **Power Save**, **Balanced** and **Performance**. The widget also tells you when an application has asked for a particular profile, and when Performance isn't available, for example because the computer is running too hot.

Power profiles need the `power-profiles-daemon` service. If it isn't installed, the widget says so.

## Sleep and Screen Locking after Inactivity

Normally your computer locks the screen and goes to sleep after a time without use, as set in [Power Management](../settings/power-management.md) and [Screen Locking](../settings/screen-locking.md).

- **Manually Block Sleep and Screen Locking** stops both until you turn the switch off again, for example while you watch a film. This uses more energy.
- Applications such as video players can block sleep and screen locking too. They're listed here with their reason. **Unblock** stops an application from blocking them, and **Allow** lets it block them again.

If your laptop is set not to act when you close the lid while an external monitor is connected, the widget mentions that here too.

## Using the icon

- Middle-click the icon to block sleep and screen locking, or to allow them again.
- Scroll over the icon to change the power profile.

Right-click the icon for:

- **Show Energy Information…**, which opens the Energy Information page of [Info Center](../applications/info-center.md).
- **Show Battery Percentage on Icon When Not Fully Charged**, which is off by default.
- **Configure Power Management…**, which opens [Power Management](../settings/power-management.md).
