---
title: XDG filesystem hierarchy
description: The standard directories SonicDE uses for data, configuration and caches.
source_url: https://userbase.kde.org/KDE_System_Administration/XDG_Filesystem_Hierarchy
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "QStandardPaths use throughout the repos, sonic-frameworks-io (gui/kio thumbnail code); read from code, not clicked through"
---

# XDG filesystem hierarchy

## freedesktop.org and standard directories

Many free and open source projects focused on desktop technology collaborate on shared specifications and software through the [freedesktop.org](https://www.freedesktop.org) project.

One of these shared specifications is the [base directory specification](https://specifications.freedesktop.org/basedir-spec/latest/), which defines a set of locations in the file system for portable desktop technology.

SonicDE follows the base directory specification and the [environment variables](environment-variables.md) it prescribes. A summary follows, and you can read the full specification on the freedesktop.org website.

## Application data

Data that applications store for a particular user goes in the `XDG_DATA_HOME` directory. If the `XDG_DATA_HOME` environment variable isn't set, it defaults to `$HOME/.local/share` for local storage, and system-wide files are in `/usr/local/share` and `/usr/share`.

Items stored in `XDG_DATA_HOME` may include files the user has put in the trash, file type definitions and associations, and application `.desktop` files.

To define the search path for system-wide directories, set the `XDG_DATA_DIRS` environment variable to a list of paths.

## Configuration

Configuration information goes in the `XDG_CONFIG_HOME` directory. If the `XDG_CONFIG_HOME` environment variable isn't set, it defaults to `$HOME/.config` for local storage and `/etc/xdg` for system-wide files.

Items stored in `XDG_CONFIG_HOME` may include application configuration files and the application menu structure.

To define the search path for system-wide directories, set the `XDG_CONFIG_DIRS` environment variable to a list of paths.

## Cache files

Temporary data caches can be stored in the `XDG_CACHE_HOME` location, which defaults to `$HOME/.cache`. There is no system-wide cache location, as caches are always specific to a user. See [Caches](caches.md).

## Thumbnails

Thumbnails representing the contents of files, used in icons and other representations of files, are stored in `$XDG_CACHE_HOME/thumbnails`. The [thumbnail specification](https://specifications.freedesktop.org/thumbnail-spec/latest/) defines the structure and content of this folder.
