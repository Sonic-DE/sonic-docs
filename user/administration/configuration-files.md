---
title: Configuration files
description: The format of configuration files, including localization, shell expansion and lock-down.
source_url: https://userbase.kde.org/KDE_System_Administration/Configuration_Files
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-config (core/kconfigini.cpp, core/kconfig.cpp), the stage's kwriteconfig6; read from code, not clicked through"
---

# Configuration files

## File format

SonicDE uses a simple text-based file format for its configuration files. It consists of key-value pairs placed in groups. All configuration files use UTF-8 encoding for text outside the ASCII range.

A group starts with a group name in square brackets. All the key-value entries that follow belong to the group. The group ends when another group starts or at the end of the file.

Entries at the top of the file with no group name before them belong to the default group.

### Example: a simple config file

This configuration file has two groups. The first contains the keys `LargeCursor` and `SingleClick`, and the second contains the keys `Show hidden files` and `Sort by`.

```ini
[KDE]
LargeCursor=false
SingleClick=true

[KFileDialog Settings]
Show hidden files=false
Sort by=Name
```

Entries in a group consist of a key and a value separated by an equals sign. The key can contain spaces and may be followed by options in square brackets.

The part after the equals sign is the entry's value. Any white space around the equals sign is ignored, as is any trailing white space.

To include a space at the beginning or end of a value, use a backslash followed by `s`.

These are all the backslash codes:

- `\s` for a space
- `\t` for a tab
- `\r` for a carriage return
- `\n` for a line feed (new line)
- `\\` for the backslash itself

### Example: white space

This fragment is equivalent to the previous example. White space around the key and value is ignored.

```ini
[KDE]
LargeCursor=          false
SingleClick = true

[KFileDialog Settings]
   Show hidden files   = false
Sort by =Name
```

### Example: preserving white space

Here, the value of `Caption` starts with two spaces, and `Description` contains three lines of text. Line feeds in backslash notation separate the lines.

```ini
[Preview Image]
Caption=\s My Caption
Description=This is\na very long\ndescription.
```

Empty lines in configuration files are ignored, as are lines starting with a hash mark (`#`). You can use the hash mark to add comments, but comments aren't preserved when an application updates the file.

## Configuration

There can be multiple configuration files with the same name in the different [configuration directories](xdg-filesystem-hierarchy.md#configuration). In that case, the contents of all of them are combined, key by key. If the same key in a group is defined in more than one place, the value from the directory with the highest precedence is used. Files in `$XDG_CONFIG_HOME`, normally `~/.config`, always have the highest precedence. If a key in a group is defined several times in a single file, the value of the last entry is used.

This cascading scheme can provide users with system-wide or organization-wide default settings, while still allowing them to make their own changes. Entries that match a default provided this way aren't written to the user's configuration file, so changes to the default settings reach the user immediately. This differs from the traditional way of providing defaults through `/etc/skel`, where changes only reach newly created accounts.

When you don't want users to change a default setting, you can lock it down.

## Shell expansion

*Shell expansion* can provide more dynamic default values. It builds a configuration key's value from the value of an environment variable.

To enable shell expansion for an entry, follow the key with `[$e]`. Normally the expanded form is written into the user's configuration file after first use. To prevent that, lock the entry down by using `[$ie]`.

### Example: dynamic entries

The value of `Email` here is made by filling in the `$USER` and `$HOST` environment variables. When *joe* is logged in on *joes_host*, the value is `joe@joes_host`. The setting isn't locked down.

```ini
[Mail Settings]
Email[$e]=${USER}@${HOST}
```

## Localization

Any configuration entry can be indexed with a language code. The language the user has selected for the desktop is then used to look up the key's value. If the default language (American English) is selected, or no index matches the selected language, the entry without an index is used.

### Example: UTF-8 in keys

Here, the value of `Caption` depends on the language. If the user has selected French (language code `fr`), the value is `Ma Légende`. In all other cases it's `My Caption`.

```ini
[Preview Image]
Caption=My Caption
Caption[fr]=Ma Légende
```

## Lock-down

To stop users overriding default settings, you can lock these settings down in the system-wide configuration files. Settings can be locked individually, per group, or per file. Lock an individual entry by adding `[$i]` after the key. Lock a group of entries by placing `[$i]` after the group name. To lock the entire file, start the file with `[$i]` on a line of its own.

### Example: using [$i]

Here, the `Caption` entry is locked, and so are all entries in the `Mail Settings` group.

```text
[Preview Image]
Caption[$i]=My Caption

[Mail Settings][$i]
Host[$e]=${hostname}
Email=someone@example.com
```

If an entry is locked, entries that would otherwise take precedence over the default setting are ignored.

Changes that applications make to locked settings are silently dropped. Applications may respond differently to locked settings. Some recognize this and remove the option from their interface. Others keep offering it even though it has no effect. It may also be possible to change the setting in the running program, in which case the change lasts as long as the program runs. When the program restarts, it returns to the locked default.

## Editing from the command line

For scripts or changing files from the command line, `kwriteconfig6` is very useful. It takes a configuration file name, a group, a key, an optional type and a value, for example:

```sh
kwriteconfig6 --file kickerrc \
              --group General \
              --key AutoHidePanel \
              --type bool \
              true
```
