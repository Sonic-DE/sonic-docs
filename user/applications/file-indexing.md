---
title: File indexing and tags
description: How the file indexer stores tags and ratings, and how to keep them safe.
source_url: https://userbase.kde.org/Baloo
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-file-search (tools/balooctl), sonic-frameworks-file-metadata (usermetadata.cpp); read from code, not clicked through"
---

# File indexing and tags

Baloo is SonicDE's file indexing and file search framework. You control it in System Settings' [File Search](../settings/file-search.md) module, or from a terminal with `balooctl6`.

## Baloo and extended attributes

Applications such as [Ecco](ecco.md) store tags and ratings in extended attributes in the file system, and Baloo indexes these so you can search them. On Linux, to show them, run this in a terminal:

```sh
getfattr -d /path/to/file
```

You may need to install the package that provides `getfattr`, which is usually `attr`.

To search recursively under `/home`:

```sh
getfattr --absolute-names -dR /home 2> /dev/null
```

To open a text file found this way right from [Terminal](terminal.md), you can add a [web search keyword](../settings/web-shortcuts.md) with this URL and give it a name such as `000ffoxopener`:

```text
file:///\{@}
```

You can then right-click the highlighted file name in Terminal and use that keyword to open it in your browser.

Some file systems don't support extended attributes at all, for example FAT32, which most USB flash drives use. Copying files to such a volume loses their tags.

Most command-line utilities, such as `cp`, `tar` and `rsync`, won't copy extended attributes without additional flags either. So unless you only use SonicDE's tools and Linux file systems like ext4, XFS or Btrfs (this isn't a complete list), and you change your backups to include extended attributes, your tags can get lost one way or another.

In some ways, extended attributes are the right place for this information. However, Linux has no core API that would preserve them by default and interpret them consistently, so there are many ways to lose your tags.

## Fixing a search that misses files

If a search doesn't find files you know are there, check for files that aren't indexed yet:

```sh
balooctl6 check
```
