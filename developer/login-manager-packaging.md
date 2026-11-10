---
title: Packaging the login manager
description: Build options, init system service files and PAM configuration for Sonic Login Manager.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-login-manager 4d445487 (CMakeLists.txt, services/CMakeLists.txt, data/CMakeLists.txt, data/pam/, src/frontend/settings/CMakeLists.txt, src/daemon/SelfProvisioner.cpp), sonicde-builder config/sonicde/packages/sonicde/sonic-login-manager.yaml; written from the code, not built with every option"
---

# Packaging the login manager

Sonic Login Manager (`sonic-login-manager`) is a display manager forked from Plasma Login Manager, which is based on SDDM. This page is for packagers. For users and administrators, see [Login Screen](../user/settings/login-screen.md) and [Login manager administration](../user/administration/login-manager.md).

## Dependencies

It's built against Qt 6 and the SonicDE Frameworks and workspace libraries, including SonicDE's own PlasmaQuick and screen libraries; it needs no KDE Plasma packages and no Qt 5. Besides those, the build needs:

- PAM
- `xau` (found with pkg-config) and zlib
- a native Xorg server binary (see `X_SERVER_EXECUTABLE` below)
- optionally `utmps`, for session tracking on systems without systemd

systemd isn't required. When its pkg-config file is found, the systemd unit is installed; otherwise the build looks for the other init systems.

## Build options

| Option | Default | What it does |
| --- | --- | --- |
| `INSTALL_PAM_CONFIGURATION` | `ON` | Installs the PAM files `soniclogin`, `soniclogin-greeter` and `soniclogin-autologin`. |
| `PAM_OS_CONFIGURATION` | `auto` | Which set of PAM files to install. `auto` picks one from `/etc/os-release`: `fedora`, `suse`, `kde-linux`, `arch`, `gentoo`, `artix`, `debian` or `freebsd`. On any other system, configuring stops with an error; set `-DINSTALL_PAM_CONFIGURATION=OFF` and ship your own PAM files. |
| `PAM_CONFIG_DIR` | `<sysconfdir>/pam.d` | Where the PAM files are installed. |
| `MANUAL_INITS` | `OFF` | Turns off init system detection, so no service files are installed unless `SPLIT_BUILD` is on. |
| `SPLIT_BUILD` | `OFF` | Installs the service files for every init system, each in its own install component, so a distribution can split them into separate packages. |
| `X_SERVER_EXECUTABLE` | detected | The Xorg binary to start. It must be a native ELF executable, not a wrapper script, because Xorg is started with ambient capabilities that an interpreter would use up. If none is found, configuring stops with an error. |

The Gentoo PAM greeter file uses `pam_systemd.so` when systemd is found and `pam_elogind.so` otherwise.

## Init system service files

Without `MANUAL_INITS` or `SPLIT_BUILD`, the service file for each init system found on the build machine is installed:

| Init system | Detected by | Installed files |
| --- | --- | --- |
| systemd | `systemd` pkg-config file | `soniclogin.service` in the systemd system unit directory |
| OpenRC | `openrc` or `rc` program | `<sysconfdir>/init.d/soniclogin`, `<sysconfdir>/logrotate.d/soniclogin` |
| runit | `runsvdir` program | `<sysconfdir>/runit/sv/soniclogin/run`, `<sysconfdir>/runit/sv/soniclogin/log/run` |
| dinit | `dinit` program | `<sysconfdir>/dinit.d/soniclogin`, `<sysconfdir>/dinit.d/soniclogin-logdir`, `<sysconfdir>/logrotate.d/soniclogin` |
| s6 | `s6-svscan` program | `<sysconfdir>/s6/sv/soniclogin-srv` and `<sysconfdir>/s6/sv/soniclogin-log` |
| sysvinit | `/etc/inittab` and `telinit`, and no OpenRC | `<sysconfdir>/init.d/soniclogin` |
| BSD rc.d | the target system | `etc/rc.d/soniclogin` under the install prefix, and an `Xwrapper.config` |

OpenRC and sysvinit both install `<sysconfdir>/init.d/soniclogin`. If both are detected, configuring stops with an error: choose one, or use `SPLIT_BUILD`. Systems where sysvinit only starts OpenRC are treated as OpenRC.

With `SPLIT_BUILD=ON`, each init system's files belong to an install component named after it (`systemd`, `openrc`, `runit`, `dinit`, `s6`, `sysvinit`, `bsd`). `cpack -G TGZ` then produces one archive per init system.

## What the login manager sets up itself

You don't need to create a user, group or folders in the package. On its first start, the daemon creates the `soniclogin` system group and user, with `/var/lib/soniclogin` as its home folder, and its state, D-Bus and runtime folders. It also copies an existing `/etc/plasmalogin.conf` and `/etc/plasmalogin.conf.d` when there are no Sonic Login Manager settings yet.

The OpenRC and dinit service files run `soniclogin --prepare-log-directory`, which creates or repairs `/var/log/sonic`, before the daemon starts. With runit and s6, the log service's run script does this before it starts the logger.

## Configuration paths

| Path | Purpose |
| --- | --- |
| `/etc/soniclogin.conf` | Settings written by the Login Screen module and administrators. |
| `/etc/soniclogin.conf.d/` | Extra settings files. |
| `<prefix>/lib/soniclogin/defaults.conf` | Distribution defaults for the login screen and its settings module, overridden by the files in `/etc`. The daemon doesn't read it. |
| `<prefix>/lib/soniclogin/soniclogin.conf.d/` | Extra distribution defaults, read by the daemon, the login screen and its settings module. |

Both follow the CMake option `SYSTEM_CONFIG_DIR` (default `<prefix>/lib/soniclogin/soniclogin.conf.d`); `defaults.conf` sits in its parent folder. They are `lib` even where libraries go to `lib64`, because they hold configuration, not libraries.

## Release notes for packagers

From 6.8.2, the login screen, its settings module and the sign-in helper talk to each other through Sonic IPC. Tell users to restart the login manager after upgrading from an older version.
