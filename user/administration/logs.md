---
title: Logs
description: Where SonicDE programs write their logs, how logs are rotated, and where to look for the shell, the login manager and the screen locker.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-logging (README.md, src/logging.h, src/logging.cpp), sonic-login-manager (src/*/CMakeLists.txt, src/daemon/SelfProvisioner.cpp, services/), sonic-screenlocker (greeter/main.cpp, greeter/worker/main.cpp, CMakeLists.txt), sonic-desktop-interface (sonic_logging_autoinstall.cpp), sonic-silver (kstyle/breezehelper.cpp, kdecoration/breezedecoration.cpp); written from the code, not clicked through"
---

# Logs

When something goes wrong, the logs are the first place to look. SonicDE programs all log the same way, through SonicDE's own logging system, and it works without systemd as well as with it.

## Where logs go

Each program has its own log file, named after the program:

- Programs you run, including the desktop itself, write to `~/.local/state/sonic/<program>.log`, or `$XDG_STATE_HOME/sonic/<program>.log` if you've set that variable. Only you can read these files.
- Programs that run as root write to `/var/log/sonic/<program>.log`. Your distribution may have chosen another folder.

On systems with the systemd journal, every message also goes to the journal. Each entry is tagged with the program's name, so you can show one program's messages with, for example:

```sh
journalctl -t sonicshell
```

When a service manager collects a program's output, the lines go there instead of a log file of the program's own. This applies to systemd, OpenRC's `supervise-daemon`, runit, s6 and dinit, and to the X session's `~/.xsession-errors`. Redirecting a program's output yourself, to a file or a pipe, doesn't count: the program still writes its own log file.

When you start a program from a terminal, its messages are shown there too.

Each line starts with the time and a two-letter level: `DD` for debug, `II` for information, `WW` for warnings and `EE` for errors. After that comes the part of the program the message is from, in square brackets.

## Size and rotation

When a log file grows past 2 MiB, it's renamed to `<program>.log.last` and a new one is started, so a log never fills your disk. Only one old file is kept. Some programs, such as the login manager's parts, start a fresh log every time they start, and keep the previous run's log as `.last`.

Debug and information messages from Qt itself and other very chatty sources are left out. Warnings and errors are always kept.

## Turning on debug messages

Most SonicDE debug messages are off. To turn them on for one part of the desktop, set `QT_LOGGING_RULES` before starting the program, using the component name, which starts with `org.sonicde.`:

```sh
QT_LOGGING_RULES="org.sonicde.<component>.debug=true" <program>
```

## Logs of particular components

### The desktop

The desktop shell, `sonicshell`, writes to `~/.local/state/sonic/sonicshell.log`. Its panels, widgets and desktop write there too, because they run inside it. The window manager, SonicWin, writes to `~/.local/state/sonic/sonic-win.log`.

This is where they write when you log in with Sonic Login Manager, which sends your session's output to `~/.local/share/soniclogin/xorg-session.log` and `/dev/null` rather than to a service manager. Messages from programs that don't use SonicDE's logging system end up in `xorg-session.log`. If you log in another way that sends the session's output to `~/.xsession-errors`, the desktop's messages go to that file instead of their own log files.

### The Silver style

The Silver application style and window decoration don't have a log of their own. Their messages go to the log of the program they're drawing: an application's own log for the style, and SonicWin's log for the window decoration.

### The login manager

The [login manager](login-manager.md) has several parts, and each has its own log:

- The service itself, `soniclogin`:
  - With systemd, in the journal: `journalctl -u soniclogin`.
  - With OpenRC or dinit, in `/var/log/sonic/soniclogin.log`. OpenRC writes the service's errors to `/var/log/sonic-login-manager.err` as well.
  - With runit or s6, in the folder `/var/log/sonic/soniclogin/`, where the current log is called `current`.
- The helper that starts your session, in `/var/log/sonic/soniclogin-helper.log`.
- The login screen, `soniclogin-greeter`, which runs as the login screen's own account. Its log is in that account's home folder, normally `/var/lib/soniclogin/.local/state/sonic/soniclogin-greeter.log`.

The helper and the login screen keep these files with every init system, systemd included. SonicDE's logging only leaves a program's output to the service manager when the service manager started that program itself, and these two are started by the `soniclogin` service. With the journal, their messages also go to the journal. Anything they print outside SonicDE's logging system, such as a crash message, ends up in the service's log.

### The screen locker

The lock screen writes to `~/.local/state/sonic/kscreenlocker_greet.log`. Each way of unlocking, such as your password, a fingerprint or a smart card, is checked by a separate helper with its own log, named after the sign-in method's PAM service: for example `~/.local/state/sonic/kscreenlocker_worker-kde.log` for the password.
