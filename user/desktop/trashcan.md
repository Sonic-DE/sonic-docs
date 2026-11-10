---
title: Trashcan
description: A widget for the desktop or a panel that opens, fills and empties the trash.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-desktop-interface (applets/trash/main.qml, trash.cpp); written from the code, not clicked through"
---

# Trashcan

The **Trashcan** widget gives you quick access to the trash from the desktop or a [panel](panels.md). Add it like any other widget; you can also show it in the [system tray](system-tray.md).

On the desktop, the widget shows the trash icon with **Trash** and the number of items below it, or **Empty** when there's nothing in the trash. In a panel it shows only the icon, and the tooltip gives the number of items.

## Using it

- Click it to open the trash in the file manager.
- Drag files onto it to move them to the trash.
- Right-click it for these actions:
  - **Open:** Opens the trash in the file manager.
  - **Empty:** Empties the trash. You're asked to confirm first if your settings ask for confirmation. While the trash is being emptied, the widget says **Emptying…**.
  - **Trash Settings…:** Opens the [Trash](../settings/trash.md) settings, where you can limit the trash size and have old files removed automatically.

When the widget has keyboard focus, Space or Return opens the trash.
