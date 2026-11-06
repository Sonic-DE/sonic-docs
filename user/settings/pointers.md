---
title: Pointers
description: Choose a pointer theme and size and configure launch feedback.
source_url: https://invent.kde.org/plasma/plasma-workspace/-/blob/master/doc/kcontrol/cursortheme/index.docbook
source_authors: [Mike McBride, Brad Hards, Lauri Watts, Natalie Clarius]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-workspace e4f0096493 (kcms/cursortheme); read from code, not clicked through"
---

# Pointers

This module lets you select a pointer theme and configure an animation for launching applications. Some features may not be available on some systems.

## Pointer themes

![The pointer theme module](images/pointers/main.png)

To use a pointer theme, select it and click **Apply**.

Hover over a theme in the list to reveal its remove button. You can't remove system-installed themes or the active one.

**Get New…** downloads more themes from the Internet, and **Install from File…** installs theme files you've downloaded or otherwise obtained.

![Getting new pointer themes](images/pointers/get-new-stuff.png)

If you'd like to create your own theme, see [Create your own mouse cursor theme](../../developer/additional/cursor-theme.md).

## Pointer size

Some themes let you choose a size. Use the **Size** field to select it.

![Choosing a pointer size](images/pointers/cursor-size.png)

## Launch feedback

Sometimes it's reassuring to know your computer didn't just ignore you and something is happening behind the scenes. **Configure Launch Feedback…** sets the visible feedback when you start an application.

![The Launch Feedback dialog](images/pointers/launch-feedback.png)

![The older Launch Feedback module](images/pointers/launch-feedback-module.png)

- **Pointer feedback:** Attaches an icon to the pointer for a short time while an application launches. Choose **None**, **Static**, **Blinking** or **Bouncing**, which is the default.
- **Task Manager feedback:** **Enable animation** gives a starting application an immediate entry in the task manager, with an animation to show something is happening.
- **Stop animations after:** How long the feedback lasts, 5 seconds by default. Not every application eventually shows a window or a task manager entry: some dock in the system tray, for example. This timeout makes sure you still get feedback in those cases, and that it goes away.
