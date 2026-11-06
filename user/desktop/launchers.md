---
title: Application launchers
description: The launchers that come with SonicDE, how to change yours, and how to change its key.
source_url: https://userbase.kde.org/Plasma_application_launchers
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-desktop-interface (applets/kickoff, applets/kicker), sonic-workspace (krunner, shell); read from code, not clicked through"
---

# Application launchers

SonicDE comes with several launchers:

- **[Application Launcher](kickoff.md):** The default launcher, with a click-through interface for finding and starting applications. It has a search facility, so you can type an application's name or description to find it.
- **[Application Dashboard](application-dashboard.md):** A fullscreen launcher with applications sorted into categories.
- **[Application Menu](application-menu.md):** A classic hierarchical menu that's easily customized to give quick access to useful applications and services.
- **[KRunner](krunner.md):** Replaces the "run command" dialog. It blurs the lines between task manager, desktop search, application launcher and command executor, and gives you a quick way to run applications or open documents, among other things.

Others, such as Excalibur and Tiled Menu, are available from the [KDE Store](https://store.kde.org/browse/cat/398/order/latest/).

## How to change the application launcher

To change the launcher, right-click your current one and choose **Show Alternatives…**, then choose the one you want to use.

> **Warning:** Some settings of the launcher you were using might be reset to defaults if you switch back.

![Choosing an alternative launcher](images/launcher-alternatives.png)

If the launcher you want isn't in the list, you need to install it first. See [Installing widgets](installing-widgets.md).

## How do I change which key opens the launcher?

There are two ways. You can right-click your current launcher and choose **Configure Application Launcher…**, go to the **Keyboard Shortcuts** tab, click the button and type the combination you want.

![The launcher's keyboard shortcut setting](images/launcher-shortcut.png)

You can also use System Settings' [Shortcuts](../settings/shortcuts.md) module, and find **Activate Application Launcher Widget** there.

![The launcher's shortcut in System Settings](images/launcher-shortcut-settings.png)

If you ever want to restore the default Meta key, the combination Alt+F1 serves this purpose.

## I can't bind the Meta key to open the launcher any more

This can happen because of the way SonicWin binds keys. See [the section on the Meta key](tips.md#meta-key).
