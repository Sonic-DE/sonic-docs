---
title: Open and Save dialogs
description: Find your way around the window that opens and saves files in SonicDE applications.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-io (src/filewidgets/kfilewidget.cpp, src/filewidgets/kdiroperator.cpp), sonic-frameworks-settings (src/gui/kstandardshortcut.cpp), sonic-qt-theme-bridge (qt6/src/platformtheme/kdeplatformtheme.cpp); written from the code, not clicked through"
---

# Open and Save dialogs

Whenever an application asks you to pick a file to open, or a name and place to save one, you see the same window. SonicDE uses it for its own applications and for other Qt applications too, so it works the same everywhere.

The window has a toolbar at the top, the [Places panel](../applications/ecco-guide.md#places) on the left, the file list in the middle, and the file name and file type at the bottom.

## The toolbar

From left to right:

- **Back**, **Forward**, **Parent Folder** and **Reload** move around the folders you've visited and refresh the list.
- **Icons View**, **Compact View** and **Details View** switch how the file list looks: large icons, a compact list of names, or a table with columns such as size and date.
- **Show Preview** (F12) shows small pictures of the files' contents in the list, instead of their type icons.
- **Sorting** sets the order of the list. Choose **Sort by Name**, **Sort by Size**, **Sort by Date** or **Sort by Type**, then the direction. The direction's name follows what you sort by, such as **A-Z** and **Z-A** for names, or **Newest First** and **Oldest First** for dates. **Folders First** keeps folders above files, and **Hidden Files Last** puts hidden files at the end.
- **Bookmarks** opens the bookmark menu, where you can add, edit and choose bookmarked folders. See [Bookmarks in applications](../applications/ecco-guide.md#bookmarks-in-applications).
- The slider at the right changes the size of the icons in the list. Its tooltip, **Icon size: … pixels**, gives the current size. The zoom buttons on either side of it, Ctrl++ and Ctrl+-, do the same.
- **New Folder…** (Ctrl+Shift+N) creates a folder in the current folder.
- **Options** opens the menu described next.

## The Options menu

- **Allow Expansion in Details View:** In Details View, folders get an arrow that shows their contents in place, as a tree, without opening them.
- **Show Hidden Files** (Ctrl+H or Alt+.): Shows files and folders whose names start with a dot.
- **Show Places Panel** (F9): Shows or hides the Places panel on the left.
- **Show Quick Filter** (Ctrl+I or \\): Shows a filter bar. Type in **Filter by name…** to see only the files whose names contain what you type. The lock button, **Keep Filter When Changing Folders**, keeps the filter when you open another folder; otherwise it's cleared. The close button, **Hide Filter Bar**, hides the bar again.
- **Show Preview Panel** (F11): Shows a panel with a larger preview of the selected file.

## Working with files in the dialog

Right-click in the file list for a menu of file operations, so you don't need to open a file manager:

- **Create New** makes a new folder, or a new file from one of the templates it lists, in the current folder.
- **Rename…** (F2) renames the selected file.
- **Move to Trash** (Delete) moves the selected files to the trash. For files that aren't on your computer, such as on a network folder, **Delete** (Shift+Delete) is shown instead, because those can't go to the trash. Hold Shift while opening the menu to get **Delete** for local files too.
- **Sorting** offers the same choices as the toolbar button.
- **View Mode** switches between **Short View**, **Detailed View**, **Tree View** and **Detailed Tree View**. The tree views show folders with an arrow that opens their contents in place.
- **Reload** refreshes the list.
- **Open Containing Folder** opens the folder that holds the selected file.
- **Properties** opens the [Properties dialog](properties.md) for the selected file.

Deleting and moving to the trash ask first, as described in [Delete and trash confirmations](file-operations.md#delete-and-trash-confirmations).

## The file name and type

At the bottom of the dialog:

- **Name:** The file to open, or the name to save as. When you open several files, it lists them all. If you've changed the name, the undo button at the end of the field, **Undo filename change**, takes back your change. A clear button empties the field.
- **File type:** Chooses which files are listed when opening. When saving, it chooses the format the file is saved in.

When saving, **Automatically select filename extension**, followed by the extension in brackets, helps with file name endings:

- If you change the file type, the extension in the name changes to match.
- If you type a name without an extension, the one for the chosen file type is added when you save.

To save a name without an extension once, end it with a dot. The dot is removed, and no extension is added.

If a file with the name you chose already exists, an **Overwrite File?** message asks whether to replace it. Click **Overwrite** to replace it, or **Cancel** to go back and choose another name.
