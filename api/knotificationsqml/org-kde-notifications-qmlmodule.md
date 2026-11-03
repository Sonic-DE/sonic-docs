---
title: "KNotifications QML Types"
description: "Cross-platform Notification Library."
---

# KNotifications QML Types

Cross-platform Notification Library.

Getting started with notifications in QML is quite similar to how this also works in C++:

- Create a KNotificiation instance.
- Customize it to your needs via its properties (labels, icons, actions, priorities, etc).
- Connect to its signals to react to the user interacting with the notification, by triggering its inline actions or by closing it.
- Eventually call its [KNotification::sendEvent](../knotifications/knotification.md#sendEvent)() method to show or re-show the notification.

```qml
import QtQuick
import org.kde.notification

Item {
    Notification {
        id: myNotification
        componentName: "your_component"
        eventId: "your_event"
        title: "Attention!"
        text: "Something important happened."
        iconName: "kde"
        flags: Notification.Persistent
        urgency: Notification.HighUrgency
        onClosed: console.log("Notification closed.")
        actions: [
            NotificationAction {
            label: "Action 1"
            onActivated: log.append("Action 1 activated.")
            },
            NotificationAction {
            label: "Action 2"
            onActivated: log.append("Action 2 activated.")
            },
            NotificationAction {
            label: "Action 3"
            onActivated: log.append("Action 3 activated.")
            }
        ]
    }

    Button {
        onClicked: myNotification.sendEvent()
    }
}
```

## Inline Reply Notifications {#inline-reply-notifications}

Inline reply notifications are also available. There's a small difference to C++ in that the reply action doesn't need to be explicitly managed but is created on demand behind the scenes.

```qml
import QtQuick
import org.kde.notification

Item {
    Notification {
        id: myReplyNotification
        componentName: "plasma_workspace"
        eventId: "notification"
        title: "Chat message from Dr Konqui"
        text: "How are you?"
        replyAction {
            label: "Reply"
            placeholderText: "Reply to Dr Konqi..."
            submitButtonText: "Send Reply"
            submitButtonIconName: "mail-reply-all"
            onReplied: console.log(text)
        }
    }
}
```

## Creating Notifications Dynamically {#creating-notifications-dynamically}

You might have a use-case that requires an arbitrary amount of dynamically created notifications rather than a fixed set of reusable instances. In that case the approach shown above might be too restrictive.

To address this it is possible to configure the auto-delete behavior of [KNotification](../knotifications/knotification.md) objects. When used from C++ it's on by default for compatibility (but can also be switched off), in QML it's off by default and can be switched on when needed as shown in the following example.

```qml
import QtQuick
import org.kde.notification

Item {
    Component {
        id: notificationComponent
        Notification {
            componentName: "plasma_workspace"
            eventId: "notification"
            text: "Temporary notification we can create new instances of."
            autoDelete: true
        }
    }

    Button {
        property int count: 0
        onClicked: {
            var notification = notificationComponent.createObject(parent);
            notification.title = "New Notification " + count;
            n.sendEvent();
            ++count;
        }
    }
}
```

## Further References {#further-references}

There's a more complete and actually runnable pure-QML example in `examples/notificationtester.qml` provided as part of the [KNotifications](../knotifications/knotifications-module.md) source code.

## Contents

- [Notification](qml-org-kde-notifications-notification.md)
- [NotificationAction](qml-org-kde-notifications-notificationaction.md)
- [NotificationConfiguration](qml-org-kde-notifications-notificationconfiguration.md)
- [NotificationPermission](qml-org-kde-notifications-notificationpermission.md): Check or request permissions to show notifications on platforms where that is necessary.
- [NotificationReplyAction](qml-org-kde-notifications-notificationreplyaction.md)
