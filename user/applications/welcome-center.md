---
title: Welcome Center
description: The short tour that introduces SonicDE when you first log in.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-welcome-center 30afb72d, Enjoy It! and Network pages rechecked at 3f95336c (README.md, src/qml/ContributionCard.qml, src/main.cpp, src/config.kcfg, src/kded/daemon.cpp, src/release.cpp, src/qml/Main.qml, src/qml/footers/, src/qml/pages/); written from the code, and the Powerful When Needed page and --help run from a staged build on a private X server"
---

# Welcome Center

Welcome Center is a short tour of SonicDE. It opens by itself the first time you log in. To open it again, find **Welcome Center** in your application launcher, or run `plasma-welcome`.

Use **Next** and **Back** to move between pages. **Skip** closes the tour at any time, and **Finish** closes it on the last page.

## The pages

- **Welcome:** Introduces SonicDE, or your distribution if it adds its own text, and can tell you more about both. Sonron, the SonicDE mascot, greets you here, unless your distribution shows its own picture.
- **Access the Internet:** Shows the network widget so you can connect. Once you're connected, it says **You're connected**, and if you connect while this page is showing, the tour moves on to the next page by itself. If network support isn't installed, it says so and asks you to report that to your distribution.
- **Simple by Default:** Explains the desktop, panel, Application Launcher, Task Manager, System Tray, Digital Clock and Peek at Desktop. Click an item in the picture to read about it.
- **Powerful When Needed:** Has cards for features you may want later: **Keyboard Shortcuts**, **Overview**, **KRunner**, **KDE Connect**, **Activities** and **Vaults**. Click a card to read about it.
- **Share Anonymous Usage Information:** Lets you choose how much anonymous usage information to share. You can also change this later in System Settings.
- **Enjoy It!:** Shows a picture of Sonron and has links to learn more about the SonicDE community and to find help, and a card with **Make a donation** and **Get involved**.

Your distribution can add its own pages before the last one.

> **Note:** KDE Connect isn't part of SonicDE. Its page offers to install it, if your distribution provides it.

For more about the features on these cards, see [Keyboard shortcuts](../settings/shortcuts.md), [Overview](../desktop/overview.md), [KRunner](../desktop/krunner.md), [Activities](../settings/activities.md) and [Vaults](vaults.md).

## After an update

After an upgrade to a new major or minor version of SonicDE, or a beta, Welcome Center shows a page about the release when you log in. It doesn't appear for smaller bug-fix updates.

The page can link to the release announcement and load a preview of it, which downloads it from the internet. **Load preview automatically** does that whenever the page appears, except on a metered connection. Turn off **Show after SonicDE is updated** if you don't want this page after future updates.

## Running it from the command line

| Command | What it does |
| --- | --- |
| `plasma-welcome` | Shows the tour. |
| `plasma-welcome --post-update` | Shows the page about the current release. |
| `plasma-welcome --pages <pages>` | Shows only the pages you list, separated by commas, by their internal names. For example, `--pages PowerfulWhenNeeded.qml`. |
| `plasma-welcome --live-environment` | Shows the shorter tour for a live system, with its installer page and without the usage information page. |

## Settings

Welcome Center's settings are in `~/.config/plasma-welcomerc`, in the `[General]` group:

| Key | Default | What it does |
| --- | --- | --- |
| `LastSeenVersion` | Empty | The last version you've seen. While it's empty, the tour opens when you log in. |
| `ShowUpdatePage` | `true` | Whether to show the page about the release after an upgrade. |
| `AutomaticUpdatePreview` | `false` | Whether to load the announcement preview automatically. |
