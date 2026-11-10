---
title: Mouse actions
description: Choose what happens when you click or scroll on an empty part of the desktop or a panel.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-workspace (containmentactions/, shell/currentcontainmentactionsmodel.cpp), sonic-desktop-interface (desktoppackage/contents/defaults, desktoppackage/contents/configuration/ConfigurationContainmentActions.qml); written from the code, not clicked through"
---

# Mouse actions

Mouse actions decide what happens when you click or scroll on an empty part of the desktop. To change them, right-click the desktop, choose **Desktop and Wallpaper** and open the **Mouse Actions** page.

Out of the box, the right button opens the desktop's context menu (**Standard Menu**) and the middle button pastes (**Paste**).

## Adding and changing actions

Each line on the page joins a mouse button or scroll direction to an action. To add one, click **Add Action** and then press the mouse button, or scroll the wheel, over that button. Hold Shift, Ctrl, Alt or Meta while you do so to make the action need that key too. The line then shows the combination, for example "Ctrl+Middle-Button" or "Vertical-Scroll".

Pick the action from the list next to it. If the action has settings, a configure button next to it opens them. A remove button deletes the line.

## The actions

- **Application Launcher:** A menu of your applications, in the same categories as the application menu. Its setting **Show applications by name**, on by default, lists applications by name; turn it off to list them by their description instead, such as "Web Browser".
- **Paste:** Pastes the text or files you last selected onto the desktop, at the place you clicked.
- **Standard Menu:** The desktop's context menu. Its settings list the entries of the menu, so you can choose which ones it shows, for example **Show KRunner**, **Open Terminal**, **Lock Screen**, **Show Logout Screen**, **Display Configuration** and **Wallpaper Actions**. **[Other Actions]** stands for the entries that the desktop adds itself, and **[Separator]** for the lines between groups.
- **Switch Activity:** Click for a menu of your activities. Scroll to go to the next or previous activity.
- **Switch Desktop:** Click for a menu of your virtual desktops. Scroll to go to the next or previous one.
- **Switch Window:** Click for a menu of your open windows. Scroll to go through them. Its settings choose how the menu is laid out: **Display all windows in one list**, **Display a submenu for each desktop** or **Display only the current desktop's windows**.
