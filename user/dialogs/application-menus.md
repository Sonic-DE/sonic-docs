---
title: Common application menus
description: The menu button, Find Action, and the Settings and Help menu items that SonicDE applications share.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-frameworks-xml-gui (src/ui_standards.rc, kxmlguiwindow.cpp, kswitchlanguagedialog_p.cpp, kaboutapplicationdialog.cpp, kabstractaboutdialog_p.cpp, kaboutkdedialog_p.cpp, kbugreport.cpp), sonic-frameworks-settings-ui (src/khamburgermenu.cpp, kcommandbar.cpp, kcommandbarmodel_p.cpp, kcolorschememenu.cpp, kstylemanager.cpp), sonic-frameworks-notification-settings (src/knotifyconfigwidget.cpp, knotifyeventlist.cpp, knotifyconfigactionswidgetbase.ui), sonic-frameworks-settings (src/gui/kstandardshortcut.cpp, kstandardactions_p.h); written from the code, not clicked through"
---

# Common application menus

SonicDE applications share a set of menu items, so they work the same in [Ecco](../applications/ecco.md), [Terminal](../applications/terminal.md) and the others. Most are in the **Settings** and **Help** menus. Not every application has all of them.

## The menu button

Applications that can hide their menu bar, such as Ecco, have a menu button at the right end of the toolbar. Click it, or press F10, to open a menu with the most-used actions and the **Help** menu.

Actions that are only in the menu bar are collected in its **More** submenu, under **More Actions**. **Show Menubar with All Actions** at the top of that submenu brings the menu bar back. You can also show or hide the menu bar with **Show Menubar** (Ctrl+M) in the **Settings** menu.

## Find Action

**Find Action…** (Ctrl+Alt+I), in the **Help** menu, opens a search box over the window that lists all the actions of the application you're in, with their shortcuts. Type part of an action's name to narrow the list, then press Enter or click an action to run it. It's handy when you know what you want to do but not which menu it's in.

The actions you used most recently are listed first. To forget them, run **Clear History**, which is listed under **Command Bar**.

## The Settings menu

### Configure Language

**Configure Language…** sets the language of this one application, different from the rest of the desktop. Choose it in **Primary language:**. **Add Fallback Language** adds another language, used for any text that isn't translated into the one above it. **Remove** takes a fallback language off the list, and **Defaults** goes back to the desktop's language.

A message reminds you that the change takes effect the next time you start the application. To change the language of the whole desktop, see [Changing the desktop language](../tutorials/change-language.md).

### Color Scheme and Application Style

Some applications have a **Color Scheme** menu, to give that application different colors from the rest of the desktop. **Default** follows the [Colors](../settings/colors.md) module. Some also have an **Application Style** menu, which works the same way for the look of buttons and other controls; **Default** follows the [Application Style](../settings/application-style.md) module.

### Configure Keyboard Shortcuts and Configure Toolbars

See [Shortcuts and toolbars in applications](shortcuts-and-toolbars.md).

### Configure Notifications

**Configure Notifications…** lists the events the application can tell you about. The columns are **State**, which shows icons for what happens now, **Title** and **Description**. Select an event to choose what happens:

- **Play a sound:** Plays a sound file. Choose the file in the field beside it, and click the play button to hear it.
- **Show a message in a popup:** Shows a [notification](../settings/notifications.md).

Click **Apply** or **OK** to save. The [Notifications](../settings/notifications.md) module in System Settings has the same settings for every application, along with the desktop-wide ones.

## The Help menu

### Report Bug

**Report Bug…** opens **Submit Bug Report**. It shows the **Application:** you're reporting on, its **Version:** and your **OS:**, so you can include them. The button at the bottom opens the bug tracker in your web browser:

- **Launch Bug Report Wizard** opens the KDE bug tracker's form, with these details filled in. This is the button for applications that haven't set their own bug address.
- **Submit Bug Report** opens the application's own bug reporting page.

SonicDE's own components are tracked in the issue tracker of each project at <https://github.com/Sonic-DE>, as the **About SonicDE** window explains.

### About the application

**About** followed by the application's name shows its version, licence and description. More tabs appear when there's something to show:

- **Components:** The versions of the libraries the application uses, Qt and the platform. **Copy to Clipboard** copies all of this, which is useful in a bug report.
- **Author** or **Authors:** Who wrote it, with buttons to visit their homepage or send an email.
- **Thanks To:** Others who helped.
- **Translation:** The translators for your language.

### About SonicDE

**About SonicDE** has four tabs: **About**, with a short introduction to SonicDE and a link to <https://sonicde.org>; **Report Bugs or Wishes**, which explains where to report problems and suggestions; **Join SonicDE**, about the ways to take part; and **Support SonicDE**, about supporting the project.
