---
title: Menu favorites
description: Customize the application menu favorites for SonicDE deployments.
source_url: https://develop.kde.org/docs/administration/menu/
source_authors: [Blagovest Petrov, Carl Schwan, Harald Sitter, Kristen McWilliam, Nicolas Fella, Thiago Sueto, Yvan Masson, shenleban tongying]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "kastatsfavoritesmodel.cpp in sonic-workspace/applets/kicker, the model behind the application launchers. Read from code; not run."
---

# Menu favorites

The application menus can be customized by distributions or companies deploying SonicDE on their workstations. One common customization is a default favorites list that includes some branded software, such as a Linux distribution's extensions or a hardware manufacturer's software.

The favorites can have applications added before or after the defaults. If the default favorites don't suit you, you can ignore them and use only the applications you added.

This applies to all the application menus, for new users.

Add a new file, `/etc/xdg/kicker-extra-favoritesrc`:

```ini
[General]
Prepend=org.kde.dolphin.desktop;org.kde.konsole.desktop
Append=org.kde.plasma-systemmonitor.desktop
IgnoreDefaults=false
```

`Prepend` and `Append` are lists of `.desktop` file names, separated by semicolons, and `IgnoreDefaults=true` leaves out the default favorites.
