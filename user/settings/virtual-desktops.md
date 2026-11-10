---
title: Virtual Desktops
description: Add and arrange virtual desktops and choose how switching works.
source_url: https://invent.kde.org/plasma/kwin-x11/-/blob/master/doc/desktop-x11/index.docbook
source_authors: [Mike McBride, Jost Schenck]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-win a4e76b52c5 (src/kcms/desktop); read from code, not clicked through"
---

# Virtual Desktops

You can have several virtual desktops, each with its own windows.

Hover over a desktop in the list to reveal its **Rename** and **Remove** buttons.

**Add Desktop** adds a new one to the list.

**Rows** sets the number of rows the desktops are arranged in, which the Pager widget on your panel follows.

## Options

- **Navigation wraps around:** Moving past the edge of the desktops with the keyboard or a screen edge takes you to the opposite edge.
- **Show animation when switching:** Choose an animation from the list, or uncheck this to turn animations off. If the animation has settings, the button next to the list opens them, and the button after it shows information about the animation, such as its author. This is the same choice as **Virtual desktop switching:** in the [Animations](animations.md) module.
- **Show on-screen display when switching:** Shows the desktop's name when you switch. The box next to it sets how long the display stays on the screen, in milliseconds. The default is 1000 ms.
- **Show desktop layout indicators:** Also shows a small preview of the desktop layout, with the selected desktop indicated.

Scrolling the mouse wheel over the [Pager](../desktop/pager.md) widget changes to the next virtual desktop in the direction you scrolled. Scrolling over an empty part of the desktop does the same only if you add the **Switch Desktop** action for scrolling on the Mouse Actions page of the desktop's settings, which you open from its context menu. See [Mouse actions](../desktop/mouse-actions.md).
