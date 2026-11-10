---
title: File Associations
description: Choose which applications open which types of file.
source_url: https://invent.kde.org/plasma/kde-cli-tools/-/blob/master/doc/kcontrol6/filetypes/index.docbook
source_authors: [Mike McBride]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-terminal-tools c3e6ab9c (keditfiletype); read from code, not clicked through"
---

# File Associations

One of the most convenient things about the desktop is that it automatically matches a data file with its application. When you click a document in the file manager, the right application starts and loads it so you can start working.

These associations are crucial. Hundreds are created automatically for the most common data types, based on the most commonly included software and preferences. But they can't predict every combination of software and data files, file formats not yet invented, or everyone's favorite application for certain formats.

You can change or add file associations in this module.

Each file association is recorded as a MIME type, which stands for “Multipurpose Internet Mail Extensions”. It lets a computer determine the type of a file without opening and analyzing each one.

## Using this module

You can also start this module by typing `kcmshell6 kcm_filetypes` in a terminal or KRunner.

The associations are organized into several categories, shown in **Known Types**. At a minimum you'll have Application, Audio, Image, Inode, Message, Multipart, Text and Video.

> [!NOTE]
> There's no functional difference between the categories. They only help organize the associations.

Double-click a category to see the MIME types in it.

> [!TIP]
> You can also find a MIME type with the **Search for file type or filename pattern...** box above the list. Type a letter and the categories expand, showing only the MIME types that contain it. A second letter limits the list further.

### Adding a new MIME type

Click **Add...** and a small dialog appears. Select the category from **Group** and type the name in **Type name**.

### Removing a MIME type

Select the MIME type and click **Remove**. It's deleted immediately. You can only remove your own MIME types. For a system type you've changed, **Revert** returns it to its initial system-wide definition.

### Editing a MIME type's properties

Select the MIME type, and its current values appear, split into two tabs.

**General** has 4 properties:

1. The icon, visible in the file manager.
2. **Filename Patterns**, a search pattern used to determine the MIME type.
3. **Description**, a short description for your benefit.
4. **Application Preference Order**, which determines the applications associated with the MIME type.

**Embedding** has settings for how services handle the type.

### Changing the icon

Click the icon button. A dialog shows all available icons. Click the one you want and click **OK**.

### Editing the patterns

**Filename Patterns** determines which files belong to this MIME type.

Usually, files are selected by suffix. Files ending in `.wav` are sound files in the WAV format, and files ending in `.c` are programs written in C.

The asterisk (`*`) is a wildcard that matches any number of characters. For example, `*.pdf` matches `Datafile.pdf`, `Graphics.pdf` and `User.pdf`, but not `PDF`, `Datafile.PDF` or `.pdf`.

To add a pattern, click **Add...** next to the list, type it into **Extension:** in the **Add New Extension** dialog and click **OK**. To remove one, select it and click **Remove**.

> [!TIP]
> It's useful to have multiple patterns, such as one for lower case and one for upper case, so that the file type is determined more accurately.

### Editing the description

Type a short description in **Description**. It's only there to help you and doesn't affect the MIME type.

### Editing the application associations

The list shows all the applications associated with the MIME type, in order. The top one is tried first, then the next one down, and so on.

> [!NOTE]
> Each system has a different selection of applications, so with several associations per MIME type, the desktop still works when one isn't installed. If the first application for PDF files isn't on your system, for example, the second one starts instead.

Since the order matters, select an application and click **Move Up** or **Move Down** to change it. **Apply To...** uses the current order for other file types.

**Add...** opens a dialog where you select another application to use for this MIME type.

**Edit...** changes an application's options for this MIME type, in a dialog with General, Permissions, Application and Details tabs. On the Application tab you can edit its name, description and comment. In the **Command** field you can use placeholders after the command, which are replaced with the actual values when it runs:

- `%f`: a single file name
- `%F`: a list of files, for applications that can open several local files at once
- `%u`: a single URL
- `%U`: a list of URLs
- `%d`: the folder of the file to open
- `%D`: a list of folders
- `%i`: the icon
- `%m`: the mini-icon
- `%c`: the caption

**Remove** removes an application, so that it never runs with this MIME type.

> [!TIP]
> It's a good idea to move an unwanted application lower in the list instead of deleting it. If you delete it and your preferred application stops working, there won't be one to open the document.

### Embedding

[Ecco](../applications/ecco.md) doesn't use embedded views, and always opens a file in its associated application. These settings only apply to applications that can embed viewers.

**Services Preference Order** lists the embedded services for this type in the order they're used. Use **Move Up** and **Move Down** to change it.

### Saving your changes

Click **Apply** to make your changes permanent.

## Editing a single file type

You don't have to open this module to change one file type. In a file's **Properties** dialog, the **General** tab has **Change…** next to the application that opens it. It opens the File Type Editor, a window titled **Edit File Type** followed by the type's name, with the same **General** and **Embedding** tabs as this module. For a file with no registered type, the button is **Create…** instead, and the window, titled **Create New File Type**, creates a type for it.
