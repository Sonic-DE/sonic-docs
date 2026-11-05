---
title: Session daemons
description: The daemons that handle calls and messages for the user, which SonicDE doesn't ship.
source_url: https://develop.kde.org/docs/packaging/plasma-mobile/telephony/session-daemon-userland-dbus-ipc-level/
source_authors: [Alessio Mattiazzi, Alexey Andreyev, Carl Schwan, Mikhail Zolotukhin, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "The folders of the current plasma-dialer source (commit a7a1369), read but not built, and SonicDE's repository list. sonic-frameworks-modemmanager is SonicDE's. The other projects are described from the source page. Its discussion of how Telepathy's development is going is left out, and a dated plan is reduced to the choice made."
---

# Session daemons

ModemManager [gives unified access](system-daemon/index.md) to different modems over the system D-Bus. Session daemons build on that. Their tasks include:

- Handling calls and messages
- Providing call and message history
- Mapping phone numbers to contacts
- Power management
- Notifications
- Interacting with other parts of the user's environment
- Filtering spam

**SonicDE doesn't ship any of the daemons on this page.** The only one of these components it includes is ModemManagerQt, in `sonic-frameworks-modemmanager`.

## Related projects

### eg25-manager

[eg25-manager](https://gitlab.com/mobian1/eg25-manager) is a daemon that handles low-power modes of the Quectel EG25 through ModemManager. It's used for the PinePhone.

### SMS, MMS and voicemail

- [SMS/MMS daemon](https://gitlab.com/kop316/mmsd)
- [Visual voicemail daemon](https://gitlab.com/kop316/vvmd)

Both are developed for Phosh but don't depend on a particular environment, and could be used directly through their session-level D-Bus APIs.

### ModemManagerQt

ModemManagerQt is a Qt wrapper for the ModemManager D-Bus API, in SonicDE's `sonic-frameworks-modemmanager` repository.

### kde-telephony-meta

[kde-telephony-meta](https://invent.kde.org/plasma-mobile/plasma-dialer/-/tree/master/kde-telephony-meta) holds data the upstream telephony components share, including their D-Bus XML interface descriptions and Qt meta types for complex D-Bus types.

## Daemons

Both of these are part of the upstream [plasma-dialer](https://invent.kde.org/plasma-mobile/plasma-dialer) project.

### Modem daemon

[modem-daemon](https://invent.kde.org/plasma-mobile/plasma-dialer/-/tree/master/modem-daemon) tracks modem events in the background, so that it can:

- Give client applications and daemons access to calls over the session D-Bus
- Save the history

It's written in Qt and works with the system D-Bus, providing a session D-Bus API for applications. It uses ModemManagerQt but offers a higher-level API, so that changing the underlying manager should be transparent to applications.

### KDE telephony daemon

[kde-telephony-daemon](https://invent.kde.org/plasma-mobile/plasma-dialer/-/tree/master/kde-telephony-daemon) tracks modem events in the background, so that it can:

- Enable audio channels when needed
- Show notifications
- Launch the dialer automatically
- Share telephony services over the session D-Bus

It depends on the modem daemon, and includes `contactphonenumbermapper`, a library for working with contacts and phone numbers.

## Telepathy

[Telepathy](https://github.com/TelepathyIM/wiki/wiki) is a freedesktop.org framework for building instant messaging clients that interoperate over D-Bus. It could use oFono or ModemManager to implement calling and messaging clients, and could in theory cover both daemons above. The upstream dialer is based on ModemManager without it.

## What the daemons don't do

Session daemons interact with the rest of the user's environment and give applications a unified API. Providing developer libraries for particular environments and languages is outside their scope. Their API is exported on the session bus, so that a library such as the [QML plugin](qml-plugin.md) can use it.
