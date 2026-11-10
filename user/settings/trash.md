---
title: Trash
description: Set when files in the trash are deleted and how much space it can use.
source_url: https://invent.kde.org/network/kio-extras/-/blob/master/doc/kcontrol6/trash/index.docbook
source_authors: [Burkhard Lück]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-frameworks-io-extras 368b21968 (kcms/trash); read from code, not clicked through"
---

# Trash

This module configures the trash. It's under **Workspace** in System Settings.

Each disk or partition you delete files from keeps its own trash. When there's more than one, the module starts with a list of them, shown by where each disk is mounted, such as `/` or `/home`. Select one to see and change its settings below: each trash keeps its own. With only one trash, there's no list.

- **Cleanup:** **Delete files older than** automatically deletes files that have been in the trash longer than the number of days you set. Leave it off to keep them however long they've been there.
- **Size:** **Limit to** caps the trash at a percentage of disk space, with the calculated amount shown beside it. Otherwise it's unlimited.
- **Full trash:** What to do when the limit is reached: **Show a warning**, **Delete oldest files from trash** or **Delete biggest files from trash**.
