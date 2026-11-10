---
title: Login Screen
description: Use the login screen, set up automatic login and make the login screen match your desktop.
source_url: https://userbase.kde.org/System_Settings/Login_Screen
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-login-manager 4d445487 (src/frontend/kcm/ui/main.qml, Appearance.qml, src/frontend/greeter/qml/, src/frontend/settings/sonicloginsettings.cpp, src/frontend/wallpaper/wallpaperapp.cpp, src/common/ThemeSync.cpp), sonic-workspace 808d83b2eb (components/loginlockscreen/Footer.qml), sonic-breeze-sddm (breeze-sddm-theme); rewritten for Sonic Login Manager, which replaced the module the source page describes; read from code, not clicked through"
---

# Login Screen

Sonic Login Manager shows the login screen when your computer starts and after you log out. This page describes the login screen and its settings module, which is under **Security & Privacy** in System Settings. For installing it and choosing it as your system's login manager, see [Login manager administration](../administration/login-manager.md).

## Using the login screen

The login screen lists the people who can log in. Choose yourself, type your password and press Enter, or click the arrow button next to the password field. If the user needs no password, the button reads **Log In**.

- **Other…** switches to **Type in Username and Password**, where you type both. **List Users** goes back to the list.
- **Desktop Session:** under the password field shows which desktop starts when you log in. Click it to choose another. It only appears when more than one session is installed.
- A message tells you when **Caps Lock is on**, and when **Login Failed**.
- The buttons below the login prompt put the computer to **Sleep** or **Hibernate**, **Restart** it or **Shut Down**. Each only appears if your computer supports it.

The bottom of the screen has:

- **Virtual Keyboard**, which opens SonicDE's on-screen keyboard so you can log in without a physical keyboard. Your picture and the password field move up so they stay above it.
- **Switch layout**, which shows your current keyboard layout and switches to the next one. It only appears when you have more than one layout; see **Apply Desktop Settings…** below.
- The battery level, on battery-powered computers.

By default, the login screen uses the Silver Dark theme. Text and icons have a soft glow on dark themes and a shadow on light ones, so they stay readable over any wallpaper.

## Automatic login

If you don't want to type your username and password when logging in, tick **Automatically log in:**, then choose the user (**as user:**) and the session to start (**with session:**), and click **Apply**. Remember that anyone who can physically reach your computer then has instant access to all your data, so weigh up the risk before using this.

Automatic login can't unlock your KDE Wallet, so it asks for the wallet's password each time you log in. The module explains this and offers **Open KDE Wallet Settings**.

**Log in again immediately after logging off** logs the automatic user straight back in when they log out.

## Defaults

- **Default user:** **Last logged-in user** preselects whoever logged in last. Choose the other option to always preselect the user you pick from the list.
- **Default session:** **Last logged-in session** preselects the session used last time. Choose the other option to always preselect the session you pick.

## Desktop settings

**Apply Desktop Settings…** makes the login screen reflect your own customizations to:

- language and locale settings
- keyboard layouts
- screen arrangement, scale and orientation
- NumLock preference
- fonts and font rendering
- color scheme
- icon theme
- cursor theme and size
- desktop theme

Themes and customizations you installed yourself are copied to the login screen. Themes installed for the whole system are used as they are. Fonts must be installed for the whole system to be used on the login screen. **Reset to Default Settings** undoes all of this.

## Appearance

**Configure Appearance…** changes how the login screen looks:

- **Clock:** **Show clock** shows the time on the login screen.
- **Wallpaper type:** The kind of wallpaper, such as a plain color, a single image or the Picture of the Day, with that wallpaper's settings below. Slideshows aren't offered, because only one picture is copied to the login screen. Until you set a wallpaper here, the login screen shows the Picture of the Day.

## SDDM

SonicDE also provides the Breeze theme for the SDDM login manager, for systems that use SDDM instead of Sonic Login Manager. This module doesn't configure SDDM.
