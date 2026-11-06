---
title: Getting started with screen readers
description: What you need to use SonicDE applications with a screen reader.
source_url: https://userbase.kde.org/Accessibility/Getting_Started
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-desktop-interface (kcms/access, kaccess/kaccess.cpp); the source page covers building Qt 4.8 by hand, which was replaced with the current steps; read from code, not clicked through"
---

# Getting started with screen readers

## Prerequisites

You need:

- A working AT-SPI 2 service, which is the D-Bus service that assistive technologies use to talk to applications
- A screen reader, such as Orca

Qt includes the bridge to AT-SPI, so there's nothing extra to build.

## Running applications

To turn on the screen reader for your whole session, see [Starting the Orca screen reader](desktop.md#starting-the-orca-screen-reader).

To try a single application without that, set this variable and then start the application from the same terminal:

```sh
export QT_ACCESSIBILITY=1
```

## Reporting problems

Please report problems you find in the issue tracker of the application concerned.

## More information

- [Accessibility on the desktop](desktop.md)
- [Application overview](applications.md)
