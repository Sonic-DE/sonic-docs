---
title: File operation dialogs
description: The windows you see when you open, rename, copy, move or delete files: Open With, Rename, File Already Exists and the confirmations.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-io (src/widgets/kopenwithdialog.cpp, renamefiledialog.cpp, renamedialog.cpp, skipdialog.cpp, widgetsaskuseractionhandler.cpp, widgetsopenorexecutefilehandler.cpp, executablefileopendialog.cpp, executablefileopendialog.ui; src/core/copyjob.cpp); written from the code, not clicked through"
---

# File operation dialogs

These windows appear in [Ecco](../applications/ecco.md), on the desktop, in [Open and Save dialogs](file-dialog.md) and in any other application that works with files. They look and work the same everywhere.

## Open With

Right-click a file and choose **Open With > Other Application…** in Ecco, or open a file that no application is set up for, and the **Choose Application** window asks which application to use. Some applications open the same window under the title **Open With**, and when it's opened for a whole file type rather than for particular files, the title names the type, as in **Choose Application for** followed by the type.

- **Known Applications** lists the installed applications, grouped like the application menu. Select one and click **OK**.
- The field above the list does two things. Type part of a name to narrow the list. Or type a command, with any options, to run a program that isn't in the list. The button at the end of the field browses for a program.
- **Remember application association for all files of type**, followed by the type's name, makes your choice the default for every file of that type, so it's used next time you open one. For a file whose type isn't known, the checkbox offers to remember the choice for all files with the same name ending, such as all `"*.xyz"` files.
- **Terminal options**, when expanded, has **Run in terminal**, for programs that work in a terminal. With SonicDE's Terminal as your terminal application, **Do not close when command exits** keeps the terminal open afterwards, so you can read what the program printed.
- **Get more Apps from Discover** appears when Discover is installed. It opens Discover with applications that can open this file type.

## Renaming

Select an item and choose **Rename…** or press F2. Ecco lets you edit a single item's name in place, unless you've turned that off in its settings. Elsewhere, a **Rename Item** window opens:

- **Rename the item … to:** Type the new name, then click **Rename**.
- If the new name starts with a dot, a warning says the item will be hidden from view, because names starting with a dot are hidden files.
- If you change the name's ending, a warning says the file's type may change, which could prevent it from opening correctly.
- If an item with the new name already exists, you're told, and **Rename** stays unavailable until you choose another name.

### Renaming several items at once

With several items selected, the **Rename Items** window opens. **How to rename:** offers three ways, and the window remembers which one you used last time. **Preview:** shows the old and new names before anything changes.

- **Enumerate:** Gives the items numbered names. Type a name containing `#`, and each `#` sequence is replaced by a number. Next to the name, choose **Replace filename** to use only the new name, or **Before filename** or **After filename** to add it to each existing name. **# will be replaced by ascending numbers starting with:** sets the first number. With **Replace filename**, the name must contain one sequence of `#`, unless all the items have different file name endings. Several `#` in a row add leading zeros, so `##` gives 01, 02, 03 and so on.
- **Replace text:** Replaces text in every name. Type the text to find in **Replacing:** and the new text in **With:**. You're told if no name contains the text.
- **Add text:** Adds the text in **Add Text:** to every name, **Before filename** or **After filename**.

File name endings are kept in all three ways. For more examples, see [Renaming several files in Ecco](../applications/ecco-batch-rename.md).

## When a file already exists

When you copy or move something to a place that already has an item with the same name, a window asks what to do. It's called **File Already Exists**, or **Folder Already Exists** for folders.

For files, it shows the **Source** and the **Destination** side by side, with their size, date and a preview, and tells you how they differ: whether the source is more recent or older, smaller or bigger, and whether the files are identical, seem identical or are different. If Kompare is installed, **Compare Files** shows the differences between two text files.

The buttons along the bottom:

- **Rename:** Give the item you're copying a new name, typed in the field at the bottom. **Suggest New Name** fills in a free name, such as the old one with a number added.
- **Skip:** Don't copy or move this item, and go on to the next.
- **Overwrite:** Replace the existing item with the new one. When copying several files, its menu also offers **Overwrite older files**, which only replaces files that are older than the ones you're copying, and skips the rest. It can only be chosen once **Apply to All** is checked.
- **Write Into:** For folders. Copies the contents into the existing folder, alongside what's already there. You're asked again for each file that's already in it.
- **Resume:** Shown when the existing file looks like an unfinished copy of the same file. Continues the copy where it stopped.
- **Cancel:** Stops the whole operation.

When several items are being copied, check **Apply to All** before clicking a button to give the same answer to every other conflict, so you aren't asked again.

## When an item can't be copied

If something goes wrong with one item during a copy or move, for example because its name contains characters the destination doesn't allow, an **Information** window explains the problem. Depending on the problem, it offers:

- **Replace:** Shown when the name has characters the destination doesn't allow. Replaces those characters so the item can be copied. **Replace All** does the same for every item with that problem.
- **Retry:** Shown for other problems. Tries this item again, after you've fixed the problem.
- **Skip:** When several items are being copied, leaves out this one and carries on. **Skip All** leaves out, without asking, the other items that run into the same kind of problem.
- **Cancel:** Stops the whole operation.

## Delete and trash confirmations

Before deleting, SonicDE asks you to confirm. The window lists what will be affected.

- **Delete Permanently:** Confirms deleting items for good, without the trash. It also appears when the trash is too full to take the items, or when there's no trash for that location, such as on some network folders. This can't be undone.
- **Empty Trash:** Confirms deleting everything in the trash. This can't be undone.
- **Move to Trash:** Confirms moving items to the trash. You can get them back from there. This confirmation is off unless you turn it on, for example in Ecco's settings.

Click **Cancel** to keep the items. Check **Do not ask again** to stop the window from appearing next time for this kind of action. The choices are saved in `~/.config/kiorc`, in the `[Confirmations]` group, as `ConfirmDelete`, `ConfirmEmptyTrash` and `ConfirmTrash`. Set one back to `true` to be asked again.

## Opening a program or script file

When you open a file that's marked as executable, such as a shell script, a window asks what to do with it: **Would you like to launch this file?**, or for text files such as scripts, **What do you wish to do with this file?** It shows the file's name and type.

- **Launch:** Runs the file as a program.
- **Open**, or **Open with** followed by an application's name: Opens the file to read or edit it, instead of running it. This button is only there for text files such as scripts.
- **Cancel:** Does nothing.

The choice is set in `~/.config/kiorc`, in the `[Executable scripts]` group: `behaviourOnLaunch` is `alwaysAsk` by default. Set it to `execute` to always run such files, or `open` to always open them without asking.
