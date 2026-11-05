---
title: Creating service menus
description: Add your own actions to the context menus of files and folders.
source_url: https://develop.kde.org/docs/apps/dolphin/service-menus/
source_authors: [Carl Schwan, Jeffrey Brown, Leo **, Marius P, Méven Car, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "KFileItemActions in sonic-frameworks-io and sonic-ecco's context menu settings and servicemenuinstaller. Menu placement, MIME matching, the URL count and protocol keys and the executable-bit rule run through KFileItemActions from a test program against the staged libraries; plasma-apply-wallpaperimage run on a sonicshell on a private Xvfb and D-Bus. The menus were not opened in Ecco's own window, and Download Services was read from code, not run."
---

# Creating service menus

Being able to choose actions for a certain file type from the context menu of a file manager is an often requested feature. You don't need to be a software developer to add them. This page shows how, step by step.

A *service menu* is a special entry that appears in the context menu of a file or folder, depending on the type of the selected files. For example, if the Ark archive tool is installed, right-clicking an archive offers to extract it. Any application using the KIO context menu shows them.

In this tutorial, we'll create actions that set an image as the desktop wallpaper from its context menu.

## Where service menus are located

Service menus are `.desktop` files, the same kind of file that creates entries in the application launcher. They are found in the `kio/servicemenus` directory in the generic data locations. This command prints those directories, searched in the order they appear:

```bash
qtpaths --locate-dirs GenericDataLocation kio/servicemenus
```

On a default setup, the order is:

```text
~/.local/share/kio/servicemenus
/usr/share/kio/servicemenus
```

A file in the local location must be marked as executable before its commands will run, because that location isn't authorized by default. Without this, the entry still appears in the menu, but selecting it doesn't run its command.

```bash
touch setAsWallpaper.desktop
chmod +x setAsWallpaper.desktop
```

Service menus installed with "Download Services…" in Ecco's context menu settings go in the local location, and are marked as executable for you.

Older service menus in a `kservices5` directory, with the key `ServiceTypes=KonqPopupMenu/Plugin`, are still read for compatibility. Use `kio/servicemenus` for new ones.

## The start of a service menu

We'll name the file `setAsWallpaper.desktop`. All that matters about the name is that it is unique and ends in `.desktop`. Every service menu starts with this section:

```ini
[Desktop Entry]
Type=Service
MimeType=image/png;image/jpeg;
Actions=setAsWallpaper
```

The heading starts the `Desktop Entry` group: all the options up to the next heading belong to it.

`Type=Service` is needed because the default type is `Application`, something with an `Exec` line.

`MimeType` sets the file types the service menu applies to, as a list separated by semicolons, with no spaces. Here, it shows up when we select PNG or JPEG images.

> **Tip:** To create a service menu for folders, use the `inode/directory` type. For all files, use the base type `application/octet-stream`, which doesn't match folders.

You can also specify a whole group of types with a wildcard. To apply to all images:

```ini
MimeType=image/*;
```

`Actions` lists the actions in the service menu, separated by semicolons. Each one gets a section of its own that defines what it does.

## Creating an action

So far we've named one action, `setAsWallpaper`. Now add a heading for it at the end of the file. These files are case sensitive, so watch the capitalization.

```ini
[Desktop Action setAsWallpaper]
```

Next, give the action a name that the user will see:

```ini
Name=Use As Wallpaper
```

To translate the name, add another `Name` entry followed by the language code. For example:

```ini
Name[fi]=Aseta taustakuvaksi
```

Next, add an icon, by name and without a file extension. You can find icons by name in `/usr/share/icons/`, or with Icon Explorer from `sonic-theme-sdk`. Without an `Icon` line the action still works, it just doesn't look as nice.

```ini
Icon=preferences-desktop-wallpaper
```

Finally, make it useful:

```ini
Exec=plasma-apply-wallpaperimage %f
```

`Exec` is what runs when the user selects the action. You can put any command there. `%f` is replaced by the path of the file, and `%u` by its URL. If a command accepts several files at a time, use `%F` or `%U`. All the possible values are in [the Desktop Entry Specification](https://specifications.freedesktop.org/desktop-entry-spec/latest/exec-variables.html).

The file now looks like this:

```ini
[Desktop Entry]
Type=Service
MimeType=image/*;
Actions=setAsWallpaper

[Desktop Action setAsWallpaper]
Name=Use As Wallpaper
Icon=preferences-desktop-wallpaper
Exec=plasma-apply-wallpaperimage %f
```

Save it, make it executable, and right-click an image in Ecco: the "Use As Wallpaper" item should be in the menu.

> **Tip:** If a task needs more than one command, use a shell: `Exec=/bin/sh -c "<YOUR COMMANDS HERE>"`.

## Adding more actions

Our action uses the wallpaper's current fill mode. To let the user choose how the image fills the screen, we can add actions for the modes `plasma-apply-wallpaperimage` understands: `stretch`, `preserveAspectFit`, `preserveAspectCrop` and `pad`.

First, change the `Actions` line. Note the semicolons, not commas.

```ini
Actions=setAsWallpaper;fitAsWallpaper;
```

Then add a section at the end of the file:

```ini
[Desktop Action fitAsWallpaper]
Name=Use As Wallpaper, Fitted
Icon=preferences-desktop-wallpaper
Exec=plasma-apply-wallpaperimage --fill-mode preserveAspectFit %f
```

`fitAsWallpaper` in the heading says which action this is. Right-clicking an image now offers another option. The menu is built from the files each time, so there's no need to restart anything.

With many actions, and all the other service menus on a system, the menu can quickly get out of hand. To put a service menu's actions in a submenu, add this to the `Desktop Entry` group:

```ini
X-KDE-Submenu=Use As Wallpaper
```

The file now looks like this:

```ini
[Desktop Entry]
Type=Service
MimeType=image/*;
Actions=setAsWallpaper;fitAsWallpaper;
X-KDE-Submenu=Use As Wallpaper

[Desktop Action setAsWallpaper]
Name=Keep Current Fill
Icon=preferences-desktop-wallpaper
Exec=plasma-apply-wallpaperimage %f

[Desktop Action fitAsWallpaper]
Name=Fitted
Icon=preferences-desktop-wallpaper
Exec=plasma-apply-wallpaperimage --fill-mode preserveAspectFit %f
```

By default, entries go in an "Actions" submenu when there are several, and at the top level when there are very few. To always show your menu at the top level, add `X-KDE-Priority=TopLevel` to the `Desktop Entry` group.

## Advanced properties

You may not need these, but it helps to know they exist. They all go in the `Desktop Entry` group.

| Property | Explanation |
| --------------- | --------------- |
| `X-KDE-Protocol` | The scheme the URLs must have, such as `smb` on a Samba share |
| `X-KDE-Protocols` | A list of schemes the URLs can have, such as `file,smb` |
| `X-KDE-RequiredNumberOfUrls` | How many URLs must be selected for the menu to appear. To allow several counts, separate them with commas, such as `2,4,6` |
| `X-KDE-MinNumberOfUrls` | The minimum number of URLs that must be selected |
| `X-KDE-MaxNumberOfUrls` | The maximum number of URLs that can be selected |

For more dynamic options, see [KAbstractFileItemActionPlugin](/docs/api/kiowidgets/kabstractfileitemactionplugin), which explains how to write such plugins in C++.

## Examples

This is a list of service menus contributed by users:

- [KDE Service Menus from Z-Ray Entertainment](https://gitlab.com/z-ray-entertainment/kde-service-menus)

## Troubleshooting

To check a service menu for errors, use `desktop-file-validate`:

```bash
desktop-file-validate /path/to/service.desktop
```

It follows the Desktop Entry Specification, which doesn't define `Type=Service`, so it reports errors about that type and about `MimeType` and `Actions` even in a working file. Look for anything else it reports.

If an entry appears but nothing happens when you select it, check that the file is executable. To see error messages, start Ecco from a terminal. On a system with systemd, you can also check the journal with `journalctl -r`.
