---
title: Background Services
description: See and control the services of the desktop's background daemon.
source_url: https://invent.kde.org/plasma/plasma-desktop/-/blob/master/doc/kcontrol/kded/index.docbook
source_authors: [Burkhard Lück]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-desktop-interface fad996458a (kcms/kded); read from code, not clicked through"
---

# Background Services

This module gives you an overview of the plugins of the background services manager, `kded6`. It's under **System > Session** in System Settings.

There are two types of service:

- **Load-on-Demand Services:** Started when they're needed. They're only listed for convenience, because you can't change them.
- **Startup Services:** Can be loaded when the desktop starts. The checkbox next to each one sets whether it's automatically loaded.

> [!WARNING]
> Be careful when turning off services you don't know. Some are vital for the desktop, so don't turn them off unless you know what you're doing.

To change a service's status, select it in the list and use **Start Service** or **Stop Service**. Some services turn themselves off again when started by hand, if they aren't useful in the current environment.

The list can be filtered to **All Services**, **Running** or **Not Running**.

If you're turning something off here to work around an issue, please also report a bug about it.
