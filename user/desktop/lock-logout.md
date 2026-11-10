---
title: Lock/Logout
description: Buttons for locking the screen, logging out, shutting down and more, on your desktop or panel.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-workspace (applets/lock_logout: data.js, ConfigGeneral.qml, main.xml); written from the code, not clicked through"
---

# Lock/Logout

The Lock/Logout widget puts buttons for leaving or pausing your session on the desktop or in a panel. Hover over a button to see what it does.

Out of the box it shows two buttons: **Lock** and **Show logout screen**.

## Settings

The **General** page of the widget's settings lists every button the widget can show. Check the ones you want:

- **Lock:** Locks the screen.
- **Switch user…:** Starts a parallel session as a different user.
- **Shut down:** Turns off the computer.
- **Restart:** Restarts the computer.
- **Log out:** Ends the session.
- **Show logout screen:** Opens the [logout screen](logout-screen.md), where you can choose to log out, turn off or restart the computer.
- **Sleep:** Suspends the computer to RAM.
- **Hibernate:** Suspends the computer to disk.

Drag a row by its handle to change the order of the buttons. At least one button must stay checked. Actions your system can't do, for example hibernating on a computer that doesn't support it, are marked **Unavailable** and can't be checked.
