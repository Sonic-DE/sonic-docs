---
title: Connection Preferences
description: Mark files that are still being uploaded, and set FTP options for your network connections.
source_url: https://invent.kde.org/network/kio-extras/-/blob/master/doc/kcontrol6/netpref/index.docbook
source_authors: [Lauri Watts]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-frameworks-io-extras (kcms/netpref/netpref.cpp); read from code, not clicked through"
---

# Connection Preferences

This module has two groups of options for copying files over the network. It's under **Wi-Fi & Internet** in System Settings.

## Global Options

- **Mark partially uploaded files:** While a file is being uploaded over SMB, SFTP or another network protocol, it gets a `.part` extension added to the end of its name. The extension is removed once the upload is complete, so you can tell at a glance which files on the server aren't finished yet.

## FTP Options

- **Enable passive mode (PASV):** Passive FTP is often needed behind a firewall. Many firewalls only allow connections started from the inside. Passive FTP is controlled by the client, which makes it usable through firewalls.
- **Mark partially uploaded files:** The same as the global option, for uploads over FTP: partially uploaded files get a `.part` extension, which is removed once the upload is complete.
