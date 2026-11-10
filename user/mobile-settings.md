---
title: Mobile settings
description: The System Settings modules of the SonicDE Mobile session, for the shell, navigation, time, networks, the modem and energy.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-mobile-interface (kcms/mobileshell, kcms/navigation, kcms/time, kcms/info, quicksettings/settingsapp, bin/startplasmamobile.in, components/shellsettingsplugin/kwinsettings.cpp), sonic-network-manager (kcms/kcm_wifi_mobile, kcm_wired_mobile, kcm_cellularnetwork, kcm_hotspot), sonic-power-management (kcm_mobile), sonic-system-settings (app/kcmmetadatahelpers.h), sonic-terminal-tools (plasma-open-settings); written from the code, not clicked through"
---

# Mobile settings

In the [SonicDE Mobile](mobile.md) session, System Settings shows a set of modules made for touch screens. They only appear there, not on the desktop. To open System Settings, tap the **Settings** quick setting in the action drawer.

## Shell

**General:**

- **Shell Vibrations:** Opens a page where **Shell Vibrations** turns vibration feedback in the shell on or off, and **Vibration Duration** chooses **Long**, **Medium** or **Short**. The on-screen keyboard's vibrations are set separately, in the keyboard settings.
- **Animations:** When off, animations are cut down as much as possible.
- **Auto Hide Panels:** Hides the status bar and the navigation panel, so applications always have the whole screen.

**Status Bar:**

- **Date in status bar:** Shows the date next to the clock.
- **Battery Percentage:** Shows the battery charge as a number.
- **Status Bar Size:** **Tiny**, **Small**, **Normal**, **Large** or **Very Large**. This takes effect after a restart.

**Action Drawer:** the panel you pull down from the top of the screen.

- **Quick Settings:** Opens a page that lists your quick settings in the order they appear. Drag them by their handles into a new order, and use **Hide** to take one out; hidden ones move to **Disabled Quick Settings**, where **Show** brings them back. **Quick Settings Columns** sets the most columns the drawer uses when the screen is in landscape.
- **Top Left Drawer Mode** and **Top Right Drawer Mode:** How the drawer opens when you pull it down from the top left or the top right: **Pinned Mode** or **Expanded Mode**.

**Lock Screen Shortcuts:** **Left button** and **Right button** put a button on the lock screen for **None**, **Flashlight** or **Camera**.

## Navigation

**Navigation Mode** is **Panel**: a navigation panel with buttons along the bottom of the screen. Gesture navigation isn't available yet. **Always show keyboard toggle** keeps the button that opens and closes the on-screen keyboard on the navigation panel all the time.

## Time and Date

- **Display:** **24-Hour Format** for clocks, and your **Timezone**.
- **Time and Date:** **Automatic Time Synchronization** sets the time from the Internet. Turn it off to set the **System Time** and **System Date** yourself.

These settings change the system clock through the system's `timedate1` service, so they need a service that provides it, such as systemd-timedated.

## Information

**System Information** lists the operating system, your software versions and kernel, and the processors and memory. **Copy** copies it all, for example to paste into a bug report.

## Wi-Fi

- **Wi-Fi** turns wireless networking on and off.
- **Saved Networks** lists networks you've used before; **Available Networks** lists the ones in range. Tap a network to connect.
- **Add Custom Connection** sets up a network by hand: its **SSID**, **Hidden Network**, the **Security type** (such as **WPA/WPA2 Personal** or **WPA3 Personal**) with its **Password**, and the **IP Settings**: **Method** (**Automatic** or **Manual**), **IP Address**, **Gateway**, **Network prefix length** and **DNS**.
- The details page of a connected network shows its transfer rates and connection details, and **Share Wi-Fi via QR Code** shows a code another phone can scan to join.
- **More** opens **Wi-Fi Settings**, with **Notifications for connection changes**.

## Wired Network

**Wired Network Connections** lists your wired connections. **Add New Connection** creates one, with the same **IP Settings** as for Wi-Fi.

## Cellular Network

For devices with a modem.

- **Mobile data** turns mobile data on and off. It explains when it can't: when no SIM is inserted, the modem doesn't support it, or an APN still needs setting up.
- **Data Usage** shows how much data you've used.
- Each SIM has its own page, **SIM** with its number, with:
  - **Roaming:** Allows mobile data on a roaming network.
  - **Modify APNs:** The access point names for your carrier. **Add APN** with **Name**, **APN**, **Username**, **Password** and **Network type**, or **Automatically detect APN**. Each APN can be edited or deleted.
  - **Networks:** **Scan For Networks** and choose a network operator.
  - **SIM Lock:** **Lock SIM** to require a PIN for calls and mobile data, **Change PIN**, or **Disable SIM Lock**.
  - **Modem Details:** Information about the modem, and **Force Modem Restart** under **Modem Control**.

## Hotspot

**Hotspot** shares your internet connection with other devices as a Wi-Fi network. **Configure** sets the **Hotspot SSID** (the network's name) and the **Hotspot Password**.

## Energy

- **Devices** lists your batteries with their charge. Tap one for **Battery Information**, such as a **Usage Graph**, **Is Rechargeable**, **Charge State**, **Current Charge**, **Health**, **Vendor**, **Model**, **Serial Number** and **Technology**.
- **Screen:** **Dim screen after**, **Turn off screen after** and **Suspend device after** set how long the device waits, when you're not using it, before each step.
- **Power Profile:** **Power profile** chooses between saving power and performance. It only appears on devices that support power profiles.
