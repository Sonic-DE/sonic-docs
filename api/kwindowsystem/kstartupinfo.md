---
title: "KStartupInfo Class"
description: "Class for manipulating the application startup notification."
---

# KStartupInfo Class

Class for manipulating the application startup notification. [More...](#details)

- **Header:** `#include <KStartupInfo>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KWindowSystem)`  
  `target_link_libraries(mytarget PRIVATE KF6::KWindowSystem)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kstartupinfo-members.md)

## Public Types

- [enum KStartupInfo::startup\_t](#startup_t-enum)

## Public Functions

- [KStartupInfo(int flags, QObject \*parent = nullptr)](#KStartupInfo)
- [KStartupInfo::startup\_t checkStartup(WId w)](#checkStartup)
- [KStartupInfo::startup\_t checkStartup(WId w, KStartupInfoData &data)](#checkStartup-1)
- [KStartupInfo::startup\_t checkStartup(WId w, KStartupInfoId &id)](#checkStartup-2)
- [KStartupInfo::startup\_t checkStartup(WId w, KStartupInfoId &id, KStartupInfoData &data)](#checkStartup-3)
- [void setTimeout(unsigned int secs)](#setTimeout)

## Signals

- [void gotNewStartup(const KStartupInfoId &id, const KStartupInfoData &data)](#gotNewStartup)
- [void gotRemoveStartup(const KStartupInfoId &id, const KStartupInfoData &data)](#gotRemoveStartup)
- [void gotStartupChange(const KStartupInfoId &id, const KStartupInfoData &data)](#gotStartupChange)

## Static Public Members

- [void appStarted()](#appStarted)
- [void appStarted(const QByteArray &startup\_id)](#appStarted-1)
- [QByteArray createNewStartupId()](#createNewStartupId)
- [QByteArray createNewStartupIdForTimestamp(quint32 timestamp)](#createNewStartupIdForTimestamp)
- [void resetStartupEnv()](#resetStartupEnv)
- [bool sendChange(const KStartupInfoId &id, const KStartupInfoData &data)](#sendChange)
- [bool sendChangeXcb(xcb\_connection\_t \*conn, int screen, const KStartupInfoId &id, const KStartupInfoData &data)](#sendChangeXcb)
- [bool sendFinish(const KStartupInfoId &id)](#sendFinish)
- [bool sendFinish(const KStartupInfoId &id, const KStartupInfoData &data)](#sendFinish-1)
- [bool sendFinishXcb(xcb\_connection\_t \*conn, int screen, const KStartupInfoId &id)](#sendFinishXcb)
- [bool sendFinishXcb(xcb\_connection\_t \*conn, int screen, const KStartupInfoId &id, const KStartupInfoData &data)](#sendFinishXcb-1)
- [bool sendStartup(const KStartupInfoId &id, const KStartupInfoData &data)](#sendStartup)
- [bool sendStartupXcb(xcb\_connection\_t \*conn, int screen, const KStartupInfoId &id, const KStartupInfoData &data)](#sendStartupXcb)
- [void setNewStartupId(QWindow \*window, const QByteArray &startup\_id)](#setNewStartupId)
- [void setStartupId(const QByteArray &startup\_id)](#setStartupId)
- [QByteArray windowStartupId(WId w)](#windowStartupId)

## Detailed Description {#details}

This class can be used to send information about started application, change the information and receive this information. For detailed description, see [https://invent.kde.org/frameworks/kwindowsystem/-/blob/master/docs/README.kstartupinfo](https://invent.kde.org/frameworks/kwindowsystem/-/blob/master/docs/README.kstartupinfo).

You usually don't need to use this class for sending the notification information, as KDE libraries should do this when an application is started (e.g. KRun class).

For receiving the startup notification info, create an instance and connect to its slots. It will automatically detect started applications and when they are ready.

*See also* [KStartupInfoId](kstartupinfoid.md), [KStartupInfoData](kstartupinfodata.md)

## Member Type Documentation {#member-type-documentation}

### enum KStartupInfo::startup\_t {#startup_t-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KStartupInfo::NoMatch` | `0` | The window doesn't match any existing startup notification. |
| `KStartupInfo::Match` | `1` | The window matches an existing startup notification. |
| `KStartupInfo::CantDetect` | `2` | Unable to detect if the window matches any existing startup notification. |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KStartupInfo::KStartupInfo(int *flags*, QObject \**parent* = nullptr) {#KStartupInfo}

Creates an instance that will receive the startup notifications, as a child of `parent`.

The various `flags` passed may be:

| Constant | Description |
| --- | --- |
| CleanOnCantDetect | When a new unknown window appears, all startup notifications for applications that are not compliant with the startup protocol are removed. |
| DisableKWinModule | KWinModule, which is normally used to detect new windows, is disabled. With this flag, [checkStartup](kstartupinfo.md#checkStartup)() must be called in order to check newly mapped windows. |
| AnnounceSilenceChanges | Normally, startup notifications are "removed" when they're silenced, and "recreated" when they're resumed. With this flag, the change is normally announced with [gotStartupChange](kstartupinfo.md#gotStartupChange)(). |

### \[static\] void KStartupInfo::appStarted() {#appStarted}

Manual notification that the application has started.

If you do not map a (toplevel) window, then startup notification will not disappear for the application until a timeout. You can use this as an alternative method in this case.

### \[static\] void KStartupInfo::appStarted(const QByteArray &*startup\_id*) {#appStarted-1}

Sends explicit notification that the startup notification with `startup_id` should end.

### KStartupInfo::startup\_t KStartupInfo::checkStartup(WId *w*) {#checkStartup}

Checks if the given window `w` matches any existing startup notification.

### KStartupInfo::startup\_t KStartupInfo::checkStartup(WId *w*, KStartupInfoData &*data*) {#checkStartup-1}

Checks if the given window `w` matches any existing startup notification, if yes, returns the notification data in `data`.

### KStartupInfo::startup\_t KStartupInfo::checkStartup(WId *w*, KStartupInfoId &*id*) {#checkStartup-2}

Checks if the given window `w` matches any existing startup notification, if yes, returns the identification in `id`.

### KStartupInfo::startup\_t KStartupInfo::checkStartup(WId *w*, KStartupInfoId &*id*, KStartupInfoData &*data*) {#checkStartup-3}

Checks if the given window `w` matches any existing startup notification, if yes, returns the identification in `id` and notification data in `data`.

### \[static\] QByteArray KStartupInfo::createNewStartupId() {#createNewStartupId}

Creates and returns a new startup id. The id includes properly setup user timestamp.

On the X11 platform the current timestamp will be fetched from the X-Server. If the caller has an adequate timestamp (e.g. from a [QMouseEvent](https://doc.qt.io/qt-6/qmouseevent.html)) it should prefer using [createNewStartupIdForTimestamp](kstartupinfo.md#createNewStartupIdForTimestamp) to not trigger a roundtrip to the X-Server.

*See also* [createNewStartupIdForTimestamp](kstartupinfo.md#createNewStartupIdForTimestamp)

### \[static\] QByteArray KStartupInfo::createNewStartupIdForTimestamp(quint32 *timestamp*) {#createNewStartupIdForTimestamp}

Creates and returns new startup id with `timestamp` as user timestamp part.

`timestamp` The timestamp for the startup id.

*See also* [createNewStartupId](kstartupinfo.md#createNewStartupId)

### \[signal\] void KStartupInfo::gotNewStartup(const KStartupInfoId &*id*, const KStartupInfoData &*data*) {#gotNewStartup}

Emitted when a new startup notification is created (i.e. a new application is being started).

`id` The notification identification.

`data` The notification data.

### \[signal\] void KStartupInfo::gotRemoveStartup(const KStartupInfoId &*id*, const KStartupInfoData &*data*) {#gotRemoveStartup}

Emitted when a startup notification is removed (either because it was detected that the application is ready or because of a timeout).

`id` The notification identification.

`data` The notification data.

### \[signal\] void KStartupInfo::gotStartupChange(const KStartupInfoId &*id*, const KStartupInfoData &*data*) {#gotStartupChange}

Emitted when a startup notification changes.

`id` The notification identification.

`data` The notification data.

### \[static\] void KStartupInfo::resetStartupEnv() {#resetStartupEnv}

Unsets the startup notification environment variable.

### \[static\] bool KStartupInfo::sendChange(const KStartupInfoId &*id*, const KStartupInfoData &*data*) {#sendChange}

Sends given notification data about started application with the given startup identification.

This is used for updating the notification info, if no notification for this identification exists, it's ignored.

Returns `true` if successful, `false` otherwise.

`id` The id of the application.

`data` The application's data.

*See also* [KStartupInfoId](kstartupinfoid.md), [KStartupInfoData](kstartupinfodata.md)

### \[static\] bool KStartupInfo::sendChangeXcb(xcb\_connection\_t \**conn*, int *screen*, const KStartupInfoId &*id*, const KStartupInfoData &*data*) {#sendChangeXcb}

Like [sendChange](kstartupinfo.md#sendChange), uses `conn` instead of QX11Info::connection() for sending the info.

Returns `true` if successful, `false` otherwise.

`conn` The xcb connection of the application.

`screen` The x11 screen the connection belongs to.

`id` The id of the application.

`data` The application's data.

### \[static\] bool KStartupInfo::sendFinish(const KStartupInfoId &*id*) {#sendFinish}

Ends startup notification with the given identification.

Returns `true` if successful, `false` otherwise

`id` The id of the application.

### \[static\] bool KStartupInfo::sendFinish(const KStartupInfoId &*id*, const KStartupInfoData &*data*) {#sendFinish-1}

Ends startup notification with the given identification and the given data (e.g. PIDs of processes for this startup notification that exited).

Returns `true` if successful, `false` otherwise

`id` The id of the application.

`data` The application's data.

### \[static\] bool KStartupInfo::sendFinishXcb(xcb\_connection\_t \**conn*, int *screen*, const KStartupInfoId &*id*) {#sendFinishXcb}

Like [sendFinish](kstartupinfo.md#sendFinish) , uses `conn` instead of QX11Info::connection() for sending the info.

Returns `true` if successful, `false` otherwise.

`conn` The xcb connection of the application.

`screen` The x11 screen the connection belongs to.

`id` The id of the application.

### \[static\] bool KStartupInfo::sendFinishXcb(xcb\_connection\_t \**conn*, int *screen*, const KStartupInfoId &*id*, const KStartupInfoData &*data*) {#sendFinishXcb-1}

Like [sendFinish](kstartupinfo.md#sendFinish) , uses `conn` instead of QX11Info::connection() for sending the info.

Returns `true` if successful, `false` otherwise.

`conn` The xcb connection of the application.

`screen` The x11 screen the connection belongs to.

`id` The id of the application.

`data` The application's data.

### \[static\] bool KStartupInfo::sendStartup(const KStartupInfoId &*id*, const KStartupInfoData &*data*) {#sendStartup}

Sends given notification data about started application with the given startup identification.

If no notification for this identification exists yet, it is created, otherwise it's updated. Note that the name field in data is required.

Returns `true` if successful, `false` otherwise

`id` The id of the application.

`data` The application's data.

*See also* [KStartupInfoId](kstartupinfoid.md), [KStartupInfoData](kstartupinfodata.md)

### \[static\] bool KStartupInfo::sendStartupXcb(xcb\_connection\_t \**conn*, int *screen*, const KStartupInfoId &*id*, const KStartupInfoData &*data*) {#sendStartupXcb}

Like [sendStartup](kstartupinfo.md#sendStartup), uses `conn` instead of QX11Info::connection() for sending the info.

Returns `true` if successful, `false` otherwise.

`conn` The xcb connection of the application. Note that the name field in data is required.

`screen` The x11 screen the connection belongs to.

`id` The id of the application.

`data` The application's data.

### \[static\] void KStartupInfo::setNewStartupId(QWindow \**window*, const QByteArray &*startup\_id*) {#setNewStartupId}

Use this function if the application got a request with startup notification from outside (for example, when KUniqueApplication::newInstance() is called, or e.g. when KHelpCenter opens a new URL in its window).

The `window` can be either an already existing and visible window, or a new one, before being shown. Note that this function is usually needed only when a window is reused.

`startup_id` the startup notification identifier

### \[static\] void KStartupInfo::setStartupId(const QByteArray &*startup\_id*) {#setStartupId}

Sets a new value for the application startup notification window property for newly created toplevel windows.

`startup_id` The startup notification identifier.

*See also* [KStartupInfo::setNewStartupId](kstartupinfo.md#setNewStartupId)

### void KStartupInfo::setTimeout(unsigned int *secs*) {#setTimeout}

Sets the timeout for notifications in `secs`, after this timeout a notification is removed.

### \[static\] QByteArray KStartupInfo::windowStartupId(WId *w*) {#windowStartupId}

Returns startup notification identification of the given window `w`.

Returns the startup notification id. Can be null if not found.
