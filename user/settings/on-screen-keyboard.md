---
title: On-Screen Keyboard
description: Choose the on-screen keyboard's languages and how its keys behave.
source_url: https://invent.kde.org/plasma/kwin-x11/-/blob/master/doc/kwinvirtualkeyboard-x11/index.docbook
source_authors: [Yuri Chornoivan]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-keyboard 69f30ae4 (kcm, README.md); read from code, not clicked through"
---

# On-Screen Keyboard

This module configures Sonic Keyboard, the [virtual keyboard](https://en.wikipedia.org/wiki/Virtual_keyboard) that you type on with a mouse or touchscreen. It's under **Input & Output > Keyboard** in System Settings.

## Languages

The list chooses the languages the keyboard offers. Use the field above it to filter languages. If none are selected, the system's default keyboard layout is used.

## Key press feedback

- **Sound:** Plays a sound when you press a key.
- **Vibration:** Vibrates when you press a key.

## General

- **Keyboard navigation:** Lets you move around the keyboard with a hardware keyboard's keys.
- **Auto-capitalization:** Capitalizes letters automatically.

## Alternate characters

- **Show popup when holding a key:** Holding a key shows a popup of its alternate characters, such as accented letters.
- **Hold delay:** How long to hold the key before the popup appears, from 100 to 1500 milliseconds.
