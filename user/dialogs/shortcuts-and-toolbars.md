---
title: Shortcuts and toolbars in applications
description: Change an application's keyboard shortcuts and toolbars with Configure Keyboard Shortcuts and Configure Toolbars.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-xml-gui (src/kshortcutsdialog.cpp, kshortcutsdialog.ui, kshortcutseditor.cpp, kshortcuteditwidget.cpp, kshortcutschemeseditor.cpp, kkeysequencewidget.cpp, kedittoolbar.cpp, ktoolbareditor.cpp, ktoolbar.cpp, ktoolbarhandler.cpp, ui_standards.rc); written from the code, not clicked through"
---

# Shortcuts and toolbars in applications

Most SonicDE applications, such as [Ecco](../applications/ecco.md) and [Terminal](../applications/terminal.md), let you change their keyboard shortcuts and toolbars in the same way. You'll find **Configure Keyboard Shortcuts…** and **Configure Toolbars…** in the **Settings** menu, or in the [menu button](application-menus.md#the-menu-button) when the menu bar is hidden.

The changes only apply to that one application. Shortcuts that work everywhere on the desktop are set in the [Shortcuts](../settings/shortcuts.md) module of System Settings.

## Configure Keyboard Shortcuts

The window lists all of the application's actions. Type in the search field at the top to find an action by its name, such as "Copy", or by its keys, such as "Ctrl+C".

The columns are:

- **Action:** the name of the action.
- **Shortcut:** its main shortcut.
- **Alternate:** a second shortcut that does the same.
- **Global** and **Global Alternate:** shortcuts that work even when the application isn't the active window, for the actions that support them.

Click an action to open its editor below it. For each shortcut you can choose **Default:**, the shortcut the application comes with, or **Custom:**. To set a custom shortcut, click the button next to **Custom:**, then press the keys, just as you would to use them. **Clear** removes the shortcut.

If the keys you pressed are already used by another action, a message tells you which one. Click **Reassign** to take the shortcut for this action, which removes it from the other one, or **Cancel** to keep things as they are.

The buttons along the bottom:

- **Manage Schemes:** Shows the **Shortcut Schemes** section. A scheme is a named set of shortcuts. Choose one in **Current scheme:**, make your own with **New…**, or remove one with **Delete**. **More Actions** offers **Save shortcuts to scheme**, **Export Scheme…** and **Import Scheme…**, to keep your shortcuts in a `.shortcuts` file or bring them to another computer.
- **Print:** Prints the list of shortcuts.
- **Defaults:** Sets every shortcut back to the application's defaults.

Click **OK** to keep your changes, or **Cancel** to forget them.

## Configure Toolbars

- **Toolbar:** Chooses which of the application's toolbars to change.
- **Available actions:** lists the actions you can add. **Current actions:** lists what's on the toolbar now, from left to right, or top to bottom. Each list has a **Filter** field to find an action.
- Use the arrow buttons between the lists, or drag, to add, remove and reorder actions. **--- separator ---** adds a dividing line, and **--- expanding spacer ---** adds a gap that takes up the free space, pushing the actions after it to the far end.
- **Change Icon…** chooses a different icon for the selected action.
- **Change Text…** changes the text shown on the toolbar for the selected action, in **Icon text:**. Check **Hide text when toolbar shows text alongside icons** to show only the icon for this action when the toolbar shows text beside icons, which saves space.

**Defaults** asks whether to reset all toolbars of the application to their defaults. Click **Reset** to do so. This is applied straight away.

## The toolbar's right-click menu

Right-click an empty part of a toolbar, or one of its buttons, for quick changes.

Under **Show Text**, when you right-clicked a button, its name is listed with a checkbox. Uncheck it to show only that button's icon while the toolbar shows text alongside icons. This is the same as **Hide text when toolbar shows text alongside icons** in **Change Text…**.

Under **Toolbar Settings**:

- **Text Position:** **Icons Only**, **Text Only**, **Text Alongside Icons** or **Text Under Icons**.
- **Icon Size:** **Default**, or one of the sizes, from **Small** to **Huge**.
- **Orientation:** Moves the toolbar to the **Top**, **Left**, **Right** or **Bottom** of the window. It's hidden while toolbar positions are locked.
- **Configure Toolbars…** opens the window described above.
- **Lock Toolbar Positions:** Stops the toolbars from being dragged to another place by accident.

Applications with several toolbars have a **Toolbars Shown** menu, in the **Settings** menu and the right-click menu, to show or hide each one. Applications with one toolbar have **Show Toolbar** instead.
