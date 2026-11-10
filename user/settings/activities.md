---
title: Activities
description: Create and configure activities, separate setups of your desktop.
source_url: https://invent.kde.org/plasma/plasma-desktop/-/blob/master/doc/kcontrol/kcmactivities/index.docbook
source_authors: [Yuri Chornoivan]
license: GFDL 1.2 or later
license_url: https://www.gnu.org/licenses/old-licenses/fdl-1.2.html
checked_against: "sonic-desktop-interface fad996458a (kcms/activities, applets/showActivityManager); read from code, not clicked through"
---

# Activities

This module configures activities. Activities are a way to have multiple desktop setups, each with a different set of widgets.

The module lists your current activities. Hover over an item to reveal the buttons to configure or delete it.

## Configuring an activity

The configure button opens **Activity Settings**, where you can change:

- **Icon:** Shown in the activity switcher. Click the current icon to choose another.
- **Name:** Give your activity a recognizable name.
- **Description:** A free-form description, shown below the name in the activity switcher.
- **While on this activity, allow:**
  - **Tracking file and app use.** Turn this off to stop tracking your actions, such as the recent documents you opened.
  - **Automatically turning off the screen.**
  - **Automatically shutting down or sleeping.**
- **Shortcut for switching:** The first button sets a new shortcut to switch to the activity, and the second removes it.

## Adding and removing activities

**Create New…** below the list opens **Create a New Activity**, which is similar to the settings dialog.

The delete button removes an activity after you confirm.

## Activity widgets

Two widgets help you work with activities from a panel or the desktop:

- The **Activity Pager** shows a preview of each activity. See [Activity Pager](../desktop/pager.md#activity-pager).
- **Show Activity Manager** is a button that opens and closes the activity manager, where you can switch between your activities. Its context menu has **Configure Activities…**, which opens this module.

The settings of **Show Activity Manager**, on its **Appearance** page:

- **Icon:** **Show the current activity icon**, or **Show the generic activity icon**.
- **Title:** **Show the current activity name** shows the name next to the icon. On a vertical panel only the icon is shown.
