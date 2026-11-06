---
title: Filesystem hierarchy
description: How SonicDE looks up files across directory trees, and which takes precedence.
source_url: https://userbase.kde.org/KDE_System_Administration/KDE_Filesystem_Hierarchy
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-config (core/kconfig.cpp), QStandardPaths use throughout the repos; the source page describes the KDE 4 tree under KDEHOME and KDEDIRS, which the code no longer reads, so this page describes the replacement"
---

# Filesystem hierarchy

SonicDE and its applications store their files in a fixed set of directory trees.

By default, there are two kinds of tree: one at the system level and one at the user level in the user's home folder. As a system administrator, you can add more.

Applications look up files by scanning the trees in order of precedence. When a file is in more than one tree, the file from the first-listed tree takes precedence. Normally, the tree in the user's home folder has the highest precedence, and that's also where changes are written.

Configuration files work slightly differently. If configuration files with the same name are found in several trees, their contents are combined. The order of precedence still matters: when two files define the same configuration key, the file with the highest precedence decides the value.

## Location of the directory trees

The older `KDEHOME`, `KDEROOTHOME` and `KDEDIRS` variables and the `~/.kde` folder are no longer used. The trees now follow the XDG base directory specification, using the `XDG_DATA_HOME`, `XDG_CONFIG_HOME`, `XDG_DATA_DIRS` and `XDG_CONFIG_DIRS` variables. See the [XDG filesystem hierarchy](xdg-filesystem-hierarchy.md) page.

It's possible to specify several system-level trees, which lets groups of users each have a folder of their own. Such an extra tree can contain additional applications, specialized application resources or a specific set of default settings. Since a group-level tree should normally override the system level, list it first in `XDG_DATA_DIRS` or `XDG_CONFIG_DIRS`.
