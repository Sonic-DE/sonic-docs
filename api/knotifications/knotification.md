---
title: "KNotification Class"
description: "KNotification is the main class for creating notifications."
---

# KNotification Class

[KNotification](knotification.md) is the main class for creating notifications. [More...](#details)

- **Header:** `#include <KNotification>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Notifications)`  
  `target_link_libraries(mytarget PRIVATE KF6::Notifications)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](knotification-members.md)

## Public Types

- [enum KNotification::NotificationFlag](#NotificationFlag-enum)
- [enum KNotification::StandardEvent](#StandardEvent-enum)
- [enum KNotification::Urgency](#Urgency-enum)

## Properties

- [autoDelete : bool](#autoDelete-prop)
- [componentName : QString](#componentName-prop)
- [eventId : QString](#eventId-prop)
- [flags : NotificationFlags](#flags-prop)
- [hints : QVariantMap](#hints-prop)
- [iconName : QString](#iconName-prop)
- [text : QString](#text-prop)
- [title : QString](#title-prop)
- [urgency : Urgency](#urgency-prop)
- [urls : QList\<QUrl\>](#urls-prop)
- [\[read-only\] xdgActivationToken : QString](#xdgActivationToken-prop)

## Public Functions

- [KNotification(const QString &eventId, KNotification::NotificationFlags flags = CloseOnTimeout, QObject \*parent = nullptr)](#KNotification)
- [KNotificationAction \*addAction(const QString &label)](#addAction) (since 6.0)
- [KNotificationAction \*addDefaultAction(const QString &label)](#addDefaultAction) (since 6.0)
- [void clearActions()](#clearActions) (since 6.0)
- [QString componentName() const](#componentName)
- [KNotificationAction \*defaultAction() const](#defaultAction) (since 6.0)
- [QString eventId() const](#eventId)
- [KNotification::NotificationFlags flags() const](#flags)
- [QString iconName() const](#iconName)
- [bool isAutoDelete() const](#isAutoDelete)
- [QPixmap pixmap() const](#pixmap)
- [KNotificationReplyAction \*replyAction() const](#replyAction)
- [void setAutoDelete(bool autoDelete)](#setAutoDelete)
- [void setComponentName(const QString &componentName)](#setComponentName)
- [void setEventId(const QString &eventId)](#setEventId)
- [void setFlags(const KNotification::NotificationFlags &flags)](#setFlags)
- [void setIconName(const QString &icon)](#setIconName)
- [void setPixmap(const QPixmap &pix)](#setPixmap)
- [void setReplyAction(std::unique\_ptr\<KNotificationReplyAction\> replyAction)](#setReplyAction)
- [void setText(const QString &text)](#setText)
- [void setTitle(const QString &title)](#setTitle)
- [void setUrgency(KNotification::Urgency urgency)](#setUrgency)
- [void setUrls(const QList\<QUrl\> &urls)](#setUrls)
- [void setWindow(QWindow \*window)](#setWindow) (since 6.0)
- [QString text() const](#text)
- [QString title() const](#title)
- [KNotification::Urgency urgency() const](#urgency)
- [QList\<QUrl\> urls() const](#urls)
- [QWindow \*window() const](#window) (since 6.0)
- [QString xdgActivationToken() const](#xdgActivationToken)

## Public Slots

- [void close()](#close)
- [QVariantMap hints() const](#hints)
- [void sendEvent()](#sendEvent)
- [void setHint(const QString &hint, const QVariant &value)](#setHint)
- [void setHints(const QVariantMap &hints)](#setHints)

## Signals

- [void actionsChanged()](#actionsChanged)
- [void autoDeleteChanged()](#autoDeleteChanged)
- [void closed()](#closed)
- [void componentNameChanged()](#componentNameChanged)
- [void defaultActionChanged()](#defaultActionChanged)
- [void eventIdChanged()](#eventIdChanged)
- [void flagsChanged()](#flagsChanged)
- [void hintsChanged()](#hintsChanged)
- [void iconNameChanged()](#iconNameChanged)
- [void ignored()](#ignored)
- [void textChanged()](#textChanged)
- [void titleChanged()](#titleChanged)
- [void urgencyChanged()](#urgencyChanged)
- [void urlsChanged()](#urlsChanged)
- [void xdgActivationTokenChanged()](#xdgActivationTokenChanged)

## Static Public Members

- [void beep(const QString &reason = QString())](#beep)
- [KNotification \*event(const QString &eventId, const QString &title, const QString &text, const QPixmap &pixmap = QPixmap(), const KNotification::NotificationFlags &flags = CloseOnTimeout, const QString &componentName = QString())](#event)
- [KNotification \*event(KNotification::StandardEvent eventId, const QString &text = QString(), const QPixmap &pixmap = QPixmap(), const KNotification::NotificationFlags &flags = CloseOnTimeout)](#event-1)
- [KNotification \*event(KNotification::StandardEvent eventId, const QString &title, const QString &text, const KNotification::NotificationFlags &flags = CloseOnTimeout)](#event-2)
- [KNotification \*event(KNotification::StandardEvent eventId, const QString &title, const QString &text, const QPixmap &pixmap, const KNotification::NotificationFlags &flags = CloseOnTimeout)](#event-3)
- [KNotification \*event(KNotification::StandardEvent eventId, const QString &title, const QString &text, const QString &iconName, const KNotification::NotificationFlags &flags = CloseOnTimeout)](#event-4)
- [KNotification \*event(const QString &eventId, const QString &text = QString(), const QPixmap &pixmap = QPixmap(), const KNotification::NotificationFlags &flags = CloseOnTimeout, const QString &componentName = QString())](#event-5)
- [KNotification \*event(const QString &eventId, const QString &title, const QString &text, const QString &iconName, const KNotification::NotificationFlags &flags = CloseOnTimeout, const QString &componentName = QString())](#event-6)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum KNotification::NotificationFlag {#NotificationFlag-enum}

**flags KNotification::NotificationFlags**

| Constant | Value | Description |
| --- | --- | --- |
| `KNotification::CloseOnTimeout` | `0x00` | The notification will be automatically closed after a timeout. (this is the default) |
| `KNotification::Persistent` | `0x02` | The notification will NOT be automatically closed after a timeout. You will have to track the notification, and close it with the close function manually when the event is done, otherwise there will be a memory leak. |
| `KNotification::LoopSound` | `0x08` | The audio plugin will loop the sound until the notification is closed. |
| `KNotification::SkipGrouping (since Qt 5.18)` | `0x10` | Sends a hint to Plasma to skip grouping for this notification. |
| `KNotification::CloseWhenWindowActivated (since Qt 6.0)` | `0x20` | The notification will be automatically closed if the [window](knotification.md#window)() becomes activated. You need to set a window using [setWindow](knotification.md#setWindow)(). |
| `KNotification::DefaultEvent` | `0xF000` | The event is a standard kde event, and not an event of the application. |

The `NotificationFlags` type is a typedef for `QFlags<NotificationFlag>. `It stores an OR combination of `NotificationFlag` values.

### enum KNotification::StandardEvent {#StandardEvent-enum}

Default events you can use in the event function

| Constant |   |
| --- | --- |
| `KNotification::Notification` | `0` |
| `KNotification::Warning` | `1` |
| `KNotification::Error` | `2` |
| `KNotification::Catastrophe` | `3` |

### enum KNotification::Urgency {#Urgency-enum}

The urgency of a notification.

| Constant |   |
| --- | --- |
| `KNotification::DefaultUrgency` | `-1` |
| `KNotification::LowUrgency` | `10` |
| `KNotification::NormalUrgency` | `50` |
| `KNotification::HighUrgency` | `70` |
| `KNotification::CriticalUrgency` | `90` |

*See also* [setUrgency](knotification.md#setUrgency)

## Property Documentation {#property-documentation}

### autoDelete : bool {#autoDelete-prop}

**Access functions:**

- `bool` **[isAutoDelete](knotification.md#isAutoDelete)**() const
- `void` **[setAutoDelete](knotification.md#setAutoDelete)**(`bool` *autoDelete*)

**Notifier signal:**

- `void` **[autoDeleteChanged](knotification.md#autoDeleteChanged)**()

### componentName : QString {#componentName-prop}

**Access functions:**

- `QString` **[componentName](knotification.md#componentName)**() const
- `void` **[setComponentName](knotification.md#setComponentName)**(const `QString` &*componentName*)

**Notifier signal:**

- `void` **[componentNameChanged](knotification.md#componentNameChanged)**()

### eventId : QString {#eventId-prop}

**Access functions:**

- `QString` **[eventId](knotification.md#eventId)**() const
- `void` **[setEventId](knotification.md#setEventId)**(const `QString` &*eventId*)

**Notifier signal:**

- `void` **[eventIdChanged](knotification.md#eventIdChanged)**()

### flags : NotificationFlags {#flags-prop}

**Access functions:**

- `KNotification::NotificationFlags` **[flags](knotification.md#flags)**() const
- `void` **[setFlags](knotification.md#setFlags)**(const `KNotification::NotificationFlags` &*flags*)

**Notifier signal:**

- `void` **[flagsChanged](knotification.md#flagsChanged)**()

### hints : QVariantMap {#hints-prop}

**Access functions:**

- `QVariantMap` **[hints](knotification.md#hints)**() const
- `void` **[setHints](knotification.md#setHints)**(const `QVariantMap` &*hints*)

**Notifier signal:**

- `void` **[hintsChanged](knotification.md#hintsChanged)**()

### iconName : QString {#iconName-prop}

**Access functions:**

- `QString` **[iconName](knotification.md#iconName)**() const
- `void` **[setIconName](knotification.md#setIconName)**(const `QString` &*icon*)

**Notifier signal:**

- `void` **[iconNameChanged](knotification.md#iconNameChanged)**()

### text : QString {#text-prop}

**Access functions:**

- `QString` **[text](knotification.md#text)**() const
- `void` **[setText](knotification.md#setText)**(const `QString` &*text*)

**Notifier signal:**

- `void` **[textChanged](knotification.md#textChanged)**()

### title : QString {#title-prop}

**Access functions:**

- `QString` **[title](knotification.md#title)**() const
- `void` **[setTitle](knotification.md#setTitle)**(const `QString` &*title*)

**Notifier signal:**

- `void` **[titleChanged](knotification.md#titleChanged)**()

### urgency : Urgency {#urgency-prop}

**Access functions:**

- `KNotification::Urgency` **[urgency](knotification.md#urgency)**() const
- `void` **[setUrgency](knotification.md#setUrgency)**(`KNotification::Urgency` *urgency*)

**Notifier signal:**

- `void` **[urgencyChanged](knotification.md#urgencyChanged)**()

### urls : QList\<QUrl\> {#urls-prop}

**Access functions:**

- `QList`\<`QUrl`\> **[urls](knotification.md#urls)**() const
- `void` **[setUrls](knotification.md#setUrls)**(const `QList`\<`QUrl`\> &*urls*)

**Notifier signal:**

- `void` **[urlsChanged](knotification.md#urlsChanged)**()

### \[read-only\] xdgActivationToken : QString {#xdgActivationToken-prop}

**Access functions:**

- `QString` **[xdgActivationToken](knotification.md#xdgActivationToken)**() const

**Notifier signal:**

- `void` **[xdgActivationTokenChanged](knotification.md#xdgActivationTokenChanged)**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KNotification::KNotification(const QString &*eventId*, KNotification::NotificationFlags *flags* = CloseOnTimeout, QObject \**parent* = nullptr) {#KNotification}

Create a new notification.

You have to use [sendEvent](knotification.md#sendEvent) to show the notification.

The pointer is automatically deleted when the event is closed.

`eventId` is the name of the event

`flags` is a bitmask of [NotificationFlag](knotification.md#NotificationFlag-enum)

`parent` parent object

### \[signal\] void KNotification::actionsChanged() {#actionsChanged}

Emitted when actions changed.

### \[since 6.0\] KNotificationAction \*KNotification::addAction(const QString &*label*) {#addAction}

Add an action to the notification.

The visual representation of actions depends on the notification server.

`label` the user-visible label of the action

This function was introduced in Qt 6.0.

*See also* [KNotificationAction](knotificationaction.md)

### \[since 6.0\] KNotificationAction \*KNotification::addDefaultAction(const QString &*label*) {#addDefaultAction}

Add a default action that will be triggered when the notification is activated (typically, by clicking on the notification popup). The default action typically raises a window belonging to the application that sent it.

The string will be used as a label for the action, so ideally it should be wrapped in i18n() or [tr](https://doc.qt.io/qt-6/qobject.html#tr)() calls.

The visual representation of actions depends on the notification server. In Plasma and Gnome desktops, the actions are performed by clicking on the notification popup, and the label is not presented to the user.

Calling this overrides the current default action

This function was introduced in Qt 6.0.

### \[signal\] void KNotification::autoDeleteChanged() {#autoDeleteChanged}

Emitted when [autoDelete](knotification.md#autoDelete-prop) changed.

> **Note:** Notifier signal for property [autoDelete](knotification.md#autoDelete-prop).

### \[static\] void KNotification::beep(const QString &*reason* = QString()) {#beep}

This is a simple substitution for QApplication::beep()

`reason` a short text explaining what has happened (may be empty)

### \[since 6.0\] void KNotification::clearActions() {#clearActions}

Removes all actions previously added by [addAction](knotification.md#addAction)() from the notification.

This function was introduced in Qt 6.0.

*See also* [addAction](knotification.md#addAction)

### \[slot\] void KNotification::close() {#close}

Close the notification without activating it.

This will delete the notification.

### \[signal\] void KNotification::closed() {#closed}

Emitted when the notification is closed.

Can be closed either by the user clicking the close button, the timeout running out or when an action was triggered.

### QString KNotification::componentName() const {#componentName}

Returns the component name used to determine the location of the configuration file.

> **Note:** Getter function for property [componentName](knotification.md#componentName-prop).

*See also* [setComponentName](knotification.md#setComponentName)()

### \[signal\] void KNotification::componentNameChanged() {#componentNameChanged}

Emitted when [componentName](knotification.md#componentName) changed.

> **Note:** Notifier signal for property [componentName](knotification.md#componentName-prop).

### \[since 6.0\] KNotificationAction \*KNotification::defaultAction() const {#defaultAction}

Returns the default action, or nullptr if none is set

This function was introduced in Qt 6.0.

### \[signal\] void KNotification::defaultActionChanged() {#defaultActionChanged}

Emitted when [defaultAction](knotification.md#defaultAction) changed.

### \[static\] KNotification \*KNotification::event(const QString &*eventId*, const QString &*title*, const QString &*text*, const QPixmap &*pixmap* = QPixmap(), const KNotification::NotificationFlags &*flags* = CloseOnTimeout, const QString &*componentName* = QString()) {#event}

Emit an event

This method creates the [KNotification](knotification.md), setting every parameter, and fire the event. You don't need to call [sendEvent](knotification.md#sendEvent)

A popup may be displayed or a sound may be played, depending the config.

Returns a [KNotification](knotification.md) . You may use that pointer to connect some signals or slot. the pointer is automatically deleted when the event is closed.

`eventId` is the name of the event

`title` is title of the notification to show in the popup.

`text` is the text of the notification to show in the popup.

`pixmap` is a picture which may be shown in the popup.

`flags` is a bitmask of [NotificationFlag](knotification.md#NotificationFlag-enum)

`componentName` used to determine the location of the config file. by default, appname is used

### \[static\] KNotification \*KNotification::event(KNotification::StandardEvent *eventId*, const QString &*text* = QString(), const QPixmap &*pixmap* = QPixmap(), const KNotification::NotificationFlags &*flags* = CloseOnTimeout) {#event-1}

Emit a standard event

This will emit a standard event

`eventId` is the name of the event

`text` is the text of the notification to show in the popup

`pixmap` is a picture which may be shown in the popup

`flags` is a bitmask of [NotificationFlag](knotification.md#NotificationFlag-enum)

This is an overloaded function.

### \[static\] KNotification \*KNotification::event(KNotification::StandardEvent *eventId*, const QString &*title*, const QString &*text*, const KNotification::NotificationFlags &*flags* = CloseOnTimeout) {#event-2}

Emit a standard event

This will emit a standard event with its standard icon

`eventId` the type of the standard (not app-defined) event

`title` is title of the notification to show in the popup.

`text` is the text of the notification to show in the popup

`flags` is a bitmask of [NotificationFlag](knotification.md#NotificationFlag-enum)

This is an overloaded function.

### \[static\] KNotification \*KNotification::event(KNotification::StandardEvent *eventId*, const QString &*title*, const QString &*text*, const QPixmap &*pixmap*, const KNotification::NotificationFlags &*flags* = CloseOnTimeout) {#event-3}

Emit a standard event

This will emit a standard event

`eventId` is the name of the event

`title` is title of the notification to show in the popup.

`text` is the text of the notification to show in the popup

`pixmap` is a picture which may be shown in the popup

`flags` is a bitmask of [NotificationFlag](knotification.md#NotificationFlag-enum)

This is an overloaded function.

### \[static\] KNotification \*KNotification::event(KNotification::StandardEvent *eventId*, const QString &*title*, const QString &*text*, const QString &*iconName*, const KNotification::NotificationFlags &*flags* = CloseOnTimeout) {#event-4}

Emit a standard event with the possibility of setting an icon by icon name

This will emit a standard event with a custom icon

`eventId` the type of the standard (not app-defined) event

`title` is title of the notification to show in the popup.

`text` is the text of the notification to show in the popup

`iconName` a Freedesktop compatible icon name to be shown in the popup

`flags` is a bitmask of [NotificationFlag](knotification.md#NotificationFlag-enum)

This is an overloaded function.

### \[static\] KNotification \*KNotification::event(const QString &*eventId*, const QString &*text* = QString(), const QPixmap &*pixmap* = QPixmap(), const KNotification::NotificationFlags &*flags* = CloseOnTimeout, const QString &*componentName* = QString()) {#event-5}

Emit a standard event

This will emit a standard event

`eventId` is the name of the event

`text` is the text of the notification to show in the popup.

`pixmap` is a picture which may be shown in the popup.

`flags` is a bitmask of [NotificationFlag](knotification.md#NotificationFlag-enum)

`componentName` used to determine the location of the config file. by default, plasma\_workspace is used

This is an overloaded function.

### \[static\] KNotification \*KNotification::event(const QString &*eventId*, const QString &*title*, const QString &*text*, const QString &*iconName*, const KNotification::NotificationFlags &*flags* = CloseOnTimeout, const QString &*componentName* = QString()) {#event-6}

Emit a standard event with the possibility of setting an icon by icon name

This will emit a standard event

`eventId` is the name of the event

`title` is title of the notification to show in the popup.

`text` is the text of the notification to show in the popup

`iconName` a Freedesktop compatible icon name to be shown in the popup

`flags` is a bitmask of [NotificationFlag](knotification.md#NotificationFlag-enum)

`componentName` used to determine the location of the config file. by default, plasma\_workspace is used

This is an overloaded function.

### QString KNotification::eventId() const {#eventId}

Returns the name of the event

> **Note:** Getter function for property [eventId](knotification.md#eventId-prop).

*See also* [setEventId](knotification.md#setEventId)()

### \[signal\] void KNotification::eventIdChanged() {#eventIdChanged}

Emitted when [eventId](knotification.md#eventId) changed.

> **Note:** Notifier signal for property [eventId](knotification.md#eventId-prop).

### KNotification::NotificationFlags KNotification::flags() const {#flags}

Returns the notification flags.

> **Note:** Getter function for property [flags](knotification.md#flags-prop).

*See also* [setFlags](knotification.md#setFlags)()

### \[signal\] void KNotification::flagsChanged() {#flagsChanged}

Emitted when flags changed.

> **Note:** Notifier signal for property [flags](knotification.md#flags-prop).

### \[slot\] QVariantMap KNotification::hints() const {#hints}

Returns the custom hints set by [setHint](knotification.md#setHint)()

> **Note:** Getter function for property [hints](knotification.md#hints-prop).

*See also* [setHints](knotification.md#setHints)()

### \[signal\] void KNotification::hintsChanged() {#hintsChanged}

Emitted when hints changes.

> **Note:** Notifier signal for property [hints](knotification.md#hints-prop).

### QString KNotification::iconName() const {#iconName}

Returns the icon shown in the popup

> **Note:** Getter function for property [iconName](knotification.md#iconName-prop).

*See also* [setIconName](knotification.md#setIconName)

### \[signal\] void KNotification::iconNameChanged() {#iconNameChanged}

Emitted when [iconName](knotification.md#iconName) changed.

> **Note:** Notifier signal for property [iconName](knotification.md#iconName-prop).

### \[signal\] void KNotification::ignored() {#ignored}

The notification has been ignored

### bool KNotification::isAutoDelete() const {#isAutoDelete}

Returns whether this notification object will be automatically deleted after closing.

> **Note:** Getter function for property [autoDelete](knotification.md#autoDelete-prop).

### QPixmap KNotification::pixmap() const {#pixmap}

Returns the pixmap shown in the popup

*See also* [setPixmap](knotification.md#setPixmap)

### KNotificationReplyAction \*KNotification::replyAction() const {#replyAction}

Returns the inline reply action.

*See also* [setReplyAction](knotification.md#setReplyAction)()

### \[slot\] void KNotification::sendEvent() {#sendEvent}

Send the notification to the server.

This will cause all the configured plugins to execute their actions on this notification (eg. a sound will play, a popup will show, a command will be executed etc).

### void KNotification::setAutoDelete(bool *autoDelete*) {#setAutoDelete}

Sets whether this notification object will be automatically deleted after closing. This is on by default for C++, and off by default for QML.

> **Note:** Setter function for property [autoDelete](knotification.md#autoDelete-prop).

*See also* [isAutoDelete](knotification.md#isAutoDelete)()

### void KNotification::setComponentName(const QString &*componentName*) {#setComponentName}

The componentData is used to determine the location of the config file.

If no [componentName](knotification.md#componentName) is set, the app name is used by default

`componentName` the new component name

> **Note:** Setter function for property [componentName](knotification.md#componentName-prop).

*See also* [componentName](knotification.md#componentName)()

### void KNotification::setEventId(const QString &*eventId*) {#setEventId}

Set the event id, if not already passed to the constructor.

> **Note:** Setter function for property [eventId](knotification.md#eventId-prop).

*See also* [eventId](knotification.md#eventId)()

### void KNotification::setFlags(const KNotification::NotificationFlags &*flags*) {#setFlags}

Set the notification flags.

These must be set before calling [sendEvent](knotification.md#sendEvent)()

> **Note:** Setter function for property [flags](knotification.md#flags-prop).

*See also* [flags](knotification.md#flags)()

### \[slot\] void KNotification::setHint(const QString &*hint*, const QVariant &*value*) {#setHint}

Adds a custom hint to the notification. Those are key-value pairs that can be interpreted by the respective notification backend to trigger additional, non-standard features.

`hint` the hint's key

`value` the hint's value

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[slot\] void KNotification::setHints(const QVariantMap &*hints*) {#setHints}

Set custom hints on the notification.

> **Note:** Setter function for property [hints](knotification.md#hints-prop).

*See also* [hints](knotification.md#hints)(), [setHint](knotification.md#setHint)

### void KNotification::setIconName(const QString &*icon*) {#setIconName}

Set the icon that will be shown in the popup.

`icon` the icon

> **Note:** Setter function for property [iconName](knotification.md#iconName-prop).

*See also* [iconName](knotification.md#iconName)()

### void KNotification::setPixmap(const QPixmap &*pix*) {#setPixmap}

Set the pixmap that will be shown in the popup. If you want to use an icon from the icon theme use [setIconName](knotification.md#setIconName) instead.

`pix` the pixmap

*See also* [pixmap](knotification.md#pixmap)()

### void KNotification::setReplyAction(std::unique\_ptr\<KNotificationReplyAction\> *replyAction*) {#setReplyAction}

Add an inline reply action to the notification.

On supported platforms this lets the user type a reply to a notification, such as replying to a chat message, from the notification popup, for example:

```cpp
KNotification *notification = new KNotification(QStringLiteral("notification"));
...
auto replyAction = std::make_unique<KNotificationReplyAction>(i18nc("@action:button", "Reply"));
replyAction->setPlaceholderText(i18nc("@info:placeholder", "Reply to Dave..."));
QObject::connect(replyAction.get(), &KNotificationReplyAction::replied, [](const QString &text) {
    qDebug() << "you replied with" << text;
});
notification->setReplyAction(std::move(replyAction));
```

`replyAction` the reply action to set

*See also* [replyAction](knotification.md#replyAction)()

### void KNotification::setText(const QString &*text*) {#setText}

Set the notification text that will appear in the popup.

In Plasma workspace, the text is shown in a QML label which uses Text.StyledText, ie. it supports a small subset of HTML entities (mostly just formatting tags)

If the notifications server does not advertise "body-markup" capability, all HTML tags are stripped before sending it to the server

`text` The text to display in the notification popup

> **Note:** Setter function for property [text](knotification.md#text-prop).

*See also* [text](knotification.md#text)()

### void KNotification::setTitle(const QString &*title*) {#setTitle}

Set the title of the notification popup. If no title is set, the application name will be used.

`title` The title of the notification

> **Note:** Setter function for property [title](knotification.md#title-prop).

*See also* [title](knotification.md#title)()

### void KNotification::setUrgency(KNotification::Urgency *urgency*) {#setUrgency}

Sets the urgency of the notification.

This defines the importance of the notification. For example, a track change in a media player would be a low urgency. "You have new mail" would be normal urgency. "Your battery level is low" would be a critical urgency.

Use critical notifications with care as they might be shown even when giving a presentation or when notifications are turned off.

`urgency` The urgency.

> **Note:** Setter function for property [urgency](knotification.md#urgency-prop).

*See also* [urgency](knotification.md#urgency)()

### void KNotification::setUrls(const QList\<QUrl\> &*urls*) {#setUrls}

Sets URLs associated with this notification

For example, a screenshot application might want to provide the URL to the file that was just taken so the notification service can show a preview.

> **Note:** This feature might not be supported by the user's notification service

`urls` A list of URLs

> **Note:** Setter function for property [urls](knotification.md#urls-prop).

*See also* [urls](knotification.md#urls)()

### \[since 6.0\] void KNotification::setWindow(QWindow \**window*) {#setWindow}

Sets the window associated with this notification. This is relevant when using the [CloseWhenWindowActivated](knotification.md#NotificationFlag-enum) flag.

This function was introduced in Qt 6.0.

*See also* [window](knotification.md#window)()

### QString KNotification::text() const {#text}

Returns the notification text

> **Note:** Getter function for property [text](knotification.md#text-prop).

*See also* [setText](knotification.md#setText)

### \[signal\] void KNotification::textChanged() {#textChanged}

Emitted when text changed.

> **Note:** Notifier signal for property [text](knotification.md#text-prop).

### QString KNotification::title() const {#title}

Returns the notification title

> **Note:** Getter function for property [title](knotification.md#title-prop).

*See also* [setTitle](knotification.md#setTitle)

### \[signal\] void KNotification::titleChanged() {#titleChanged}

Emitted when title changed.

> **Note:** Notifier signal for property [title](knotification.md#title-prop).

### KNotification::Urgency KNotification::urgency() const {#urgency}

The urgency of the notification.

> **Note:** Getter function for property [urgency](knotification.md#urgency-prop).

*See also* [setUrgency](knotification.md#setUrgency)()

### \[signal\] void KNotification::urgencyChanged() {#urgencyChanged}

Emitted when urgency changed.

> **Note:** Notifier signal for property [urgency](knotification.md#urgency-prop).

### QList\<QUrl\> KNotification::urls() const {#urls}

URLs associated with this notification

> **Note:** Getter function for property [urls](knotification.md#urls-prop).

*See also* [setUrls](knotification.md#setUrls)()

### \[signal\] void KNotification::urlsChanged() {#urlsChanged}

Emitted when urls changed.

> **Note:** Notifier signal for property [urls](knotification.md#urls-prop).

### \[since 6.0\] QWindow \*KNotification::window() const {#window}

The window associated with this notification. nullptr by default. Returns the window set by [setWindow](knotification.md#setWindow)()

This function was introduced in Qt 6.0.

*See also* [setWindow](knotification.md#setWindow)()

### QString KNotification::xdgActivationToken() const {#xdgActivationToken}

Returns the activation token to use to activate a window.

> **Note:** Getter function for property [xdgActivationToken](knotification.md#xdgActivationToken-prop).

### \[signal\] void KNotification::xdgActivationTokenChanged() {#xdgActivationTokenChanged}

Emitted when [xdgActivationToken](knotification.md#xdgActivationToken) changes.

> **Note:** Notifier signal for property [xdgActivationToken](knotification.md#xdgActivationToken-prop).
