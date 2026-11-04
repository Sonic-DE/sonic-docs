---
title: KNotification
description: Create platform-independent notifications.
source_url: https://develop.kde.org/docs/features/knotification/
source_authors: [Thiago Sueto]
license: CC BY-SA 4.0
license_url: https://creativecommons.org/licenses/by-sa/4.0/
checked_against: sonic-frameworks-notifications (src/knotification.h, knotificationmanager.cpp, knotificationconfiguration.cpp, notify backends), sonic-workspace d0b84fd142 (kcms/notifications, libnotificationmanager), sonic-frameworks-service (KService::noDisplay)
---

# KNotification

[KNotification](/docs/api/knotifications/knotification), in `sonic-frameworks-notifications` (`find_package(KF6Notifications)`, `KF6::Notifications`), creates notifications with the same C++ and QML API everywhere:

- on Linux, including SonicDE, following the [Desktop Notifications specification](https://specifications.freedesktop.org/notification/latest/) (SonicDE's desktop shell shows them)
- on Windows, with [SnoreToast](https://invent.kde.org/libraries/snoretoast)
- on Android, with [NotificationBuilder](https://developer.android.com/develop/ui/views/notifications/build-notification)
- on macOS, with the system's notification center

This page covers the C++ API. The QML API is described in [KNotifications QML types](/docs/api/knotificationsqml/org-kde-notifications-qmlmodule).

## The notifyrc file

To send notifications, your application must provide (and install) an `appname.notifyrc` file listing all its notification events. In SonicDE, it also lets the user control each event, for example mute it or add a sound, in System Settings → Notifications → Configure for Applications….

Install it as `knotifications6/appname.notifyrc` in a [QStandardPaths::GenericDataLocation](https://doc.qt.io/qt-6/qstandardpaths.html#StandardLocation-enum) directory. On Android, the path is `qrc:/knotifications6/`.

`appname` must match [QCoreApplication::applicationName](https://doc.qt.io/qt-6/qcoreapplication.html#applicationName-prop) or be set with [KNotification::setComponentName()](/docs/api/knotifications/knotification#setComponentName); otherwise the notifications aren't shown.

The file has two parts, global information and the individual events:

```ini
[Global]
IconName=myicon
Name=Name of Application
Comment=A brief description of the application
DesktopEntry=org.foo.yourapplication.desktop

[Event/newmail]
Name=New E-Mail
Comment=You got a new email
Action=Sound|Popup

[Event/contactOnline]
Name=Contact Goes Online
Comment=One of your contacts has been connected
Sound=filetoplay.ogg
Action=None
Urgency=Low
```

`IconName=`, `Name=` and `Comment=` work as in desktop entry files. They show where a notification comes from: in the popup, in the notification history and in the System Settings module. Without `Name`, `Comment` is shown instead.

For the notifications to appear in those three places:

- `DesktopEntry=` must match the application's desktop file name (including the extension).
- The desktop file name must be set with [QGuiApplication::setDesktopFileName()](https://doc.qt.io/qt-6/qguiapplication.html#desktopFileName-prop) or with [KAboutData](/docs/api/kcoreaddons/kaboutdata).
- The desktop file must not be hidden: not `NoDisplay=true`, and not limited to other desktops with `OnlyShowIn`/`NotShowIn`.

Each event is a group named `[Event/` + event ID + `]`. You choose the event ID, and pass it to the [KNotification constructor](/docs/api/knotifications/knotification#KNotification).

`Action=` decides whether the notification pops up (`Popup`), plays a sound (`Sound`) or does nothing (`None` or empty). With `Sound`, the event also needs a `Sound=` key. Combine both with `|`.

`Urgency=` decides how the notification is presented: `Low`, `Normal`, `High` or `Critical`, matching the [Urgency enum](/docs/api/knotifications/knotification#Urgency-enum). In SonicDE, critical notifications are shown even in Do Not Disturb mode, and the user can turn popups for low-urgency notifications off (both are settings in System Settings → Notifications, on by default).

With ECM's `KDEInstallDirs`, install the file like this:

```cmake
install(FILES appname.notifyrc  DESTINATION ${KDE_INSTALL_KNOTIFYRCDIR})
```

## Basic use from C++

With the notifyrc file installed, sending a notification is as simple as creating a KNotification, setting its text and other properties, and sending the event:

```cpp
KNotification* notification = new KNotification("eventNameFromNotifyrc");
notification->setText("It just works! 🎉");
notification->sendEvent();
```

## Reacting to the notification being closed

Applications often need to do something when the user closes the notification, its timeout runs out, or the user clicks one of its action buttons. Use the [closed signal](/docs/api/knotifications/knotification#closed):

```cpp
QObject::connect(
    notification, &KNotification::closed,
    [](){
        qInfo() << "Notification closed!";
    });
```

## Reacting to an action

Depending on the system, notifications can have *actions* the user clicks to do something quickly. Add one with `addAction()`, which returns a [KNotificationAction](/docs/api/knotifications/knotificationaction), and connect its [activated signal](/docs/api/knotifications/knotificationaction#activated) to your code.

This example adds an action that brings a QML application's window to the front:

```cpp
KNotification* notification = new KNotification("eventNameFromNotifyrc");
notification->setText("You have a new email!");
KNotificationAction* openAction = notification->addAction("Open application");
QObject::connect(
    openAction, &KNotificationAction::activated,
    [&engine](){
        auto window = qobject_cast<QQuickWindow*>(engine.rootObjects().first());
        window->show();
        window->requestActivate();
        window->raise();
    }
);
notification->sendEvent();
```

## A reply action

Notifications can also let the user type a reply inline, which the application then uses, for example to answer a chat message or an email. Use [KNotificationReplyAction](/docs/api/knotifications/knotificationreplyaction):

```cpp
KNotification* notification = new KNotification("eventNameFromNotifyrc");
notification->setText("Your friend just sent a message!");
auto replyAction = std::make_unique<KNotificationReplyAction>("Reply"); // Button label
replyAction->setPlaceholderText("Reply with...");
QObject::connect(replyAction.get(), &KNotificationReplyAction::replied, [](const QString &text) {
    qInfo() << "You sent the message:" << text;
});
// Needs to be after the QObject::connect call!
notification->setReplyAction(std::move(replyAction));
notification->sendEvent();
```
