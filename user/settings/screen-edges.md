---
title: Screen Edges
description: Trigger actions by pushing the pointer against a screen edge or corner.
source_url: https://invent.kde.org/plasma/kwin-x11/-/blob/master/doc/kwinscreenedges-x11/index.docbook
source_authors: [Mike McBride]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-win 4cf630dd38 (src/kcms/screenedges); read from code, not clicked through"
---

# Screen Edges

Active screen edges let you trigger actions by pushing the pointer against the edge of the screen. Here you set which action happens on each edge and corner.

Click a square with any mouse button and select an action from the menu. A highlighted square has an action attached, and a gray one has none. The actions include **Peek at Desktop**, **Lock Screen**, **Show KRunner**, **Application Launcher**, **Activity Manager**, **Overview**, **Grid**, **Present Windows** and window switching. How many are available depends on the effects turned on in [Desktop Effects](desktop-effects.md).

- **Maximize:** **Windows dragged to top edge** maximizes them.
- **Tile:** **Windows dragged to left or right edge** tiles them, and **Trigger quarter tiling in** sets the outer percentage of the screen that tiles to a quarter.
- **Behavior:** **Remain active when windows are fullscreen**. Turn this off to stop screen edge actions when an application is fullscreen.
- **Switch desktop on edge:** Changes the desktop when you push the pointer against an edge: **Disabled**, **Only when moving windows** or **Always enabled**.
- **Activation delay:** How long the pointer must be pushed against the edge before the action is triggered.
- **Reactivation delay:** How long after an action before the next one can be triggered.
- **Edge barrier:** With several screens, extra distance you have to move the pointer before it crosses to another screen.
- **Corner barrier:** Stops the pointer crossing to another screen at screen corners.

> [!TIP]
> [Window Behavior](window-behavior.md) has snap zones on its Movement page, for moving windows to the screen edges, the center or other windows when they get near them.
