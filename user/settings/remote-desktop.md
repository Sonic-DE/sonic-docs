---
title: Remote Desktop
description: Let other computers connect to your desktop with apps that support RDP.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-rdp-server 8fa334a (src/kcm/ui/, src/kcm/kcmkrdpserver.cpp, krdpserversettings.kcfg, server/SessionController.cpp, README.md), xdg-desktop-portal-sonicde (src/desktopportal.cpp, src/remotedesktop.cpp); written from the code, and the module opened from a staged build on a private X server; no RDP client has connected to it"
---

# Remote Desktop

This module lets you reach your desktop from another computer, using apps that support the RDP remote desktop protocol. Other people connect with an RDP client, using one of the addresses the module lists. **Copy Address to Clipboard** copies one for you.

Remote Desktop controls your screen through the desktop portal, which on X11 supports the keyboard and pointer, but not touch input.

## Turning it on

Use **Enable RDP server** to start and stop the server. You need at least one user account before anyone can log in.

The switch and autostart use systemd. Without it, the module shows **Systemd not found. krdpserver will require manual activation.**, and you have to start `krdpserver` yourself.

Your system also has to support H.264 video encoding. If it doesn't, the module tells you that Remote Desktop can't be enabled. Ask your distribution about the packages for this.

## Usernames

These are the accounts that can connect. They're separate from your computer's accounts, apart from your own system account, which logs in with your system password when it's turned on.

Click **Add New…** to add a user with a **Username** and **Password**. Each user has buttons to modify and remove it. Passwords are kept in your password manager, normally [KDE Wallet](../applications/kde-wallet.md), and the module reports any error it has reaching it.

## Server settings

- **Autostart on login:** Starts the server when you log in. This is off by default.
- **Listening Port:** The port the server listens on, 3389 by default. The server listens on all network interfaces.
- **Video quality:** From **Responsiveness** to **Quality**. With software encoding, this may make little difference.
- **Security Certificates:** **Generate automatically** creates the certificates for you, and is on by default. Turn it off to use your own with **Certificate path** and **Certificate key path**.

After you change settings while the server is running, the module asks you to **Restart Server**. This may disconnect active connections.

> **Warning:** Anyone with one of these accounts who can reach the port can use your desktop, so choose strong passwords and take care with your [firewall](firewall.md) settings.
