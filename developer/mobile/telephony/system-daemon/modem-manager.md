---
title: ModemManager
description: ModemManager and the fake modem backend for testing against it.
source_url: https://develop.kde.org/docs/packaging/plasma-mobile/telephony/system-daemon-userland-dbus-ipc-level/modem-manager/
source_authors: [Alexey Andreyev, Carl Schwan, Mikhail Zolotukhin]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-modemmanager: src/fakemodem and autotests. Its 11 tests were run and pass on a private bus. The fake modem backend itself wasn't used beyond those."
---

# ModemManager

[ModemManager](https://modemmanager.org/) is a freedesktop.org project, licensed under GPL-2.0-or-later and LGPL-2.1-or-later, started in 2008 to support USB dongles on desktops. It integrates with the higher-level [NetworkManager](https://gitlab.freedesktop.org/NetworkManager/NetworkManager) daemon.

SonicDE reaches it through ModemManagerQt, in the `sonic-frameworks-modemmanager` repository.

## Testing without a modem

ModemManager has no manual testing tool like [oFono's Phonesim](ofono.md). Phonesim support could probably be added to ModemManager or ModemManagerQt if needed.

For unit tests, ModemManagerQt provides a fake modem backend in `src/fakemodem`, used by the tests in its `autotests` folder.
