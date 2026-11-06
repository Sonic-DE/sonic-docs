---
title: Default Applications
description: Choose the applications that handle basic tasks.
source_url: https://invent.kde.org/plasma/plasma-workspace/-/blob/master/doc/kcontrol/componentchooser/index.docbook
source_authors: [Burkhard Lück]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-workspace e4f0096493 (kcms/componentchooser); read from code, not clicked through"
---

# Default Applications

This module sets the applications that handle basic tasks. Applications sometimes need to open a terminal, send an email, manage files or show a map. To do so consistently, they always call the same components, and here you choose which programs those are.

- **Internet:** Web browser, Email client, Calendar, Phone Numbers
- **Multimedia:** Image viewer, Music player, Video player
- **Documents:** Text editor, PDF viewer
- **Utilities:** File manager, Terminal emulator, Archive manager, Map

Click the box of the component you want to configure and select your favorite. Choose **Other…** to open the application chooser and select one manually.

If an application may not be able to open all the file types of that kind, the module says so. **View Details** shows which types, and you can set how they open with **Force All to Open in** that application or **Configure Manually…**.

To set which application opens a specific file type, see [File Associations](file-associations.md).
