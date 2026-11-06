---
title: Changing the default settings
description: Roll out settings to new users, all users or several of your own machines.
source_url: https://userbase.kde.org/Tutorials/Modify_KDE_Software_Defaults
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-config, the stage's kwriteconfig6; ~/.kde paths replaced with ~/.config; BrowserApplication key not retested"
---

# Changing the default settings

There are three basic reasons to change default settings:

- You're a system administrator with new users every day, and you want them to have settings that aren't the default.
- You're a system administrator and want to change the desktop or system settings of all your users, and logging in as each of them to use [System Settings](../settings/index.md) isn't an option.
- You have several SonicDE machines, perhaps a computer at work behind a proxy, one at home and some virtual machines for testing. You set up computers often and want your settings rolled out identically.

In each case, you need to change settings files in `~/.config`, or the system-wide ones in `/etc/xdg`. See [Configuration files](../administration/configuration-files.md).

## /etc/skel

When a new user is created, the contents of `/etc/skel` are copied to their home folder. To change the settings for all future users, change the files in `/etc/skel`.

## Example

To change the default browser, you'd normally use the [Default Applications](../settings/default-applications.md) module. Sometimes you can't open System Settings, though. This script changes the default browser to Firefox instead:

```sh
#!/bin/bash
# Set the default browser to Firefox.
kwriteconfig6 --file kdeglobals --group General --key 'BrowserApplication[$e]' '!firefox'
```
