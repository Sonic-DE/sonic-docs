---
title: Login manager administration
description: Make Sonic Login Manager your system's login manager, configure it for everyone and find its logs.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-login-manager 4d445487 (README.md, RELEASE-NOTES.md, CMakeLists.txt, services/, src/daemon/SelfProvisioner.cpp, src/daemon/DaemonApp.cpp, src/frontend/settings/CMakeLists.txt, src/frontend/greeter/main.cpp), sonic-frameworks-logging (src/logging.cpp); written from the code, not clicked through"
---

# Login manager administration

Sonic Login Manager is SonicDE's login manager: it starts the X server at boot, shows the [login screen](../settings/login-screen.md) and starts your desktop session. It works with any init system. The program is called `soniclogin`.

## Making it your login manager

Only one login manager can run at a time. Turn off the one you use now, for example SDDM, turn on `soniclogin`, then restart the computer. The commands depend on your init system; run them as root.

**systemd:**

```sh
systemctl disable sddm
systemctl enable soniclogin
```

**OpenRC:**

```sh
rc-update del sddm default
rc-update add soniclogin default
```

**runit:**

The service is installed to `/etc/runit/sv/soniclogin`. Link it into the folder of enabled services, which is `/run/runit/service` on Artix and `/var/service` on Void:

```sh
rm /run/runit/service/sddm
ln -s /etc/runit/sv/soniclogin /run/runit/service/
```

**dinit:**

```sh
dinitctl disable sddm
dinitctl enable soniclogin
```

**s6:**

```sh
s6 repository sync
s6 set disable sddm
s6 set enable soniclogin
s6 set commit
s6 live install
```

`soniclogin` is the bundle that holds the login manager's two s6 services, `soniclogin-srv` and its logger `soniclogin-log`.

**sysvinit:**

```sh
update-rc.d sddm disable
update-rc.d soniclogin defaults
update-rc.d soniclogin enable
```

**FreeBSD and other BSD systems:**

```sh
sysrc sddm_enable="NO"
sysrc soniclogin_enable="YES"
```

Your distribution may install the service in a different place; its package documentation has the details.

The first time it starts, the login manager sets itself up: it creates its own `soniclogin` system account, whose home folder is `/var/lib/soniclogin`, and the folders it needs. If you used Plasma Login Manager before, its settings in `/etc/plasmalogin.conf` and `/etc/plasmalogin.conf.d` are copied over, as long as Sonic Login Manager has no settings of its own yet.

## Sessions

The login screen itself always runs on X11. It can still start Wayland desktops, such as other desktop environments you've installed, as long as their session files are in `/usr/share/wayland-sessions/`. X11 sessions come from `/usr/share/xsessions/`.

## Configuration files

The [Login Screen](../settings/login-screen.md) module in System Settings writes its settings to `/etc/soniclogin.conf`. Files in `/etc/soniclogin.conf.d/` are read too.

Distributions and administrators can set login screen defaults, such as the wallpaper, the clock or the session that's preselected, in `/usr/lib/soniclogin/defaults.conf`, and add more defaults as files in `/usr/lib/soniclogin/soniclogin.conf.d/`. Settings in `/etc/soniclogin.conf` take priority over it. On managed systems, the settings module can be turned off with [Kiosk](../../developer/administration/kiosk/index.md).

## Logs

With systemd, the login manager's service logs to the journal (`journalctl -u soniclogin`). With other init systems its log is in `/var/log/sonic`: `/var/log/sonic/soniclogin.log` with OpenRC or dinit, where OpenRC also writes `/var/log/sonic-login-manager.err`, and `/var/log/sonic/soniclogin/current` with runit or s6. The helper that starts sessions logs to `/var/log/sonic/soniclogin-helper.log`. See [Logs](logs.md#the-login-manager) for the details.

The login screen keeps its own log, `soniclogin-greeter.log`, in `.local/state/sonic` inside the `soniclogin` account's home folder, so normally `/var/lib/soniclogin/.local/state/sonic/soniclogin-greeter.log`. A new one is started each time the login screen starts.

## After upgrading

Version 6.8.2 changed how the login screen, its settings module and the login manager talk to each other. After upgrading to it from an older version, restart the login manager, or the computer.
