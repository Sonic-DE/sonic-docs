---
title: Print Queue
description: See what's waiting to print, and pause, cancel or move print jobs.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-print-management 2b6e738c (src/print-queue/qml/Main.qml, src/print-queue/qml/JobView.qml, src/print-queue/qml/NotAvailablePage.qml, src/print-queue/org.kde.plasma.printqueue.desktop, src/libkcups/ProcessRunner.cpp, src/kcm/ui/main.qml, src/plasmoid/PrinterDelegate.qml); written from the code, not clicked through"
---

# Print Queue

The print queue lists the documents, called jobs, that are waiting to print or have printed. It isn't in the application launcher. Open it in one of these ways:

- In System Settings' [Printers](../settings/printers.md) module, click **Open Print Queue** next to a printer.
- In the Printers widget, use **View Print Queue** on a printer.
- Run `plasma-print-queue`, optionally followed by a printer's name.

## Choosing a printer

The sidebar lists your **Printers**, and **Printer Groups** if you have any. Pick one to see its jobs.

At the top of the page:

- **Pause** pauses the printer, so jobs wait in the queue, and **Resume** lets it print again.
- **Configure…** opens the printer in the Printers module.
- **Media Settings…** opens the printer's settings for paper and other print options.

If no printer has been set up, the window says “No printers have been set up” and offers **Set Up a Printer…**. If it can't reach the printing service, it says “Printing services not available” and suggests checking that the CUPS service is running.

## Working with jobs

**Filter Jobs** chooses which jobs are listed: **Active**, **Completed** or **All**. **Show Job Details** adds each job's status, when it was created, processed and completed, and its number of pages; **Hide Job Details** takes them away again.

Each job has the buttons that fit its state:

- **Cancel** stops the job.
- **Hold** keeps it in the queue without printing it, and **Release** lets it print.
- **Reprint** prints a finished job again.
- **Move** sends it to another printer: pick one from **Move to** followed by the printer's name. You can also drag the job onto a printer in the sidebar. This is only possible when you have more than one printer.
- **Authenticate** asks for a user name and password, for printers that need them before they print.

**Cancel All Jobs** cancels every active job of the printer, after you confirm.
