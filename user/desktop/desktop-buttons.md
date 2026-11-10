---
title: Peek at Desktop and Minimize All Windows
description: Two panel buttons that get your windows out of the way so you can see the desktop.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-desktop-interface (applets/showdesktop/main.qml, PeekController.qml, MinimizeAllController.qml, applets/minimizeall); written from the code, not clicked through"
---

# Peek at Desktop and Minimize All Windows

Sometimes you need to reach a file or widget on the desktop while windows cover it. Two small widgets help with this. Both are single buttons that you can put on a [panel](panels.md) or the desktop. **Peek at Desktop** is at the right end of the default panel; you can add **Minimize All Windows** yourself.

## Peek at Desktop

Click **Peek at Desktop** to move all windows out of the way, so you can see the desktop. Click it again (the tooltip then says **Stop Peeking at Desktop**) to move the windows back where they were.

The windows aren't minimized: they keep their state and come back together.

## Minimize All Windows

Click **Minimize All Windows** to minimize every window on the current virtual desktop and activity. Click it again (the tooltip then says **Restore Windows**) to bring back the windows it minimized. Windows you've already restored yourself, or closed, are left as they are.

If you switch to one of the windows in the meantime, for example from the [task manager](tasks.md), the button forgets the rest, and the next click minimizes all windows again.

## Using either button

- While a button is active, it shows a highlight so you can see that windows are hidden.
- Drag a file over the button and hold it there for a moment: the button acts as if you clicked it, so you can drop the file on the desktop.
- Right-click either button to use the other action without adding a second widget: the menu has both **Minimize All Windows** and **Peek at Desktop**. Only one of them can be active at a time.
- When the button has keyboard focus, Space or Return clicks it.
