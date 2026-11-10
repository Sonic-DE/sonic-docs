---
title: Permission and portal dialogs
description: The windows that appear when an application asks to open a file with another app, share your screen, take a screenshot or use other parts of your system.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "xdg-desktop-portal-sonicde ea2e26f8 (data/sonicde.portal, src/desktopportal.cpp, AppChooserDialog.qml, ScreenChooserDialog.qml, screenchooserdialog.cpp, RemoteDesktopDialog.qml, remotedesktopdialog.cpp, ScreenshotDialog.qml, screenshotdialog.cpp, GlobalShortcutsDialog.qml, WallpaperDialog.qml, UsbDialog.qml, InputCaptureDialog.qml, UserInfoDialog.qml, userinfodialog.cpp, DynamicLauncherDialog.qml, dynamiclauncher.cpp); written from the code, not clicked through"
---

# Permission and portal dialogs

Some applications, especially Flatpak and Snap apps, can't reach the rest of your system directly. They ask SonicDE through a service called the desktop portal, and SonicDE shows you a window so you decide. These windows look the same whichever application asks. You can say no to any of them: the application only gets what you approve.

Administrators can approve some requests in advance; see [Portal pre-authorization](../../developer/administration/portal-permissions.md).

## Choose Application

When an application wants to open a file in another application, **Choose Application** lists the applications that can open it, with the default and the last one used marked.

- **Set as default app to open … files:** Remembers your choice for this type of file.
- **Show All Installed Applications:** Lists every application, not only those suggested for this type of file.
- **Choose Other…:** Lets you pick a program yourself, or type a command into the search field.
- **Run in terminal** runs the chosen program in a terminal, and **Do not close when command exits** keeps that terminal open afterwards.

**Choose Other…**, **Run in terminal** and **Do not close when command exits** only appear when the requesting application allows running other programs.

Click **Open** to use the selected application.

## Sharing your screen

When an application, such as a video call, wants to see your screen, **Share screen with …** lists your screens and, under **Windows**, your open windows, with a search field. Choose what to share. When the application can take more than one, select them and click **Share**.

**Allow restoring on future sessions** is ticked by default. It lets the application share the same thing again later without asking.

## Remote Control

When an application wants to see your screen or control your keyboard and mouse, **Remote Control** lists what it's asking for. Click **Approve** to allow it or **Deny** to refuse. If the application asks to remember your answer, **Allow restoring on future sessions** appears too.

## Request Screenshot

When an application asks for a screenshot, **Request Screenshot** lets you choose how it's taken:

- **Capture Mode:** **Area:** **Full Screen**, **Current Screen** or **Active Window**, and a **Delay:** in seconds.
- **Content Options:** **Include cursor pointer** and **Include window borders**.

**Take** takes the picture and shows it, and **Save** gives it to the application.

## Other requests

- **Global Shortcuts Requested:** An application wants to add keyboard shortcuts that work everywhere. The window lists them, and **See Other Shortcuts…** shows the ones that application has already registered.
- **Set Wallpaper:** An application wants to change your desktop background, your lock screen background or both.
- **Access to USB Devices Requested:** An application wants to use USB devices, which are listed.
- **Input Capture Requested:** An application wants to take over your keyboard and mouse input, for example to share them with another computer. **Allow** approves it.
- **Share user info:** An application wants your username, full name and profile picture. **Share** gives them to it.
- **Add Application…** or **Add Web Application…:** An application wants to add a launcher to your application menu. You can change its **Name** and icon with **Edit Info…**, then click **Accept**.
