---
title: TV interface
description: SonicDE's interface for televisions, its settings, and recommended third-party applications.
source_url: https://userbase.kde.org/Plasma_Bigscreen
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-tv-interface (bin/, containments/homescreen/, settingsapp/, uvcviewer/, RELEASE-NOTES.md); the application recommendations come from https://userbase.kde.org/Plasma_Bigscreen/Third_Party_Apps and weren't retested; Flatpak links left out"
---

# TV interface

`sonic-tv-interface` provides SonicDE's interface for televisions, made to be used from the sofa with a TV remote or a game controller. To use it, choose **SonicDE TV** from the list of sessions on the login screen.

> [!NOTE]
> The TV session used to have another name on the login screen. If you used it before upgrading, choose **SonicDE TV** once more.

## Current status

The TV interface runs on X11, like the rest of SonicDE.

## Getting around

The home overlay has buttons for **Search**, **Tasks**, which shows your open applications and can close them all, and **Settings**. Each of these, and the home screen itself, can also have a keyboard shortcut; see [TV settings](tv-settings.md#system).

## On-screen keyboard

When a text field gets focus, for example the search field, the on-screen keyboard opens. That works with a remote or game controller too, so you can type without a physical keyboard.

## Settings

The TV interface has its own settings application, made to be used with a remote or controller. See [TV settings](tv-settings.md).

## UVC Viewer

**UVC Viewer** shows the picture from a USB camera or video capture device on the TV, for example to watch a games console or set-top box through a USB capture device. See [UVC Viewer](applications/uvc-viewer.md).

## Third-party applications

These applications aren't part of SonicDE, but they suit a TV.

### Kodi

An open-source media player and all-in-one entertainment hub for local media. See the [Kodi website](https://kodi.tv/).

### Plex HTPC

[Plex](https://plex.tv) is a streaming platform and media server that can be hosted on a personal server and reached from anywhere. It also has on-demand streaming without a personal server. Plex HTPC is a variant designed for a home media experience.

### Steam

A popular gaming platform and store. Steam's Big Picture mode gives a TV-friendly interface for your games. See the [Steam website](https://store.steampowered.com/).

Big Picture mode reads input directly from the controller, and links the controller's Guide button to the Steam menu. This can cause double actions when you use the controller. Consider suppressing controller input in Steam, and turning off the home overlay link to the Guide button for your controller, in **Settings > Input**.

### VacuumTube

A web wrapper for YouTube's interface for TVs, with several improvements such as an ad blocker and phone casting support. See its [source code](https://github.com/shy1132/VacuumTube).
