---
title: Introduction to Kiosk
description: How Kiosk locks settings and restricts actions, URLs and settings modules.
source_url: https://develop.kde.org/docs/administration/kiosk/introduction/
source_authors: [Barry O'Donovan, Blagovest Petrov, Carl Schwan, David Edmundson, Harald Sitter, Kai Uwe Broulik, Kristen McWilliam, Marco Martin, Nicolas Fella, Thiago Sueto, Yvan Masson, shenleban tongying]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "kauthorized.cpp and kconfig.cpp in sonic-frameworks-settings, kurlauthorized in sonic-frameworks-io, kactioncollection in sonic-frameworks-xml-gui. Immutable keys, groups and files, the action and control module restrictions and the URL rules run through KConfig, KAuthorized and KUrlAuthorized from a test program against the staged libraries, with private XDG directories. /etc/kde5rc was read from code, not tested, and nothing was checked in a real locked-down session."
---

# Introduction to Kiosk

Kiosk lets administrators create a controlled environment for their users, by customizing and locking almost any part of the desktop. That ranges from the benign, like setting and fixing the wallpaper, through the functional, like disabling logging out, to the security conscious, like disabling access to a command shell.

This is important for business environments, school and university laboratories, Internet cafés, public access terminals and kiosks.

Kiosk is controlled by entries in configuration files. This page explains how those files are laid out, how to edit them to enable Kiosk's features, and what can be customized or locked.

## Configuration file structure and hierarchy

SonicDE applications all use the same API to create, access and change their configuration files, so the files are all stored in predetermined directories and share the same syntax and structure. They are organized into groups of key-value pairs. For example, these are some settings stored in `~/.config/kdeglobals`:

```ini
[KDE]
SingleClick=true
DoubleClickInterval=400
widgetStyle=breeze
```

The `KDE` group here has global settings for the desktop, such as whether a single click activates items, and the applications' widget style. A group starts with its name in square brackets, and ends when the next one starts or at the end of the file. Keys and values can contain spaces, but whitespace just before and after the equals sign and at the end of the line is ignored.

Configuration files can be stored in several directories, and files with the same name can exist in different ones. These locations are checked in a set order, and files of the same name are combined key by key. This is known as *cascading configuration*. If the same key is defined in more than one file, the value from the directory with the highest precedence is used.

[Environment variables](https://specifications.freedesktop.org/basedir-spec) say which directories to search. `$XDG_CONFIG_DIRS` locates configuration files for the whole system, and `$XDG_CONFIG_HOME` is where user-specific ones are stored.

This cascading lets administrators set system-wide defaults, while users' own settings override those defaults. It is also the basis of Kiosk, because entries can be marked as *immutable*: an entry in a user's file in `$XDG_CONFIG_HOME` that is marked immutable at system level isn't read, and so has no effect.

For example, as the administrators of an Internet café, we might want to make sure that the widget style is always Breeze and that customers can't change it, to keep a consistent look across the machines. In a system-level directory, we would edit `$XDG_CONFIG_DIRS/kdeglobals` so that it contains:

```ini
[KDE]
SingleClick=true
DoubleClickInterval=400
widgetStyle[$i]=breeze
```

Adding `[$i]` to a key marks it as immutable. The widget style is now locked: any setting a user makes, directly or through a dialog, isn't read by the configuration system.

Options can also be marked immutable by group and by file. To mark a group as immutable, add `[$i]` to the group name:

```ini
[KDE][$i]
SingleClick=true
DoubleClickInterval=400
widgetStyle=breeze
```

To mark an entire file as immutable, put `[$i]` on a line of its own at the start of the file. A file of the same name in the user's configuration directory is then ignored.

Setting defaults for applications works the same way. To make Ecco always show the available space indicator in its status bar, add this to a file called `dolphinrc` in a system directory:

```ini
[General]
ShowSpaceInfo[$i]=true
```

Any setting that can be changed in an application can be locked this way. To get a feel for what's available, look through the configuration files in `~/.config`.

Most applications need to be restarted for configuration settings to take effect. For changes to files such as `kdeglobals`, log out and back in.

So far this lets you set system defaults, and lock them if necessary, for any application. There is much more to Kiosk, covered below.

Files take precedence in this order, highest first:

- `~/.config/myAppConfigrc` (such as `dolphinrc`)
- `~/.config/kdeglobals`
- `~/.config/system.kdeglobals`
- `/etc/xdg/myAppConfigrc`
- `/etc/xdg/kdeglobals`
- `/etc/xdg/system.kdeglobals`
- `/etc/kde5rc`

`/etc/kde5rc` is a special case: it is hardcoded to this location, and isn't part of the XDG directory structure.

## Action restrictions

Many actions in applications and the desktop can be restricted by adding entries to a system-level file such as `/etc/xdg/kdeglobals`. This disables the file open action:

```ini
[KDE Action Restrictions][$i]
action/file_open=false
```

The action is then disabled and hidden, from the File menu and toolbar of applications for example. Any action registered with a name in an application's `KActionCollection` can be disabled this way, using `action/` followed by its name.

The actions that can be restricted include all the standard file and editing options, browsing actions, bookmarks and the help system. The [keys page](keys.md) has a longer list.

A few others are worth mentioning for corporate and similar environments:

- **`shell_access`:** whether the user can start a shell for entering commands, whether KRunner can run shell commands and arbitrary executables, and whether a command can be typed into the "Open With" dialog.
- **`logout` and `action/logout`:** whether the user can end the session. The code checks both, so set both.
- **`action/lock_screen`:** whether the user can lock the screen.
- **`run_command` and `action/run_command`:** access to KRunner, and to its entry in the desktop's context menu. Set both.
- **`movable_toolbars`:** whether toolbars can be moved.
- **`action/options_show_toolbar`:** whether toolbars can be hidden.
- **`plasma/plasmashell/unlockedDesktop`:** whether the user can unlock widgets, which would allow moving, adding and removing widgets, panels, launchers and so on.

In a public environment, set `lineedit_text_completion` to `false`, so that text boxes don't remember what was entered before. This doesn't affect third-party web browsers such as Firefox.

## URL restrictions

Kiosk can control access to specific URLs based on the referrer, the protocol, the host and the path. Some of this may be better done by a proxy server or a firewall, but it is very useful because SonicDE treats all locations as URLs. For example, to block access to websites:

```ini
[KDE URL Restrictions][$i]
rule_count=2
rule_1=open,,,,http,*.hotmail.msn.com,,false
rule_2=open,,,,http!,webmail.college.com,,false
```

This only affects applications that use these checks, not other browsers.

The first rule blocks all HTTP and HTTPS access to any URL with `.hotmail.msn.com` in the host. A protocol also matches protocols starting with the same name, so `http` includes `https`. The second rule blocks only HTTP, which forces users onto HTTPS, where it is supported. Rules like these could, for example, block third-party webmail and make users use a company or college email account over HTTPS.

The format is:

```text
rule_N=<action>,<referrer protocol>,<referrer host>,<referrer path>,<protocol>,<host>,<path>,<enabled>
```

An option left blank matches everything. Wildcards can be used in host names, as above. A path matches all URLs starting with that path, unless an exclamation mark is placed at the end of it.

Local files are URLs with the `file` protocol, so access to the local filesystem can be restricted too:

```ini
[KDE URL Restrictions][$i]
rule_count=6
rule_1=open,,,,file,,,false
rule_2=list,,,,file,,,false
rule_3=open,,,,file,,$HOME,true
rule_4=list,,,,file,,$HOME,true
rule_5=open,,,,file,,$TMP,true
rule_6=list,,,,file,,$TMP,true
```

These rules only let the user browse and open files in their home directory, along with the temporary directory that normal operation needs. For a security policy, use these with other rules, such as restricted shell access.

## Control module restrictions

Almost everything on the desktop can be configured through System Settings. Each group of settings, such as "Colors" or "Fonts", is a settings module, and each module can be locked down.

For example, to stop users changing their mouse settings, lock that module with an entry like this in `kdeglobals` or `/etc/kde5rc`:

```ini
[KDE Control Module Restrictions][$i]
kcm_mouse=false
```

Use the module's name, with no `.desktop` suffix. Run `kcmshell6 --list` for a list of available modules. In most public access environments, you'll probably want to lock almost all of them.

## Closing remarks

Kiosk is an essential tool for administrators who maintain or deploy SonicDE on many desktops or for many users, or where users can't be trusted. By preventing users from changing defaults and locking settings that pose a security risk, you can greatly reduce the time spent maintaining and repairing each desktop, and give each user a familiar desktop every time they sit down at the computer.
