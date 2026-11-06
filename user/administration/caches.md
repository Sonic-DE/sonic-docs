---
title: Caches
description: The caches SonicDE creates, and how they affect login time.
source_url: https://userbase.kde.org/KDE_System_Administration/Caches
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "the stage's kbuildsycoca6, sonic-frameworks-services (sycoca), sonic-frameworks-icon-themes; KDE 4 paths, Flatpak notes and a patch to the removed startkde script were left out; read from code, not clicked through"
---

# Caches

Several caches are created when they're first needed. In setups with no persistent home directory, or where NFS is used, creating the caches can considerably increase the time from logging in until the desktop session is usable.

This page gives an overview of the caches and tips on improving caching in your setup.

## General

Caches are placed in `$HOME/.cache`.

All caches are memory-mapped at startup to improve performance when their contents are accessed. Each user needs their own cache, with write access to it.

### KSycoca

KSycoca is the system configuration cache. It holds a binary representation of the various `.desktop` files that describe installed software and services and which default applications to use. See [XDG filesystem hierarchy](xdg-filesystem-hierarchy.md) for more about desktop files. Because there can be many desktop files in many locations, rebuilding the cache can take a while, especially if your `/usr` directory is on a network file system.

To check how long this takes on your system, trigger a full rebuild in a terminal:

```sh
kbuildsycoca6 --noincremental
```

KSycoca should rebuild as needed when your configuration changes, but you can always rebuild it by hand by running `kbuildsycoca6`.

### Icon cache

The icon cache stores decompressed images of the icons in use, so that they can be shared between applications. Although it doesn't noticeably affect the time the desktop takes to become available after login, it can make for a poor experience when, after a long login, someone opens something with lots of icons, like the application launcher. That again results in a large number of system calls to find the best size of an icon in various locations.

### Desktop shell cache

This is the largest of the caches when you use the desktop. It mostly contains decompressed images (like your wallpaper). Those images are transferred while they're still compressed, so keeping this cache on NFS might even harm performance.

### Other caches

Various applications use other caches, but those are mostly small and don't noticeably affect the performance of the desktop session as a whole.

## Using prepared caches to improve performance

To avoid rebuilding KSycoca and the icon cache for each new user, you can create an up-to-date cache for your system and copy it into the user's cache folder before their session starts. This significantly reduces the number of system calls made when a desktop session starts. In one deployment where starting a session took about 80 seconds, this cut the start time to about 50 seconds.

The downside is that you have to update this cache by hand after installing or updating software.
