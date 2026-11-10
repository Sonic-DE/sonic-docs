---
title: Properties dialog
description: See and change a file's or folder's name, permissions, checksums and, for launchers, how the application starts.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-io (src/widgets/kpropertiesdialogbuiltin_p.cpp, kfilepropspluginwidget.ui, checksumswidget.ui, kpropertiesdesktopbase.ui, kpropertiesdesktopadvbase.ui); written from the code, not clicked through"
---

# Properties dialog

The Properties dialog shows everything about a file or folder and lets you change some of it. Open it by right-clicking an item in [Ecco](../applications/ecco.md), on the desktop or in an [Open or Save dialog](file-dialog.md), and choosing **Properties**. You can select several items first to see or change them together.

The dialog has several tabs. Which ones you see depends on what you selected.

## General

- **Name:** At the top, next to the icon. Type a new name and click **OK** to rename the item. For a single folder or application launcher, the icon is a button: click it to choose a different icon.
- **Type:** What kind of file it is. Hover over it to see the technical type name.
- **Content:** What the file really contains, judged from its contents. It's only shown when that differs from the type its name suggests.
- **Open with:** The application that opens files of this type. **Change…** opens the [file type editor](../settings/file-associations.md) for this type, where you can choose and order the applications. If the file's type isn't known, the button is **Create…**, and makes a new type for files with this file name ending.
- **Location:** The folder the item is in.
- **Size:** The size, rounded and to the byte. For a folder it's the total of everything inside, with the number of files and sub-folders: on your computer it's worked out straight away, and the button becomes **Refresh**, to count again. Elsewhere, click **Calculate** to start, and **Stop** to end it early. If Filelight is installed, **Explore in Filelight** shows what takes up the space.
- **Size on disk:** How much space it really takes up on the disk, which can differ from its size.
- **Points to:** For a link, the place it leads to. You can type a new target here. **Show target** opens it.
- **Created:**, **Modified:** and **Accessed:** When the item was created, last changed and last opened.

For a folder, the tab also shows **Free space:** on the disk it's on. For folders on your computer it adds that disk's **File system:**, where it's **Mounted on:** and where it's **Mounted from:**.

## Permissions

This tab is shown for items whose permissions can be changed, such as files on your own disks.

Under **Access Permissions**, choose what three kinds of people may do with the item:

- **Owner:** the user who owns it.
- **Group:** the members of its group.
- **Others:** everyone else.

For each, choose **No Access**, **Can Only View** or **Can View & Modify**. For folders the choices talk about the content, as in **Can Only View Content**. When you've selected several items with different settings, **Varying (No Change)** leaves each as it is.

- **Allow executing file as program:** For files. Lets the file run as a program or script.
- **Only owner can delete or rename contents:** For folders. Other people can still add files, but only remove or rename their own. This is how shared folders such as `/tmp` work.

**Advanced Permissions** opens a grid with each permission separately, as **Read**, **Write** and **Exec** (for folders **Show Entries**, **Write Entries** and **Enter**), for **User**, **Group** and **Others**. Its **Special** column holds **Set UID**, **Set GID** and **Sticky**. Leave these alone unless you know you need them.

Under **Ownership**, **User:** and **Group:** show who owns the item. Only the administrator can give a file to another user, and you can only choose groups you belong to.

For folders, check **Apply changes to all subfolders and their contents** to change everything inside as well.

Only the owner can change permissions. A link has no permissions of its own, so the tab says so.

## Checksums

A checksum is a short code worked out from a file's contents. Websites often publish one next to a download, so you can check that the file arrived complete and unchanged. This tab is shown for files on your computer that you can read.

- Paste the published checksum into **Expected checksum (MD5, SHA1, SHA256 or SHA512)...**, or click **Paste** to take it from the clipboard. The dialog works out the right kind, compares it, and says **Checksums match.** or **Checksums do not match.**
- Under the field, click **Calculate** next to **MD5:**, **SHA1:**, **SHA256:** or **SHA512:** to work out that checksum. **Copy** then puts it on the clipboard.

With several files selected, the tab says whether **The checksums of all files are identical.** or **The selected files have different checksums.**

## URL

This tab appears for a link file that opens a web address or another location. Change the address in **URL:**.

## Application

This tab appears for application launchers, the files that start a program from the menu or the desktop.

- **Name:**, **Generic name:** and **Comment:** are how the application appears in menus: its name, a description of its kind, such as "Image Viewer", and what it's for.
- **Environment variables:**, **Program:** and **Arguments:** make up the command that starts it. **Browse...** finds the program on your disk.
- **Work path:** The folder the application starts in.
- **Supported file types:** The kinds of files the application can open. **Add...** and **Remove** change the list.

**Advanced Options** opens more settings:

- **Run in terminal:** For programs that work in a terminal. **Do not close when command exits** keeps the terminal open afterwards, so you can read the output.
- **Run as a different user:** Starts the program as the user in **Username:**.
- **Run using dedicated graphics card:** On computers with two graphics cards, starts the program on the more powerful one.
- **Enable launch feedback:** Shows a busy pointer while the program starts.
