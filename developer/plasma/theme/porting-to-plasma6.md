---
title: Porting themes to Plasma 6
description: Common changes old themes need to work on SonicDE.
source_url: https://develop.kde.org/docs/plasma/theme/theme-porting-to-plasma6/
source_authors: [Benjamin Flesch]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-silver global theme metadata, sonic-screenlocker and LockScreenUi.qml (authenticator), SonicWin's scripting registration (WindowThumbnail)"
---

# Porting themes to Plasma 6

SonicDE's desktop is based on Plasma 6, so global themes written for Plasma 5 need several changes to work on it.

## Strict theme packaging

All themes are now handled as a `kpackage`, which means a `metadata.json` file is required. The `metadata.json` file of a global theme needs the JSON key `"KPackageStructure": "Plasma/LookAndFeel"`, otherwise it isn't shown in the "Global Theme" settings.

## No symlinks allowed

Because of the kpackage format, symlinks can no longer be used to load a global theme. Global themes must be in one of the two main folders, `/usr/share/plasma/look-and-feel` and `~/.local/share/plasma/look-and-feel`.

## Renamed QML imports

Various QML imports have been renamed, so existing Plasma 5 theme QML files need to be edited accordingly. The [sonic-workspace](https://github.com/Sonic-DE/sonic-workspace) and [sonic-silver](https://github.com/Sonic-DE/sonic-silver) repositories have current examples.

Notable changes are `QtGraphicalEffects` becoming `Qt5Compat.GraphicalEffects`, and `PlasmaCore.DataSource` becoming `org.kde.plasma.plasma5support.DataSource`, but there are many others.

## Changes for desktop layout scripts

Layout scripts such as `contents/layouts/org.kde.plasma.desktop-layout.js` have not changed very much, and the API mostly stays the same. The version of the desktop scripting API, frequently used in boilerplate such as `var plasma = getApiVersion(1);`, has not changed. The configuration options for panels and widgets have been adapted for new features, though, such as floating panels. See [sonic-silver's layout templates](https://github.com/Sonic-DE/sonic-silver/tree/master/layout-templates) for examples.

## Changes for custom lock screens

Custom lock screens are normally in `contents/lockscreen/LockScreen.qml`. The `authenticator` object provided by the screen locker has changed, to support passwordless authentication. If your theme uses a `Connections { target: authenticator }`, its handlers need adapting: `onPrompt` became `onPromptChanged`, and `onInfoMessage` and `onErrorMessage` became `onInfoMessageChanged` and `onErrorMessageChanged`.

Authentication is now started with `authenticator.startAuthenticating()` instead of `authenticator.tryUnlock()`. The `onPromptForSecret` handler became `onPromptForSecretChanged`. The password is still sent with `authenticator.respond(myPasswordInput.text)`.

## Changes for custom window switchers

If your theme has a window switcher (called a `TabBox` in SonicWin), it is affected by the renamed QML imports too. There are also specific SonicWin renames, such as `KWin.WindowThumbnailItem` becoming `KWin.WindowThumbnail`; see the [sonic-win source repository](https://github.com/Sonic-DE/sonic-win).
