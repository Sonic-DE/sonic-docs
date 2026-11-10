---
title: Notifications
description: See and manage the messages from your applications, file transfers and Do Not Disturb.
source_authors: [SonicDE contributors]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-workspace (applets/notifications: main.qml, FullRepresentation.qml, globalshortcuts.cpp, components/); written from the code, not clicked through"
---

# Notifications

The Notifications widget shows the messages your applications send you, such as a new email or a finished download, and the progress of file transfers. It sits in the [System Tray](system-tray.md). Its icon shows how many notifications you haven't read yet.

To change which applications may show notifications, and how, use the [Notifications](../settings/notifications.md) module. **Configure Event Notifications and Actions…** in the widget's context menu opens it.

## The notification history

Click the icon to open the history. It lists the notifications you've received, newest first. When an application has sent several, they're grouped together: a button such as **Show 3 More** expands the group (the number tells you how many are hidden), and **Show Fewer** collapses it again. **Close Group** dismisses the whole group.

The button at the top of the history, and **Clear All Notifications** in the context menu, remove the notifications you've already seen from the history.

Some applications let you answer straight from the notification. Click **Reply**, type in the **Type a reply…** field and click **Send**.

## File transfers and other jobs

While an application copies files or does other long work, a notification shows its progress:

- **Details** shows more about the job, such as the files involved and a chart of the transfer speed.
- **Pause** stops the job for a while, and **Resume** continues it.
- **Cancel** stops the job.
- **Minimize** folds the notification up, and **Restore** unfolds it again.

When a file job has finished, **Open** opens the result and **Open Containing Folder** shows it in your file manager.

## Do Not Disturb

Turn on the **Do not disturb** switch at the top of the history to stop notifications from popping up. They're still collected in the history, so you can read them later.

When you turn it on, a menu asks how long it should last: **For 1 hour**, **For 4 hours**, **Until this evening**, **Until tomorrow morning**, **Until Monday** or **Until manually disabled**. The history then shows when it ends automatically.

You can also middle-click the widget's icon to turn Do Not Disturb on or off.

Do Not Disturb also turns on by itself in some situations, and the history says why: for example while an application asks for it (such as during a presentation), while your screens are mirrored, or while a full-screen application has the focus. Which of these apply is set in the [Notifications](../settings/notifications.md) module.

## Keyboard shortcuts

In the [Shortcuts](../settings/shortcuts.md) module you can give global shortcuts to **Toggle do not disturb** and **Clear Notification History**. Neither has one by default. Using them shows a short on-screen message, such as "Notifications Off".
