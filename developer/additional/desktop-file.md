---
title: Desktop file
description: Let your application show up in the launcher and in application menus.
source_url: https://develop.kde.org/docs/features/additional-features/desktop-file/
source_authors: [Carl Schwan, Mikhail Zolotukhin, Nicolas Fella, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-app-info (KService, vfolder_menu.cpp), sonic-workspace d0b84fd142 (menu/desktop/kf5-unknown.directory), sonic-frameworks-cmake-modules (KDEInstallDirs)
---

# Desktop file

For your application to show up in menus, or to be offered for MIME types in file managers, it needs a `.desktop` file like this:

```ini
[Desktop Entry]
Type=Application
Exec=your-app %u
TryExec=your-app
MimeType=application/x-your-mime-type;
Icon=some-icon
X-DocPath=yourapp/index.html
Terminal=false
Name=Your App
GenericName=Some Generic Name
Comment=Short Description Of Your App
Categories=Qt;KDE;
```

The [Desktop Entry Specification](https://specifications.freedesktop.org/desktop-entry-spec/latest/) describes all the keys.

`Name`, `Type` and `Exec` are essential. `Name` is the application's name. `Type=Application` makes it a program that appears in menus. `Exec` is the command that starts it.

`TryExec` names a command used to check that the application is actually installed: if it can't be found in the `$PATH` (typically when a user wrote their own `.desktop` file and later uninstalled the application), the entry isn't shown in menus.

`Icon` is either the path of an icon shipped with your application or the name of an icon available in the system's icon theme. `Terminal=false` says the application doesn't need to run in a terminal, which is usual for graphical applications.

`X-DocPath` is the path of the application's handbook, used to open its documentation (for example by the Help menu).

Choose good `Categories` so users find your application. Without them, it ends up in the menu's "Lost & Found" category. Categories are separated by semicolons (`;`).

`MimeType` lists the MIME types your application handles, which decides whether it is offered to open a file of that type. A plain text editor, for example, uses `text/plain`, so it appears under "Open With" for text files, and an email application uses `x-scheme-handler/mailto` to handle `mailto:` links. MIME types are separated by semicolons (`;`); the [shared-mime-info repository](https://gitlab.freedesktop.org/xdg/shared-mime-info) has a comprehensive list of the MIME types used on Linux.

## Translations

The example has only English texts. To translate a key, add a `[lang]` suffix to it:

```ini
Name=Your Application
Name[fr]=Ton application
...
GenericName=Some Generic Name
GenericName[fr]=Un nom générique
```

If your project's translations are managed by a translation team, don't translate the `.desktop` file yourself. KDE, for example, has a bot called Scripty that extracts the texts of `.desktop` files into `.po` (gettext) files for its translators, and writes the translations back into the file afterwards.

## Installing the .desktop file

In your `CMakeLists.txt`, install the file with ECM's `KDEInstallDirs`:

```cmake
install(FILES org.example.my-app.desktop DESTINATION ${KDE_INSTALL_APPDIR})
```

Name the file after your application's reverse-domain ID, as here (`org.example.my-app.desktop`), and give the same name to `QGuiApplication::setDesktopFileName()` or `KAboutData`, so that the desktop (task manager, notifications) can match your windows to the file.
