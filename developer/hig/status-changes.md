---
title: Communicating status changes
description: Errors, color, notifications, on-screen displays, Task Manager badges and System Tray icons.
source_url: https://develop.kde.org/hig/status_changes/
source_authors: [John Veness, Joshua Goins, Nate Graham, Oliver Schramm, Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: "sonic-silver colors/SilverLight.colors, sonic-workspace libnotificationmanager (critical timeout, job progress), sonic-desktop-interface applets/taskmanager smartlauncherbackend.cpp, sonic-screenies SpectacleCore.cpp, Qt 6.11 documentation (setBadgeNumber)"
---

# Communicating status changes

Minimize unnecessary status messages. Indicate success by visually changing something on the screen related to the task that succeeded, not by sending a message saying “Task completed.” One exception is for long-running tasks that the user may have forgotten about.

## Errors and failures

Strive to prevent error messages by keeping the user from entering an error or failure state in the first place. Only accept data in structured input fields, validate inputs before entry, and automatically recover from internal failures.

See the following table for how to express errors to the user, in decreasing order of preference:

| Message type | When to use |
| --- | --- |
| None; the error condition is made impossible or the software recovers automatically | Always preferred |
| Description of what went wrong with some kind of “Fix it” action | When the “Fix it” action is not universally desirable or has consequences the user must be notified about |
| Description of what went wrong and how the user can proceed | When it's technically infeasible to offer a “Fix it” action |
| Only a description of what went wrong | Never |
| Only technical gibberish | Never ever |
| Silent failure | Never ever ever |

**All error messages must be actionable.** Tell the user in plain language what happened and what they can do to either fix it, or at least move forward somehow. Be explicit and don't assume knowledge of the system's inner workings or support resources! For example, if you expect the user to visit a support forum or submit a bug report, show a link to the appropriate location in the UI displaying the error message.

Ensure that failures originating with third-party software or web services are communicated to the user as such. Never let the user blame your application for a problem that's outside of your control!

## Color

Anything colorful will stand out visually, so use it strategically to attract the user's attention. Don't overdo it; when many UI elements are colorful, the user's attention will be pulled in multiple directions.

- Highlighted list or grid items, checked controls, benign and ignorable text color (blue by default):
  - [Kirigami.Theme.highlightedTextColor](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-theme#highlightedTextColor-attached-prop)
  - [Kirigami.Theme.highlightColor](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-theme#highlightColor-attached-prop)
- Warning or alert text/areas, non-default settings states (orange by default):
  - [Kirigami.Theme.neutralTextColor](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-theme#neutralTextColor-attached-prop)
  - [Kirigami.Theme.neutralBackgroundColor](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-theme#neutralBackgroundColor-attached-prop)
- Error text/areas, dangerous actions (red by default):
  - [Kirigami.Theme.negativeTextColor](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-theme#negativeTextColor-attached-prop)
  - [Kirigami.Theme.negativeBackgroundColor](/docs/api/kirigamiplatform/qml-org-kde-kirigami-platform-theme#negativeBackgroundColor-attached-prop)

Don't rely on color alone to convey meaning or invite action; also use different icons, shapes, or text.

## In-app notifications

Avoid sending system notifications while your application's main window is in the foreground, as they can appear where the user is not looking. Instead use one of the following:

- For ignorable or low-importance messages, use [showPassiveNotification](/docs/api/kirigami/qml-org-kde-kirigami-abstractapplicationwindow#showPassiveNotification-method).
- For messages that should get the user's attention but not interrupt their current task, add a [Kirigami.InlineMessage](../kirigami/inline-messages.md). If the message's scope is specific to the whole page or application, add it to the page header with the [position](/docs/api/kirigami/qml-org-kde-kirigami-inlinemessage#position-prop) property set to `Kirigami.InlineMessage.Position.Header`.

## System notifications

Send a [system notification](/docs/api/knotifications/knotifications-index) when your application is in the background and needs to inform the user about actionable events such as the progress of ongoing jobs, incoming communications from other people, or hardware issues such as running low on battery power.

Give an [urgency level](/docs/api/knotifications/knotification#setUrgency) to each notification, such as Low, Normal, or Critical. Strongly consider not sending Low importance notifications in the first place. Use [setFlags()](/docs/api/knotifications/knotification#setFlags) to give the [Persistent flag](/docs/api/knotifications/knotification#NotificationFlag-enum) to normal-priority notifications that are not critical, but that the user should not miss anyway. Critical notifications always remain visible until dismissed.

Use system notifications sparingly. Excessive notifications drive users crazy.

Don't use system notifications to bug the user about expected and ignorable events. For user-initiated system-level changes made within the desktop itself rather than a windowed application, consider using an [OSD](#on-screen-displays) instead.

Never use notifications to advertise new features or prompt the user to promote the application.

## On-screen displays

Use an on-screen display (OSD) to communicate in a lightweight fashion that a user-initiated system-level action has taken effect, and also to show the new state of the system.

OSDs are useful in either of these situations:

- When knowledge of the new state is important for the user to know.
- When an action that is quick but not instant has completed.

Examples include:

- Volume changes
- Brightness changes
- Connection to a new network or Bluetooth device has succeeded
- Active audio device has been switched in response to a hardware change
- System time zone has been switched in response to traveling somewhere else

Only desktop components should show OSDs; don't show an OSD from a windowed application. Instead, use an [in-app](#in-app-notifications) or [system notification](#system-notifications).

Don't show an OSD for an automatic action not initiated or expected by the user in some way.

## Task Manager badges and progress bars

Task Manager entries can show a number and a progress bar, set through the `com.canonical.Unity.LauncherEntry` D-Bus interface (its `Update` signal, with the `count`, `count-visible`, `progress`, and `progress-visible` properties).

Use the number for a count of unread messages or open tasks. Only include actionable tasks in the number; users want to get rid of it! [QGuiApplication::setBadgeNumber()](https://doc.qt.io/qt-6/qguiapplication.html#setBadgeNumber) sets this number from Qt.

For infrequent yet long-running tasks, also show the completion percentage in the progress bar. Only do this for jobs and tasks the user has explicitly initiated.

## System Tray icons

System Tray icons can be annoying to users, who generally expect applications to quit when their windows are closed. The status monitoring functions typically provided by System Tray icons are better implemented with deeper system integration:

- Task Manager badges can show a count of unread messages.
- Task Manager progress bars and system notifications can show job progress.
- System notifications can display new messages and status changes.

If your application runs primarily as a background service with any UI or window being of secondary importance, consider writing a [desktop widget](../plasma/widget/index.md) instead of a standalone application.

Only implement System Tray icons as a last resort, and always follow these rules:

- Also implement any of the system integrations mentioned above that make sense.
- Make the tray icon opt-in, not opt-out.
- Make the tray icon visible only when there is abnormal status to report and the application is not showing a window, not 100% of the time.
