---
title: Pager
description: See and switch between your virtual desktops with the Pager widget.
source_url: https://userbase.kde.org/Plasma/Pager
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-desktop-interface (applets/pager/qml/configGeneral.qml); read from code, not clicked through"
---

# Pager

![The Pager widget](images/pager.png)

The Pager is a widget that helps you organize [virtual desktops](../settings/virtual-desktops.md). It gives a small preview of each virtual desktop, with rectangles that represent the windows on that desktop. Click a preview to switch to that desktop. Hover over a preview to see a list of the applications on it. The context menu (right-click) can add a new virtual desktop or remove the last one.

The Pager also shows the arrangement of the virtual desktops, for example 2x2, 1x4 or 3x4. This arrangement influences the desktop switching animation.

## Configuration

Right-click the Pager and choose **Configure Pager…**.

![The Pager settings](images/pager-general.png)

You can configure:

- **General:** **Show window outlines**, **Show application icons on window outlines**, **Show only current screen** and **Navigation wraps around**.
- **Layout:** How the desktops are arranged.
- **Text display:** No text, the desktop number or the desktop name.
- **Selecting current virtual desktop:** What happens when you click the preview of the active desktop: it does nothing, or shows the desktop.
