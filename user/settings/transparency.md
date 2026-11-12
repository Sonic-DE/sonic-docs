---
title: Transparency
description: Set how see-through panels, pop-ups, menus and titlebars are, and give chosen applications their own titlebar settings.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-workspace (kcms/transparency, libklookandfeel/klookandfeelmanager.cpp), sonic-frameworks-color-scheme (src/ktoolsarea.h, src/ktoolsarea.cpp), sonic-silver and sonic-breeze (kstyle/breezestyle.cpp); written from the code and checked in a private test session"
---

# Transparency

**System Settings → Colors & Themes → Transparency** gathers every see-through setting in one place:
the desktop, menus and titlebars. Each value is set from **Transparent** to **Opaque**, with a slider and a
percentage box. Open applications and the desktop follow your changes as soon as you click **Apply**.

Some themes draw their own look and don't use these settings. While one of those is selected, its section is
greyed out with a note saying why. Your values are kept, and apply again once you choose a theme that uses
them, even while the page is open.

A [global theme](global-theme.md) can set these values too, as the Silver Apple Pie themes do. Applying a
global theme that sets them replaces your values with the theme's. Applying one that doesn't removes the
earlier theme's values and keeps any you set yourself here.

## Desktop

How see-through the desktop is. These settings need a desktop style that uses them, such as Silver Light and
Silver Dark; other styles keep their own transparency.

- **Use these settings instead of the desktop style's own:** Turns the settings below on. Moving a slider
  turns it on for you.
- **Panels**, **Pop-ups**, **Tooltips** and **Desktop widgets:** How transparent each one is. Pop-ups
  include their top and bottom bars, such as the search field and buttons in the application launcher.
  Desktop widgets are only see-through while the Blur desktop effect is on.

## Menus

**Menus:** How see-through the menus of applications are. Menus are opaque by default. This needs the
Silver or Breeze application style, chosen in [Application Style](application-style.md); other styles draw
opaque menus.

If you set menu transparency in Silver's or Breeze's own settings before, your value was moved here
automatically.

Whether see-through menus are also blurred is set in the blur effect's settings, with **Blur menus**. See
[Forcing transparency and blur](../tutorials/transparency-and-blur.md).

## Titlebars

These settings make the titlebar see-through. They're shared by every window decoration that supports them,
and by the toolbars and menu bars of applications, including modern applications drawn with Qt Quick, so a
window's whole top area looks the same.

Titlebar transparency is off until you change one of these settings and apply it, or load a
[Silver preset](silver-settings.md#presets) that uses it. It needs a window decoration that supports it, such
as Silver. Choosing one without it in [Window Decorations](window-decorations.md), such as Breeze, turns
these settings off; going back to one that supports them turns them on again, as you left them.

- **Active window** and **Inactive window:** How transparent the titlebar is.
- **Always make maximized titlebars opaque.**
- **Blur titlebars that have transparency.**
- **Apply these opacity settings to the entire header area (toolbars and menu bars).**
- **Match the titlebar to the application colour.**

Loading a Silver preset sets these settings for you, and saving a preset records them. If you set titlebar
transparency in Silver's own settings before, those settings were moved here automatically.

### Exceptions

**Exceptions…**, at the top of the page, opens the titlebar exceptions. An exception changes only the titlebar settings, for the
applications it matches.

**Add Exception** adds one. Enter an application name or window class as a regular expression, then check
each setting you want to change for those applications: **Active window opacity:** and
**Inactive window opacity:** with their own percentages, and **Override:** for each of the other settings.
Settings you leave unchecked follow the titlebar settings.

The check box at the start of each exception, **Use this exception**, turns it on and off without deleting
it. **Remove Exception** deletes it.

Exceptions marked **Default** come with SonicDE. You can't change or remove them, only switch them off with
**Use this exception**.
