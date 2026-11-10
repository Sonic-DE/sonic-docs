---
title: Icon widget
description: An icon on the desktop or in a panel that opens an application, a file, a folder or a web address.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-workspace (applets/icon: iconapplet.cpp, qml/main.qml); written from the code, not clicked through"
---

# Icon widget

The Icon widget is a single icon that opens something when you click it: an application, a file, a folder or a web address. It's what the [application launchers](launchers.md) create when you add an application to a panel from their context menu.

## Dropping files on it

You can drag files onto an Icon widget:

- On an application's icon, the application opens the files.
- On a program file's icon, the program is started with the files.
- On a folder's icon, the files are moved or copied into that folder, as when you drop them in [Ecco](../applications/ecco.md).

## Context menu

Right-click the icon for these entries:

- **Properties** opens the properties dialog of the icon, where you can change its name, its icon and, for an application, the command it runs.
- For a file or folder, there are entries to open it with other applications, and **Open Containing Folder** shows it in your file manager.
- For an application, its own extra actions are listed too, such as opening a new window.
