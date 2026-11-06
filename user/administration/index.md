---
title: Administration
description: Information for system administrators deploying or managing SonicDE.
source_url: https://userbase.kde.org/KDE_System_Administration
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "the stage's binaries and sonic-docs' developer/administration section; tools and pages that aren't shipped were left out; read from code, not clicked through"
---

# Administration

This section gives system administrators who are rolling out or managing SonicDE in their organization the information they need.

## File system

- [Configuration files](configuration-files.md): Configuration files are text-based, with groups of key-value pairs. This page explains their syntax, including localization, shell variables, complete or partial lock-down, editing tools and other advanced features.
- [Filesystem hierarchy](filesystem-hierarchy.md): How SonicDE uses the file system, where it looks for files and where it stores them.
- [XDG filesystem hierarchy](xdg-filesystem-hierarchy.md): The directories SonicDE uses, as defined by the XDG specifications from freedesktop.org.

## Desktop sessions

- [Environment variables](environment-variables.md): The environment variables that influence SonicDE and how its applications behave.
- [Session environment variables](session-environment-variables.md): How to set environment variables for your whole session.
- [Desktop startup sequence](startup.md): The desktop's visible components and background services, how they start, and how to change them.
- [Desktop scripting](../../developer/plasma/scripting/index.md): Manage the desktop shell's desktops, panels and widgets with scripts written in JavaScript.

## User and group profiles

- [Introduction to Kiosk](../../developer/administration/kiosk/introduction.md): Restrict what a SonicDE environment can do, based on user and group credentials.
- [Kiosk keys](../../developer/administration/kiosk/keys.md): Known global and application-specific keys for action, resource and URL restrictions.

## Unlocking a user session

If a user's session is locked out, perhaps because of a problem with the keyboard layout or an input device, switch to a console or log in with SSH and run:

```sh
loginctl unlock-sessions
```

## Caches

[Caches](caches.md): Several caches are created when they're first needed.
