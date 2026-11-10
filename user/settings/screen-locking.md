---
title: Screen Locking
description: Set when the screen locks, when a password is needed and how it looks.
source_url: https://invent.kde.org/plasma/plasma-workspace/-/blob/master/doc/kcontrol/screenlocker/index.docbook
source_authors: [Mike McBride]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-screenlocker 8de127f5 (kcm, settings/kscreensaversettings.cpp, ksldapp.cpp), sonic-desktop-interface 649680b89c (desktoppackage/contents/lockscreen: LockScreenUi.qml, MainBlock.qml, config.qml, config.xml), sonic-workspace 808d83b2eb (components/loginlockscreen/Footer.qml, lookandfeel/components/WallpaperFader.qml); read from code, not clicked through"
---

# Screen Locking

This module, under **Security & Privacy** in System Settings, sets how much time must pass before the screen locks, how long you can unlock it without a password, and how the lock screen looks.

- **Lock screen automatically:** The period of inactivity before the screen locks, from a list of times or **Custom…**, or **Never**.
- **Lock after waking from sleep:** Locks the screen after the system has been suspended.
- **Delay before password required:** If you press a key or click a mouse button within this time, you can return to your work without a password. Choose **Require password immediately**, a list of times, or **Never require password**. The password is the one you log in with.

- **Keyboard shortcut:** The key that locks the screen straight away. The default is Meta+L. It's the same as **Lock Session** in the [Shortcuts](shortcuts.md) module, so changing it in either place changes both.

Locking the screen manually turns password protection on immediately.

## Appearance

**Configure Appearance…** changes how the lock screen looks:

- **Wallpaper type:** The background of the lock screen. It can be a plain color, a single image, or a slideshow of images from a folder, and you can load new wallpapers from the Internet.
- **Show clock:** **Always** shows the time on the lock screen, **On unlocking prompt** only while the password field is showing, and **Never** hides it.
- **Media controls:** **Show under unlocking prompt** shows the music or video that's playing, with buttons to control it. It's on by default.

## Unlocking

Press a key or move the mouse to show the unlock screen. When the password field appears, the wallpaper is blurred and tinted with your theme's background color, so the text stands out. Text and icons also have a soft glow on dark themes, or a shadow on light ones.

Type your password and press Enter. If your computer has a fingerprint reader or smart card reader set up, you can use that instead. A message tells you when **Caps Lock is on**. After a wrong password, the system makes you wait a moment before trying again. The password field and unlock button are greyed out until then.

The buttons under the password field let you put the computer to **Sleep** or **Hibernate**, or **Switch User**, when your computer supports them.

The bottom of the screen has:

- **Virtual Keyboard**, which opens SonicDE's on-screen keyboard, so you can unlock without a physical keyboard. Your picture and the password field move up so they stay above it.
- **Switch layout**, which shows your current keyboard layout and switches to the next one. It only appears when you have more than one layout.
- The battery level, on battery-powered computers.
