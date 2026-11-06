---
title: Font Management
description: Install, remove, preview and manage your fonts.
source_url: https://invent.kde.org/plasma/plasma-workspace/-/blob/master/doc/kcontrol/fontinst/index.docbook
source_authors: [Craig Drummond]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-workspace e4f0096493 (kcms/kfontinst/kcmfontinst); read from code, not clicked through"
---

# Font Management

This module installs, removes, previews and manages your fonts.

## Font groups

There are 4 special predefined font groups:

1. **All Fonts:** All fonts, both personal and system-wide.
2. **Personal Fonts:** Your personal fonts, which aren't available to other users.
3. **System Fonts:** Fonts available to all users. Installing or removing a system-wide font needs administrator privileges.
4. **Unclassified:** All fonts that haven't been placed in a group of your own. It only appears if you have some.

To add a font to a group, drag it from the list of fonts onto the group. To remove a font from a group, drag it onto All Fonts.

Below this list are buttons to create a new group, remove a group, and enable or disable the fonts in the current group. The context menu of the list has more items to print font samples and export a group to an archive.

### Enabling and disabling

If you have many fonts, you may want only certain ones active at certain times. You can disable individual fonts or whole groups. Disabling a font doesn't remove it from the system, it just hides it from applications. Enabling it again lets you use it.

## Font list

The main display is a list of the installed fonts, grouped by family name. The number in square brackets is the number of installed styles for that family. For example, Times may be listed as:

- Times \[4\]
  - Regular
  - Italic
  - Bold
  - Bold Italic

To install a font, press **Install from File…** and select the fonts you want. The selected group controls where they're installed.

To uninstall fonts, select them in the list and press the delete button.

The right mouse button opens a context menu with more actions, such as Enable, Disable, Print, Open in Font Viewer and Reload.

### Filtering

A text field above the list filters the fonts by these categories:

1. Family
2. Style
3. Foundry
4. FontConfig match, which lets you enter a family name and see the family FontConfig would actually use
5. Font file type
6. Font file name
7. Font file location
8. Writing system

### Getting new fonts

You can install new fonts from local files, or download them with **Get New Fonts…**. Downloaded fonts go into your Personal Fonts group. To install them system-wide, drag them onto the System Fonts group, which needs administrator privileges.

## Duplicate fonts

If you have lots of fonts, you may have duplicates.

**Find Duplicates…** opens a tool that scans your system for fonts with multiple files. For example, if you have `times.ttf` and `times.TTF` installed in `/usr/local/share/fonts`, the underlying font mechanism, FontConfig, only sees one of them. If you uninstalled the font it would reappear, because only one file would have been removed. The tool lists each font with multiple files and its files. To select a file for deletion, click the column containing the trash can icon.

## Preview

This displays preview text in different font sizes. Its context menu lets you zoom in and out, select a preview type (Standard Preview or All Characters) and change the preview text.

Use the Font Viewer application if you need more preview types for Unicode blocks.
