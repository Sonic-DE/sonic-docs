---
title: Connection Preferences
description: Set FTP options for your network connections.
source_url: https://invent.kde.org/network/kio-extras/-/blob/master/doc/kcontrol6/netpref/index.docbook
source_authors: [Lauri Watts]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-frameworks-io-extras 368b21968 (kcms/netpref); read from code, not clicked through"
---

# Connection Preferences

You can configure FTP options here.

- **Enable passive mode (PASV):** Passive FTP is often needed behind a firewall. Many firewalls only allow connections started from the inside. Passive FTP is controlled by the client, which makes it usable through firewalls.
- **Mark partially uploaded files:** Partially uploaded files get a `.part` extension added to the end of their name. It's removed once the upload is complete.
