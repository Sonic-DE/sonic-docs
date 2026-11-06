---
title: Screen Locking
description: Set when the screen locks, when a password is needed and how it looks.
source_url: https://invent.kde.org/plasma/plasma-workspace/-/blob/master/doc/kcontrol/screenlocker/index.docbook
source_authors: [Mike McBride]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-screenlocker 0ed103d7 (kcm, settings/kscreensaversettings.cpp); read from code, not clicked through"
---

# Screen Locking

This module sets how much time must pass before the screen locks, how long you can unlock it without a password, and how the lock screen looks.

- **Lock screen automatically:** The period of inactivity before the screen locks, from a list of times or **Custom…**, or **Never**.
- **Lock after waking from sleep:** Locks the screen after the system has been suspended.
- **Delay before password required:** If you press a key or click a mouse button within this time, you can return to your work without a password. Choose **Require password immediately**, a list of times, or **Never require password**. The password is the one you log in with.

Locking the screen manually turns password protection on immediately. The default shortcut, Meta+L, locks the screen. You can change it in [Shortcuts](shortcuts.md).

## Appearance

**Configure Appearance…** changes the background of the lock screen. **Wallpaper type** can be a plain color, a single image, or a slideshow of images from a folder, and you can load new wallpapers from the Internet.
