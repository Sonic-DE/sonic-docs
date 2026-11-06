---
title: Compositor
description: Turn compositing on or off, and set the animation speed and window thumbnails.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-win 4cf630dd38 (src/kcms/compositing/compositing.ui, main.cpp, kwincompositing_setting.kcfg, src/compositor_x11.cpp); written from the code, not clicked through"
---

# Compositor

Compositing lets [SonicWin](../applications/sonicwin.md), the window manager, use your graphics hardware to draw windows. [Desktop effects](desktop-effects.md), translucent windows and blur all depend on it. This module sets whether compositing runs and how it behaves.

- **Compositing: Enable on startup:** Starts compositing when your session starts. This is on by default.
- **Allow applications to block compositing:** Lets an application ask for compositing to be turned off while its window is open, which improves performance in games, for example. This is on by default. A [window rule](window-rules.md) can overrule it for particular windows.
- **Animation speed:** How fast animations run, from **Very slow** to **Instant**.
- **Keep window thumbnails:** When to keep live thumbnails of windows, which window switchers and window previews can show:
  - **Never**
  - **Only for Shown Windows**, the default
  - **Always**. This interferes with the minimized state of windows, so they may not suspend their work when minimized. The module warns you about this when you choose it.

To turn compositing off or back on for the current session, press Shift+Alt+F12, the **Suspend Compositing** shortcut. This doesn't change **Enable on startup**.

## If OpenGL compositing crashed

If OpenGL compositing has crashed SonicWin in the past, most likely because of a driver bug, the module shows a warning. If you've since moved to a stable driver, you can reset this protection with **Re-enable OpenGL detection**. This may cause an immediate crash if the driver still has the problem.
