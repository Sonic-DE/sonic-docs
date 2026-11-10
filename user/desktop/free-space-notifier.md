---
title: Free Space Notifier
description: Get a warning when a disk is running out of space.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-workspace (freespacenotifier: module.cpp, freespacenotifier.cpp, freespacenotifier.kcfg, freespacenotifier_prefs_base.ui); written from the code, not clicked through"
---

# Free Space Notifier

The Free Space Notifier is a background service that warns you when a disk is nearly full. It watches every partition you can write to, such as your root partition, your Home folder and mounted drives, but leaves out read-only partitions and cache drives.

When free space gets low, a notification tells you how much is left, for example "Your Home folder is running out of disk space; 150 MiB of space remaining (3%)." It warns you again if the free space then drops to half of what it was at the last warning. The notification goes away once you've freed enough space.

The notification offers these buttons:

- **Open in Filelight:** Shows what takes up the space, if the Filelight disk usage tool is installed. Without it, **Open in File Manager** opens the partition in your file manager instead.
- **Configure Warning…:** Opens the settings described below.

## Settings

The settings dialog has one page, **General**:

- **Enable low disk space warning:** Turns the warnings on or off. It's on by default.
- **Warn when free space is below:** The amount of free space, in MiB, at which you're warned. The default is 200 MiB.
- **And when free space is under:** The share of the partition, in percent, that must be free. The default is 5%.

You're warned only when the free space is below both values.

If you turn the warning off, the service stops and no longer starts with your session. To turn it back on, start **Free Space Notifier** again in the [Background Services](../settings/background-services.md) module.
