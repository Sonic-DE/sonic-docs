---
title: SMART Status
description: Check the health of your hard drives and SSDs, and get warned before one fails.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-disks 1a83753 (src/kcm/kcm_disks.json, src/kcm/ui/main.qml, ReportPage.qml, src/smartnotifier.cpp, src/helper.cpp); written from the code, not clicked through"
---

# SMART Status

Most hard drives and SSDs keep track of their own health using a system called S.M.A.R.T. SonicDE checks it in the background and warns you when a drive reports problems, so you have time to back up your data.

The checks use the `smartctl` program from the smartmontools package, which your distribution provides.

## Warnings

When a drive reports that it's failing, a **Storage Device Problems** notification says the drive is likely to fail soon. Back up your data and replace the drive as soon as you can. **Manage** in the notification opens the SMART Status page.

Early signs of trouble that aren't a failure yet don't cause a notification. They only show on the SMART Status page.

## The SMART Status page

The page is in [Info Center](info-center.md), under **Devices**. It lists each drive that supports S.M.A.R.T., by name and device path, with its state:

- **This device appears to be working as expected.**
- Early signs of malfunction, with a list of what was found. The drive isn't reporting a failure yet, but it's worth backing up your data and contacting the manufacturer, or replacing the drive to be safe.
- The drive's SMART system is reporting problems, which may mean it's about to fail. Back up your data and replace the drive as soon as possible.

Each drive has these buttons:

- **Ignore:** Stops warnings for this drive, for example for an old drive you know about. **Monitor** turns them back on.
- **Show Details:** Shows the drive's full SMART report. **Copy to Clipboard** copies it, for example to include in a support request.

At the top of the page, **Open Partition Manager** starts [Partition Manager](partition-manager.md) and **Perform Backup** starts the backup tool, when they're installed.

If the page says **Unable to obtain data. KDED is not running.**, the background service that checks the drives isn't running. If it says **No S.M.A.R.T. devices found.**, none of your drives report S.M.A.R.T. data.
