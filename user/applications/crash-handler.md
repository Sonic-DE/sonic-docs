---
title: Crash Handler
description: What happens when an application crashes, how to report it, and what gets sent.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-dr-robotnik cd082c9da, reporting assistant pages at 723b956a4 (src/main.cpp, src/statusnotifier.cpp, src/settings.kcfg, src/drkonqi.cpp, src/qml/, src/sentry/lib/sentrydsns.cpp, src/bugzillaintegration/reportinterface.cpp, data/gdb_preamble/preamble.py, CMakeLists.txt); written from the code, and the main window opened from a staged build on a private X server. No real crash was handled and no report was sent"
---

# Crash Handler

When an application crashes, the Crash Handler tells you and helps you collect the details developers need to fix it.

## When an application crashes

A notification names the application and says it **Closed Unexpectedly**. Its buttons can include:

- **Report Bug:** Opens the Crash Handler window.
- **Restart App:** Starts the application again.
- **Add Details:** Appears after an automatic report, so you can say what you were doing.

If you don't act on the notification, nothing is reported, unless you've turned on automatic reports.

## The Crash Handler window

The window says that the application has closed unexpectedly, and whether the crash can be reported. It has two main buttons:

- **Send Automatic Report:** Collects the crash details and sends them in the background. Once it's sent, you can describe the crash in **Tell us more about the crash…** and click **Send Message**, or restart the application.
- **See Developer Information:** Shows the technical details.

A report isn't offered if the application gives no address for bug reports, or if it was updated or removed after it started. In that case, log out and back in, so that the update is fully applied.

> **Note:** Automatic reports currently go to KDE's crash tracking system, `crash-reports.kde.org`, and not to SonicDE. For problems specific to SonicDE, report them in the [SonicDE issue trackers](https://github.com/Sonic-DE) instead.

## Developer information

This page shows the backtrace, which is the list of what the program was doing when it crashed. It needs the `gdb` debugger, and it's more useful with your distribution's debug symbols installed.

- **Install Debug Symbols:** Tries to install the missing symbols, if your distribution supports this.
- **Reload:** Generates the backtrace again.
- **Copy:** Copies it to the clipboard.
- **Save:** Saves it to a file.
- **Report on**, followed by the site's name: Starts the [reporting assistant](#the-reporting-assistant) for the application's bug tracker.

If the Crash Handler was started in minimal mode or in safe mode, the reporting assistant is turned off. You can still view, copy and save the crash information, and report it yourself.

## The reporting assistant

The reporting assistant walks you through a bug report for KDE's Bugzilla, one page at a time. Reports are written in English.

1. **Reporting Assistant:** Developers need to be able to contact you about the report, so you have to agree to that with **I Agree to be Contacted** before you can go on. If you don't want to, close the window.
2. **Your Knowledge:** Answers **Yes** or **No** to “Do you remember what you were doing prior to the crash?” and says whether the application crashes again if you repeat the same situation. Then tick the extra information you can give: what you were doing when the application crashed, **Unusual desktop behavior I noticed**, or **Custom settings of the application that may be related**. If your answers aren't enough for a useful report, a **Not Sufficiently Useful** message says so, and you can close the assistant.
3. **Fetching the Backtrace (Automatic Crash Information):** Generates the backtrace and rates it, from “The generated crash information is useful.” to “The generated crash information is not useful.” Installing debug symbols makes it more useful.
4. **Log in to the Bug Tracking System:** Enter the **Email Address:** and **Password:** of your Bugzilla account and click **Login**. **Save login information using the KDE Wallet system** keeps them in [KDE Wallet](kde-wallet.md) for next time.
5. **Enter Details About the Crash:** Write the **Title of the bug report:** and the **Information about the crash:**. The text must reach a minimum length; until then it says “Provide more information”. Choose the **Distribution method:**, how you installed the software, or tick **KDE Platform is compiled from source**. The crash and system information are added for you. Click **Preview Report**.
6. **Bug Report Preview:** Shows the report as it will be sent. To change it, go back to the earlier pages. Click **Submit** to send it.

If sending fails, the assistant says why. **Retry Submission** tries again, and **Save Report to File** saves the whole report so you can submit it yourself. When the report has been sent, **Crash Report Sent** shows the address of the new bug report and offers to restart the application.

## Reporting automatically

After you've sent a report, the window offers two options for the future:

- **Automatically report crashes:** Always sends a report to KDE's crash tracking system with no input from you, and you won't get any more crash notifications. This applies to applications whose bug address is KDE's Bugzilla, which is the default.
- **Automatically download debug symbols to enhance crash reports:** Fetches symbols when they're needed for a report.

Both are off by default. You can also set them in `~/.config/drkonqirc`:

```ini
[DrKonqi]
Sentry=false
DownloadSymbols=false
```

## What contacts the internet

- Opening the Crash Handler window fetches a list of KDE's crash reporting addresses from `autoconfig.kde.org`, and keeps it in `~/.cache/drkonqi/`. This doesn't include details of the crash.
- A report contains the backtrace, along with information about the application and your system.
- If the Python `sentry_sdk` module is installed, the script that helps `gdb` collect a backtrace reports its own errors to `crash-reports.kde.org`.
