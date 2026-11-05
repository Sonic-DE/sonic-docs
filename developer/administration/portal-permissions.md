---
title: Portal pre-authorization
description: Let applications use XDG portals without an interactive dialog.
source_url: https://develop.kde.org/docs/administration/portal-permissions/
source_authors: [Blagovest Petrov, Carl Schwan, Harald Sitter, Kristen McWilliam, Nicolas Fella, Thiago Sueto, Yvan Masson, shenleban tongying]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "remotedesktop.cpp in xdg-desktop-portal-sonicde: the kde-authorized permission lookup. Read from code; flatpak isn't installed on the test host, so the commands were not run."
---

# Portal pre-authorization

Interactive permission prompts are useful, but sometimes access to resources has to be authorized without one.

For this, `xdg-desktop-portal-sonicde` has a permission table named `kde-authorized` in the standard xdg-desktop-portal permission store. An entry in this table bypasses the interactive prompt. To authorize a well-known application, pass its `app_id` to the set command:

```bash
flatpak permission-set kde-authorized remote-desktop org.example.remotedesktop yes
```

To authorize a host application without an `app_id`, use an empty one:

```bash
flatpak permission-set kde-authorized remote-desktop "" yes
```

The `app_id` usually comes from Flatpak or Snap metadata. For host applications, it comes from the Registry or the systemd unit name:

- Applications can set their own `app_id` in the [XDG portal Registry](https://flatpak.github.io/xdg-desktop-portal/docs/doc-org.freedesktop.host.portal.Registry.html).
- Applications started by the desktop are set up correctly.
- Manually created units should follow the [systemd desktop environment conventions](https://systemd.io/DESKTOP_ENVIRONMENTS/), naming the unit `app-org.example.appname.service`.
- If the name can't be determined, the empty `app_id` is used.

## Supported types

- `remote-desktop`

## Caveats

- Host applications can impersonate any `app_id`.
- The empty `app_id` may match too broadly. It's better to have the application provide one, by following [those conventions](https://systemd.io/DESKTOP_ENVIRONMENTS/) or by registering directly with the [Registry](https://flatpak.github.io/xdg-desktop-portal/docs/doc-org.freedesktop.host.portal.Registry.html).
