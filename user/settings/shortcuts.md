---
title: Shortcuts
description: Change keyboard shortcuts and add your own for applications and commands.
source_url: https://invent.kde.org/plasma/plasma-desktop/-/blob/master/doc/kcontrol/keys/index.docbook
source_authors: [Mike McBride, Jost Schenck]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-desktop-interface fad996458a (kcms/keys); read from code, not clicked through"
---

# Shortcuts

Many people prefer the keyboard for some tasks. Pressing Ctrl+F is often faster than moving your hands to the mouse and opening the Edit menu to select Find.

Since people have different preferences, the desktop offers full customization of shortcuts. A shortcut is a combination of an action with a key or combination of keys.

## Finding shortcuts

The list on the side of the module is divided into sections:

- **Applications**
- **Commands**, your own commands and scripts
- **System Services**
- **Common Actions**, standard actions often found in applications, such as Save, Print and Copy

Select an item to see its shortcuts. The search field finds shortcut names and key combinations.

The common actions are only the standard ones. Most applications also define their own, which you customize in the application's own shortcuts dialog.

## Changing a shortcut

Expand an action to configure it. Each action can have:

- **Default shortcuts:** The ones it comes with, which you can turn on or off.
- **Custom shortcuts:** Click **Add New**, then press the key combination you want.

If the combination is already in use, you can choose to **Reassign** it. Deleting a shortcut doesn't take effect until you apply your changes, and you can undo it until then.

## Adding your own

**Add New** lets you choose:

- **Application…** to pick an application to launch. If it has extra actions, they're available too.
- **Command or Script…** to give a name to a command, or choose a script file.

To remove an item with all its shortcuts, use its delete button in the list.

## Shortcut schemes

**Import…** loads a shortcut scheme, either a built-in one or a custom scheme from a file.

**Export…** saves your shortcuts to a file. Select the components to include. You can't export while there are unsaved changes.
