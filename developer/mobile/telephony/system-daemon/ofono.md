---
title: Testing with oFono Phonesim
description: Using oFono's fake modem to test telephony features.
source_url: https://develop.kde.org/docs/packaging/plasma-mobile/telephony/system-daemon-userland-dbus-ipc-level/ofono/
source_authors: [Alexey Andreyev, Carl Schwan, Fushan Wen, Jonah Brüchert, Luis Büchi, Mikhail Zolotukhin]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "Only that the phonesim, Qt 6 fork and oFono2MM repositories exist. None of these steps were run: they use third-party tools that aren't part of SonicDE, and they assume systemd."
---

# Testing with oFono Phonesim

SonicDE uses ModemManager for telephony, but the competing oFono stack has a very useful debugging tool. This page describes how to use it to develop telephony features.

## Phonesim

Phonesim adds a fake phone modem that can be controlled through a Qt user interface. It can be used to test various parts of a phone's user interface: making and receiving calls, signal strength, sending SMS and so on.

The current stable release of Phonesim is based on Qt 5. On most distributions, you need to compile it yourself from the [source code](https://git.kernel.org/pub/scm/network/ofono/phonesim.git). For a version based on Qt 6, there is [this fork](https://invent.kde.org/jbbgameich/ofono-phonesim/-/tree/qt6). In some cases, you may be able to install `ofono-phonesim` from your distribution's repository.

To set it up for development:

1. Install oFono.

2. Edit `/etc/ofono/phonesim.conf` and uncomment everything, so that it looks like this:

   ```ini
   [phonesim]
   Address=127.0.0.1
   Port=12345
   ```

3. Start the oFono daemon:

   ```bash
   systemctl start ofono
   ```

4. Start Phonesim:

   ```bash
   ./src/phonesim -gui -p 12345 ../src/default.xml
   ```

   At first nothing happens. This is fine, as the user interface only appears once the virtual modem is activated.

5. From the [oFono source directory](https://git.kernel.org/pub/scm/network/ofono/ofono.git), run `./test/enable-modem` to bring the modem up. The control window should appear.

6. Run `./test/online-modem` to activate the modem.

7. Install [oFono2MM](https://github.com/droidian/oFono2MM), then reload the available services and restart ModemManager:

   ```bash
   systemctl daemon-reload
   systemctl restart ModemManager
   ```

   The running ModemManager is now the fake implementation, based on oFono. To restore the normal ModemManager later, delete `/usr/lib/systemd/system/ModemManager.service.d/10-ofono2mm.conf`.

Applications that use ModemManager should now see the fake modem. For example, the upstream [Spacebar](../applications.md#spacebar) application can receive SMS. Start `spacebar-daemon` before `spacebar`.
