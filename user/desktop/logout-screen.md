---
title: Logout screen
description: The screen that asks whether to log out, restart, shut down or put the computer to sleep.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-silver (look-and-feel/org.kde.silver.desktop/contents/logout/Logout.qml), sonic-workspace (startkde/session-shortcuts/main.cpp, containmentactions/contextmenu/menu.cpp); written from the code, not clicked through"
---

# Logout screen

The logout screen lets you choose how to leave your session. It comes with your global theme. With the Silver themes, it covers the desktop with a half-transparent layer in the theme's background color, so the buttons stand out while the desktop stays faintly visible behind them.

## Opening it

- Press Ctrl+Alt+Del, the default shortcut for **Show Logout Screen**. You can change it in the [Shortcuts](../settings/shortcuts.md) module.
- Choose **Show Logout Screen** from the desktop's context menu, if it's turned on there (see [Mouse actions](mouse-actions.md)).
- Use the **Show logout screen** button of the [Lock/Logout](lock-logout.md) widget.

## The buttons

When you open the screen to choose freely, it offers **Sleep**, **Hibernate**, **Restart**, **Shut Down** and **Log Out**, as far as your computer supports them, and **Cancel**. Press Esc to cancel too.

When you open it for one particular action, such as restarting, it shows only that action, as **Restart Now**, **Shut Down Now** or **Log Out Now**, and **Cancel**. A countdown then carries out the action by itself after 30 seconds, unless you click **Cancel**.

If updates are waiting to be installed, the restart and shut-down buttons read **Install Updates and Restart** and **Install Updates and Shut Down**, and extra buttons let you restart or shut down without installing them.

The screen also tells you when it matters:

- When other users are logged in, it warns that they may lose work if the computer is shut down or restarted.
- When the computer is set to start into its firmware settings or the boot loader menu, or into a particular boot entry, at the next restart, it says so.

## Skipping it

If you'd rather log out, restart or shut down straight away, clear **Ask for confirmation:** **On shutdown, restart, and logout** in the [Session](../settings/session.md) module.
