---
title: Opening network files in any application
description: How applications that only understand local files can open files from network locations.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-io-fuse d87a234 (README.md, DESIGN.md, TODO, data/, src/main.cpp), sonic-frameworks-io e3f55ceb (src/core/desktopexecparser.cpp); written from the code, and a local folder mounted through kio-fuse from a staged build on a private session bus. Opening a real network file in an application hasn't been tried"
---

# Opening network files in any application

SonicDE's own applications can work directly with [network locations](../protocols/index.md), such as `sftp://` or `smb://` addresses. Many other applications only understand files on your computer.

When you open a network file in one of those, the KIO FUSE service makes it appear as an ordinary local file, and gives the application that path. This happens by itself: you don't need to set anything up or mount anything. Without the service, the file would be downloaded to a temporary copy instead.

## Saving changes

When an application saves the file, the change is written to a local cache first, and uploaded when the application closes the file. This means that:

- An error during that upload can't be reported to the application, so check important files after saving them.
- Keep the network connection up until the application has closed the file.

## Using it by hand

You can mount a network location yourself, for example to use it from a terminal:

```bash
dbus-send --session --print-reply --type=method_call \
    --dest=org.kde.KIOFuse /org/kde/KIOFuse \
    org.kde.KIOFuse.VFS.mountUrl string:sftp://user@example.org/home/user
```

The reply gives the local path, which follows the pattern `<mount point>/<protocol>/<user>@<server>/<path>`. The mount point is in your runtime directory, usually `/run/user/<your user ID>/`: it's called `kio-fuse` on a system using systemd, and `kio-fuse-` followed by random characters on others.

There's no way to unmount a single location. Unmounting the mount point ends the service for every application using it, so close them first:

```bash
fusermount3 -u /run/user/$(id -u)/kio-fuse
```

The service needs FUSE 3 on your system.
