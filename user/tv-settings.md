---
title: TV settings
description: The settings of the SonicDE TV session, made to be used with a TV remote or game controller.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-tv-interface (settingsapp/qml, kcms/bigscreen-settings, kcms/display, kcms/input, kcms/wallpaper, kcms/audio-device-chooser, kcms/wifi, kcms/bluetooth, kcms/kdeconnect, kcms/webapps, CMakeLists.txt); written from the code, not clicked through"
---

# TV settings

The [SonicDE TV](tv.md) session has its own settings application, which you can use with a TV remote or game controller. Open it with **Settings** in the home overlay. Its pages are listed in a sidebar on the left.

The sidebar also offers the desktop System Settings, which has more settings. Before opening it, it asks **Open desktop settings?** and warns that it doesn't support key navigation, so you may need a mouse.

## System

**Homescreen Appearance:**

- **Colored tiles:** Colors the background of each application tile to match the application's icon.
- **Wallpaper blur:** Blurs the wallpaper behind the home screen.
- **Dark Mode:** Switches the TV session between **Silver Light - TV** and **Silver Dark - TV**. This only changes the TV session; your desktop keeps its own global theme.

**System:**

- **Window decorations:** Gives applications that ask for one a window frame, with minimize, maximize and close buttons.
- **Navigation sounds:** Plays a sound when the selection changes in system applications.
- **Navigation rumble:** Makes the game controller rumble when the selection changes: **Off**, **Weak**, **Medium** or **Strong**.
- **Power inhibition:** Stops the system from going to sleep by itself.
- **Adjust date and time:** Opens a sidebar with the **Timezone** (search with **Search City / Region**), **Set time automatically**, and the **Time** and **Date** when you set them yourself.

**Shortcuts:** keyboard shortcuts for **Open home overlay shortcut**, **Open homescreen shortcut**, **Open settings shortcut** and **Open tasks shortcut**.

## Display

**Display Configuration** chooses the **Selected display** and, for that display, whether it's **Enabled**, its **Screen mode (Resolution & Refresh Rate)** and its **Scale**. After a change, it asks **Keep display configuration?** and goes back to the previous settings after a few seconds unless you confirm.

## Input

How remotes and game controllers move around the TV interface. These settings need the input service: if it isn't running, the page says **Input daemon is not running**.

- **System Navigation:** Lets connected remotes and game controllers move around the TV interface. Applications can always use them directly.
- **TV remote:** Lets you move around with a TV remote connected over HDMI (CEC). It only appears when a remote is connected, and only if SonicDE was built with CEC support.
- **Game Controllers:** While a controller is connected, **Game controllers** lets you move around with it, and **Automatic input suppression** stops that while another application is using a controller. Choose a controller in the list for its own settings: **System navigation** for that controller, and **START button when suppressed**, which still lets the START button through and may conflict with some applications. With no controller, the page says **No controllers connected**.

## Wallpaper

**Open wallpaper selector** chooses the wallpaper.

## Audio

**Audio Devices** lists the **Playback Devices** and **Recording Devices**. For each, **Set as default device** makes it the one sound goes to or comes from, and **Adjust Volume** sets its volume.

## Wi-Fi

Lists the wireless networks in range under **Connections**; **Refresh** looks again. Choose a network to **Connect**, entering its password if it has one, or to **Disconnect**. **Network details** shows its IP address and speed, and **Forget network** removes a saved network.

## Bluetooth

**Enable Bluetooth** turns Bluetooth on and off. **Paired devices** and **Available devices** list the devices; choose one to **Pair**, **Connect** or **Disconnect**. Each paired device has **Trusted** (accept its connections automatically), **Blocked** (reject all connections from it), **Change name** and **Forget device**.

## KDE Connect

Pairs the TV with your phone through KDE Connect. **Devices** lists the phones found, with **Pair** and **Unpair**, and **Accept** or **Reject** for requests from a phone. KDE Connect isn't part of SonicDE, so this page only works when it's installed.

## Web Apps

Turns websites into applications on the home screen. **Add Web App** asks for a **Name**, a **URL** and, if needed, a **User Agent** (leave it empty for the default). **Installed web apps** lists them, each with **Delete**.
