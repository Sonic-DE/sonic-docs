---
title: File Search
description: Choose which files are indexed for fast searching.
source_url: https://invent.kde.org/plasma/plasma-desktop/-/blob/master/doc/kcontrol/baloo/index.docbook
source_authors: [Vishesh Handa]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-desktop-interface fad996458a (kcms/baloo); read from code, not clicked through"
---

# File Search

This module lets you configure which files are indexed for fast searching. It uses a technology called Baloo to search through files efficiently.

The results are used by KRunner, launcher menus, the Search widget, [Ecco](../applications/ecco.md) and other applications.

## Data to index

- **File names and contents** indexes both.
- **File names only** indexes just the names.
- **Nothing (disable indexing entirely)** turns indexing off. This disables file searching in KRunner and launcher menus, and removes extended metadata display from all applications. You can then delete the saved index data to free the space it uses, but the whole index has to be rebuilt if you turn indexing on again.

**Also index hidden files and folders** includes hidden items. Any file or folder whose name starts with a period (`.`) is hidden by default.

**Pause Indexer** and **Resume Indexer** control indexing that's in progress, and the module shows what's currently being indexed.

## Locations

This is a list of folders that can be indexed. By default only your `$HOME` folder is indexed, and no other folders or drives are.

Removable media is never indexed by default. You can explicitly remove it from the list of excluded folders, and it will then be indexed.

Use the box next to each item to set it to **Indexed** or **Not indexed**, and **Remove entry** to take it off the list.

**Start Indexing a Folder…** and **Stop Indexing a Folder…** let you choose a folder to add to the list.

For more about configuration options, such as adding a drive mounted outside your `$HOME` folder, see [Baloo/Configuration](https://community.kde.org/Baloo/Configuration).
