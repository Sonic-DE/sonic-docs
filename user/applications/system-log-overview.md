---
title: System Log overview
description: A short list of what the System Log viewer can do.
source_url: https://userbase.kde.org/KSystemLog
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-system-log d2ff710 (src/modes/); read from code, not clicked through"
---

# System Log overview

![The System Log window](images/overviews/system-log.png)

System Log is a log viewer developed for beginners, who may not know how to find information about their system or where the log files are. The [System Log](system-log.md) page describes it in full.

System Log has the following features:

- Shows all the logs of your system, grouped into general ones (the default system log, authentication, kernel, X.org and so on) and optional services (Apache, CUPS and so on)
- Colors log lines according to their severity
- Tabs, to display several logs at the same time
- Shows new lines automatically as they are logged
- Fast parsing and reading (more than 10,000 lines every 5 seconds)
- Detailed information for each log line
- A quick filter
- Sends a log message to the system by hand
- Saving, copying to the clipboard and printing

It can read these logs on your system: Acpid, Apache, Audit, authentication, Cron, CUPS, daemon, Journald, kernel, Postfix, Samba, system, X.org and X session logs.
