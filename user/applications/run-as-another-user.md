---
title: Running programs as another user
description: Run a program as another user with kdesu.
source_url: https://invent.kde.org/plasma/kde-cli-tools/-/blob/master/doc/kdesu/index.docbook
source_authors: [Geert Jansen]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-terminal-tools c3e6ab9c (kdesu) and sonic-frameworks-root-shell c1d60e31 (src/suprocess.cpp, src/stubprocess.cpp, src/kdesu_stub.c, src/kdesud); read from code, not clicked through"
---

# Running programs as another user

`kdesu` is a graphical front end for the UNIX `su` command. It lets you run a program as a different user by supplying that user's password. It's an unprivileged program that uses the system's `su`, or `sudo` or `doas` where the system is set up to use them.

It can also remember passwords, so you only need to enter the password once for each command. See [Password keeping](#password-keeping) for more on this, including a security analysis.

It's meant to be started from the command line or from `.desktop` files. Although it asks for the password with a graphical dialog, it's more glue between the command line and the desktop than a pure graphical program.

`kdesu` isn't in your `PATH`. It's installed in the frameworks' `libexec` folder, for example `/usr/lib64/libexec/kf6/kdesu`, so use that full path to start it.

## Using kdesu

The syntax is:

```bash
kdesu [-c command] [-d] [-f file] [-i icon] [-n] [-p priority] [-r] [-s] [-t] [-u user]
      [--noignorebutton] [--attach winid] [--embed winid] [command]
```

- `command`: The command to run, as separate arguments.
- `-c command`: The command to run, as one argument. For example, to start a new file manager as root: `/usr/lib64/libexec/kf6/kdesu -c ecco`
- `-d`: Doesn't show the command to be run in the dialog.
- `-f file`: Allows efficient use in `.desktop` files. `kdesu` examines the file. If the current user can write to it, the command runs as the current user. If not, it runs as the target user, by default root. A path starting with `/` is taken as an absolute file name. Otherwise, it's taken as the name of a configuration file.
- `-i icon`: The icon to use in the password dialog. You can give just the name, without any extension.
- `-n`: Doesn't keep the password. This disables the keep password checkbox in the password dialog.
- `-p priority`: The priority, from 0, the lowest, to 100, the highest. The default is 50.
- `-r`: Uses realtime scheduling.
- `-s`: Stops the `kdesud` daemon, which forgets all passwords. See [Password keeping](#password-keeping).
- `-t`: Enables terminal output, which disables password keeping. This is largely for debugging. To run a console application, use the standard `su` instead.
- `-u user`: The target user. The most common use is to run a command as the superuser, but you can give any user name, with the right password.
- `--noignorebutton`: Doesn't show the ignore button.
- `--attach winid`: Makes the dialog transient for the given window.
- `--embed winid`: Embeds the dialog into a window.

## Internals

### X authentication

The program you run under the root user ID generally has no authority to access your X display. `kdesu` gets around this by adding an authentication cookie for your display to a temporary `.Xauthority` file, which is removed after the command exits.

If you don't use X cookies, you're on your own. `kdesu` detects this and doesn't add a cookie, but you have to make sure root can access your display.

### Interface to su

Some `su` implementations don't read the password from `stdin`, so `kdesu` creates a pty/tty pair and runs `su` with its standard file descriptors connected to the tty.

To run the command you selected rather than an interactive shell, `kdesu` uses the `-c` argument with `su`. `su` passes it to the target user's shell, which runs the program. For example: `su root -c the_program`.

Instead of running your command directly, `kdesu` runs a little stub program called `kdesu_stub`. The stub, running as the target user, asks `kdesu` for some information over the pty/tty channel and then runs your program. That information is the X display, an X authentication cookie if available, the `PATH` and the command to run. A stub is used because the X cookie is private information, and so can't be passed on the command line.

### Password checking

`kdesu` checks the password you entered, and gives an error message if it isn't correct. It does this with a trial run of `su` and the stub program.

### Password keeping

For your comfort, `kdesu` has a “keep password” feature. If you're interested in security, you should read this section.

Allowing `kdesu` to remember passwords opens up a small security hole in your system. It doesn't let anybody but your user ID use the passwords, but done without caution, this would lower root's security level to that of a normal user. A hacker who broke into your account would get root access. `kdesu` tries to prevent this.

It uses a daemon called `kdesud`, which listens for commands on a UNIX socket in your runtime folder. The socket's mode is 0600, so only your user ID can connect to it. If password keeping is enabled, `kdesu` runs commands through this daemon. It writes the command and root's password to the socket, and the daemon runs the command using `su`, as described above. The command and the password are then kept for a time, by default two hours. If another request for the same command comes within that time, the client doesn't have to supply the password.

To stop hackers who broke into your account from stealing passwords from the daemon, for example by attaching a debugger, the daemon marks itself as not dumpable. The daemon also sets the `DISPLAY` environment variable to the value it had when it was started, so the only thing a hacker can do is run an application on your display.

One weak spot in this scheme is that the programs you run probably aren't written with security in mind, unlike setuid root programs. They might have buffer overruns or other problems that a hacker could exploit.

Using password keeping is a tradeoff between security and comfort. Think it over and decide for yourself whether you want to use it.
