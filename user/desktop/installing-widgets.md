---
title: Installing widgets
description: Install new widgets from the store, a local file or a terminal.
source_url: https://userbase.kde.org/Plasma/Installing_Plasmoids
source_authors: [KDE UserBase contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-desktop-interface (desktoppackage/contents/explorer/WidgetExplorer.qml, AppletDelegate.qml), sonic-workspace (components/shellprivate/widgetexplorer.cpp), the stage's kpackagetool6 and knsrcfiles/plasmoids.knsrc; read from code, not clicked through"
---

# Installing widgets

Found a new widget, but don't know how to install it? Here's how. These screenshots are older, so the dialogs look different now.

![The Get New Widgets menu](images/install-download-new.png)

## Installing from the store

Right-click the desktop, choose **Enter Edit Mode**, then open **Add Widgets**.

![Adding widgets](images/install-add-widgets.png)

Click **Get New…** at the top of the widget list, then **Download New Plasma Widgets**.

Search for the widget you want and click **Install**.

![Installing a widget](images/install-install.png)

Drag the installed widget to the desktop or a panel as usual.

![Adding the widget to the desktop](images/install-add-to-desktop.png)

## Installing from a local file

Open **Add Widgets** as above, click **Get New…**, then **Install Widget From Local File…**.

![Installing from a local file](images/install-local-file.png)

Select a local file and click **Finish**.

![Selecting a file](images/install-finish.png)

## Installing from a terminal

To install a widget from [Terminal](../applications/terminal.md), type:

```sh
kpackagetool6 -t Plasma/Applet -i widget-file-name.plasmoid
```

## Finding widgets in Add Widgets

The search field at the top of **Add Widgets** finds widgets by name. The button next to it, **All Widgets**, opens a list of **Categories**; choose one to show only the widgets in it, or **All Widgets** to show them all again.

Widgets you've installed recently are marked **New!**. When you select a widget that's already in use, it shows how many copies are running, and **Remove all instances** removes all of them from your desktop and panels.

## Uninstalling widgets

You can uninstall widgets that you installed yourself. Widgets that come with SonicDE can't be uninstalled this way.

1. Open **Add Widgets** and select the widget.
2. Click its **Mark for Uninstallation** button. To change your mind, click it again: it's now called **Cancel Uninstallation**.
3. Click **Uninstall** at the bottom of the list. The button shows how many widgets are marked, for example **Uninstall (2 Widgets)**.
