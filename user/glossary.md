---
title: Glossary
description: Plain explanations of terms you'll meet when using SonicDE.
source_url: https://userbase.kde.org/Glossary
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "the stage's libraries and binaries for what's shipped; entries for software SonicDE doesn't ship (Akonadi, Flake, KHTML, KJS, Kross, Phonon, ThreadWeaver, WebKit) were left out"
---

# Glossary

This page gives a non-technical reference, with links to more information.

## Activities

Activities are sets of widgets with their own wallpaper. They're a bit like [virtual desktops](#virtual-desktops), but not quite.

For example, you could have a "work" activity with your to-do notes, a Folder View with your work files and a subtle wallpaper. Next to it, a "free time" activity has previews of family photos, a Folder View showing your movie collection and the wallpaper you've loved for years. When work ends, you switch from one to the other.

More information: [Activities](desktop/overview.md#activities)

## Application Launcher

A launch menu in which applications are sorted into functional groups. Right-clicking also lets you add applications to the desktop or a panel, and the search box gets you quickly to less-used applications. There are alternatives, such as the fullscreen Application Dashboard.

More information: [Application Launcher](desktop/kickoff.md)

## Baloo

A file indexing and search service that [Ecco](#ecco) uses to get information about files and allow searches. In a terminal, `balooctl6 status` shows whether an index exists, and `balooctl6 check` and `balooctl6 disable` are helpful too.

More information: [File indexing and tags](applications/file-indexing.md)

## Containment

A top-level grouping of widgets. Each containment manages the layout and configuration data of its widgets independently of other containments. This lets you group widgets according to how you work.

## D-Bus

A messaging system between services, which lets several programs interact. SonicDE is also gradually moving some of its communication to its own framework, `sonic-frameworks-ipc`.

More information: [D-Bus on freedesktop.org](https://www.freedesktop.org/wiki/Software/dbus/)

## Ecco

SonicDE's default file manager. It has a side panel, Places, but you mainly navigate with the breadcrumb trail above the main window. It has advanced features such as split views and tabs. You can mount and unmount USB devices in the side panel.

More information: [Ecco file manager](applications/ecco.md)

## Get Hot New Stuff

*Get Hot New Stuff (GHNS)* is an open standard that makes it easy to download and install extensions for applications. The desktop and many applications and widgets use it, for example to get new themes.

More information: [The KDE Store](https://store.kde.org)

## Home directory

The place on your system where all your files are kept. You can write files outside this folder, but applications are set up to suggest it as the place for your files. It's easiest to keep your things here.

## Info Center

Displays data about your system, such as energy usage and hardware information.

More information: [Info Center](applications/info-center.md)

## Kirigami

A set of components that let developers create applications that look good and work well on mobile platforms as well as the desktop.

## KIO

A framework that provides a single interface for operating on files, whether local or on a remote server. Workers provide support for individual protocols. Some particularly useful ones are `http`, `ftp`, `sftp`, `smb`, `nfs`, `fish` (over SSH), `man`, `tar` and `zip`.

More information: [Network and file protocols](protocols/index.md)

## Kiosk

A framework for restricting what users can do on a SonicDE system, ideal for locked-down environments such as Internet cafés.

More information: [Introduction to Kiosk](../developer/administration/kiosk/introduction.md)

## KPart

An individual component that lets applications share their services with other applications. Ecco's Terminal panel is one example.

## KRunner

The mini command line that you open with the Alt+F2 or Alt+Space keyboard shortcut.

More information: [KRunner](desktop/krunner.md)

## Pager

A small panel widget that shows where windows are on your desktop and, if you have several [virtual desktops](#virtual-desktops), gives an overview of them all.

More information: [Pager](desktop/pager.md)

## Panel

The bar at the edge of the screen that holds widgets, such as the launcher and the task manager.

More information: [Panels](desktop/panels.md)

## Qt

(Pronounced "cute".) A framework for writing cross-platform applications. It forms the underlying library SonicDE is built on.

More information: [The Qt toolkit on Wikipedia](https://en.wikipedia.org/wiki/Qt_(software))

## Solid

Provides a single interface for hardware management. Its backends are pluggable, which helps developers write less code and keep it independent of the platform.

## Sonic Shell

The part of the desktop that you can see. It's the glue between the desktop, panels and widgets.

Sonic Shell replaces the older Plasma shell. The first time it starts, it takes over your panels, desktop widgets, their settings and the shell's keyboard shortcuts from the older shell, if you used it before. Nothing needs to be done by hand, the old settings are left as they were, and settings Sonic Shell already has are never overwritten.

More information: [Desktop overview](desktop/overview.md)

## SonicWin

SonicDE's compositor and window manager. This is where window decorations can be changed and themes applied.

More information: [SonicWin window manager](applications/sonicwin.md)

## System Settings

The one place where you can change and customize many aspects of the desktop and the window manager, such as icon themes, desktop effects and shortcuts.

More information: [System Settings](settings/index.md)

## Virtual desktops

A popular idea in Unix window managers: instead of one screen to put your windows on, you have several. When you switch to another desktop, usually with a [pager](#pager), you only see the windows you started on it or moved to it. A window can also be set to appear on all desktops.

More information: [Virtual Desktops](settings/virtual-desktops.md)

## Widget

A single component on the desktop or a panel. Other common names for the same idea are "applet", "plasmoid" and "gadget".

More information: [Widgets](desktop/widgets.md)

## X server

The basic layer that graphical interfaces like SonicDE are built on. It manages basic mouse and keyboard input, from the local machine as well as remote ones, and provides elementary routines for drawing.

## XMLGUI

A framework for developers for designing the user interface.
