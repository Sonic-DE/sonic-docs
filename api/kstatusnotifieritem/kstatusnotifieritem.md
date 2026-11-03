---
title: "KStatusNotifierItem Class"
description: "KDE Status Notifier Item protocol implementation."
---

# KStatusNotifierItem Class

KDE Status Notifier Item protocol implementation. [More...](#details)

- **Header:** `#include <KStatusNotifierItem>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS StatusNotifierItem)`  
  `target_link_libraries(mytarget PRIVATE KF6::StatusNotifierItem)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kstatusnotifieritem-members.md)  
[Deprecated members](kstatusnotifieritem-obsolete.md)

## Public Types

- [enum KStatusNotifierItem::ItemCategory](#ItemCategory-enum)
- [enum KStatusNotifierItem::ItemStatus](#ItemStatus-enum)

## Public Functions

- [KStatusNotifierItem(QObject \*parent = nullptr)](#KStatusNotifierItem)
- [KStatusNotifierItem(const QString &id, QObject \*parent = nullptr)](#KStatusNotifierItem-1)
- [void abortQuit()](#abortQuit) (since 6.5)
- [QWindow \*associatedWindow() const](#associatedWindow) (since 6.0)
- [QString attentionIconName() const](#attentionIconName)
- [QIcon attentionIconPixmap() const](#attentionIconPixmap)
- [QString attentionMovieName() const](#attentionMovieName)
- [KStatusNotifierItem::ItemCategory category() const](#category)
- [QMenu \*contextMenu() const](#contextMenu)
- [QString iconName() const](#iconName)
- [QIcon iconPixmap() const](#iconPixmap)
- [QString id() const](#id)
- [bool isMenu() const](#isMenu) (since 6.14)
- [QString overlayIconName() const](#overlayIconName)
- [QIcon overlayIconPixmap() const](#overlayIconPixmap)
- [QString providedToken() const](#providedToken)
- [void setAssociatedWindow(QWindow \*window)](#setAssociatedWindow) (since 6.0)
- [void setAttentionIconByName(const QString &name)](#setAttentionIconByName)
- [void setAttentionIconByPixmap(const QIcon &icon)](#setAttentionIconByPixmap)
- [void setAttentionMovieByName(const QString &name)](#setAttentionMovieByName)
- [void setCategory(const KStatusNotifierItem::ItemCategory category)](#setCategory)
- [void setContextMenu(QMenu \*menu)](#setContextMenu)
- [void setIconByName(const QString &name)](#setIconByName)
- [void setIconByPixmap(const QIcon &icon)](#setIconByPixmap)
- [void setIsMenu(bool isMenu)](#setIsMenu) (since 6.14)
- [void setOverlayIconByName(const QString &name)](#setOverlayIconByName)
- [void setOverlayIconByPixmap(const QIcon &icon)](#setOverlayIconByPixmap)
- [void setStandardActionsEnabled(bool enabled)](#setStandardActionsEnabled)
- [void setStatus(const KStatusNotifierItem::ItemStatus status)](#setStatus)
- [void setTitle(const QString &title)](#setTitle)
- [void setToolTip(const QString &iconName, const QString &title, const QString &subTitle)](#setToolTip)
- [void setToolTip(const QIcon &icon, const QString &title, const QString &subTitle)](#setToolTip-1)
- [void setToolTipIconByName(const QString &name)](#setToolTipIconByName)
- [void setToolTipIconByPixmap(const QIcon &icon)](#setToolTipIconByPixmap)
- [void setToolTipSubTitle(const QString &subTitle)](#setToolTipSubTitle)
- [void setToolTipTitle(const QString &title)](#setToolTipTitle)
- [void showMessage(const QString &title, const QString &message, const QString &icon, int timeout = 10000)](#showMessage)
- [bool standardActionsEnabled() const](#standardActionsEnabled)
- [KStatusNotifierItem::ItemStatus status() const](#status)
- [QString title() const](#title)
- [QString toolTipIconName() const](#toolTipIconName)
- [QIcon toolTipIconPixmap() const](#toolTipIconPixmap)
- [QString toolTipSubTitle() const](#toolTipSubTitle)
- [QString toolTipTitle() const](#toolTipTitle)

## Public Slots

- [void activate(const QPoint &pos = QPoint())](#activate)
- [void hideAssociatedWindow()](#hideAssociatedWindow) (since 6.0)

## Signals

- [void activateRequested(bool active, const QPoint &pos)](#activateRequested)
- [void quitRequested()](#quitRequested) (since 6.5)
- [void scrollRequested(int delta, Qt::Orientation orientation)](#scrollRequested)
- [void secondaryActivateRequested(const QPoint &pos)](#secondaryActivateRequested)

## Detailed Description {#details}

This class implements the Status notifier Item D-Bus specification. It provides an icon similar to the classical systemtray icons, with some key differences:

- the actual representation is done by the systemtray (or the app behaving like it) itself, not by this app. Since 4.5 this also includes the menu, which means you cannot use embed widgets in the menu.
- there is communication between the systemtray and the icon owner, so the system tray can know if the application is in a normal or in a requesting attention state.
- icons are divided in categories, so the systemtray can represent in a different way the icons from normal applications and for instance the ones about hardware status.

Whenever possible you should prefer passing icon by name rather than by pixmap because:

- it is much lighter on D-Bus (no need to pass all image pixels).
- it makes it possible for the systemtray to load an icon of the appropriate size or to replace your icon with a systemtray specific icon which matches with the desktop theme.
- some implementations of the system tray do not support passing icons by pixmap and will show a blank icon instead.

> **Note:** When used inside a Flatpak it is important to request explicit support in the Flatpak manifest with the following line: `--talk-name=org.kde.StatusNotifierWatcher`

## Member Type Documentation {#member-type-documentation}

### enum KStatusNotifierItem::ItemCategory {#ItemCategory-enum}

Different kinds of applications announce their type to the systemtray, so can be drawn in a different way or in a different place.

| Constant | Value | Description |
| --- | --- | --- |
| `KStatusNotifierItem::ApplicationStatus` | `1` | An icon for a normal application, can be seen as its taskbar entry. This is the default value. |
| `KStatusNotifierItem::Communications` | `2` | This is a communication oriented application; this icon will be used for things such as the notification of a new message. |
| `KStatusNotifierItem::SystemServices` | `3` | This is a system service, it can show itself in the system tray if it requires interaction from the user or wants to inform him about something. |
| `KStatusNotifierItem::Hardware` | `4` | This application shows hardware status or a means to control it. |
| `KStatusNotifierItem::Reserved` | `129` |   |

### enum KStatusNotifierItem::ItemStatus {#ItemStatus-enum}

All the possible status this icon can have, depending on the importance of the events that happens in the parent application.

| Constant | Value | Description |
| --- | --- | --- |
| `KStatusNotifierItem::Passive` | `1` | Nothing is happening in the application, so showing this icon is not required. This is the default value. |
| `KStatusNotifierItem::Active` | `2` | The application is doing something, or it is important that the icon is always reachable from the user. |
| `KStatusNotifierItem::NeedsAttention` | `3` | The application requests the attention of the user, for instance battery running out or a new IM message was received. |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KStatusNotifierItem::KStatusNotifierItem(QObject \**parent* = nullptr) {#KStatusNotifierItem}

Construct a new status notifier item.

`parent` the parent object for this object. If the object passed in as a parent is also a [QWidget](https://doc.qt.io/qt-6/qwidget.html), it will be used as the main application window represented by this icon and will be shown/hidden when an activation is requested.

*See also* [associatedWindow](kstatusnotifieritem.md#associatedWindow)

### \[explicit\] KStatusNotifierItem::KStatusNotifierItem(const QString &*id*, QObject \**parent* = nullptr) {#KStatusNotifierItem-1}

Construct a new status notifier item with a unique identifier.

If your application has more than one status notifier item and the user should be able to manipulate them separately (e.g. mark them for hiding in a user interface), the id can be used to differentiate between them.

The id should remain consistent even between application restarts. Status notifier items without ids default to the application's name for the id. This id may be used, for instance, by hosts displaying status notifier items to associate configuration information with this item in a way that can persist between sessions or application restarts.

`id` the unique id for this icon

`parent` the parent object for this object. If the object passed in as a parent is also a [QWidget](https://doc.qt.io/qt-6/qwidget.html), it will be used as the main application window represented by this icon and will be shown/hidden when an activation is requested.

*See also* [associatedWindow](kstatusnotifieritem.md#associatedWindow)

### \[since 6.5\] void KStatusNotifierItem::abortQuit() {#abortQuit}

Cancelles an ongoing quit operation.

Call this in a slot connected to [quitRequested](kstatusnotifieritem.md#quitRequested)().

This function was introduced in Qt 6.5.

*See also* [quitRequested](kstatusnotifieritem.md#quitRequested)()

### \[virtual slot\] void KStatusNotifierItem::activate(const QPoint &*pos* = QPoint()) {#activate}

Shows the main window and try to position it on top of the other windows, if the window is already visible, hide it.

`pos` if it's a valid position it represents the mouse coordinates when the event was triggered

### \[signal\] void KStatusNotifierItem::activateRequested(bool *active*, const QPoint &*pos*) {#activateRequested}

Inform the host application that an activation has been requested.

For instance left mouse click, but this is not guaranteed since it's dependent from the visualization

`active` if it's true the application asked for the activation of the main window, if it's false it asked for hiding

`pos` the position in the screen where the user clicked to trigger this signal, QPoint() if it's not the consequence of a mouse click.

### \[since 6.0\] QWindow \*KStatusNotifierItem::associatedWindow() const {#associatedWindow}

Access the main window associated with this StatusNotifierItem.

This function was introduced in Qt 6.0.

*See also* [setAssociatedWindow](kstatusnotifieritem.md#setAssociatedWindow)()

### QString KStatusNotifierItem::attentionIconName() const {#attentionIconName}

Returns the name of the icon to be displayed when the application is requesting the user's attention.

If attentionImage() is not empty this will always return an empty string.

> **Note:** Getter function for property attentionIconName.

### QIcon KStatusNotifierItem::attentionIconPixmap() const {#attentionIconPixmap}

Returns a pixmap of the requesting attention icon

### QString KStatusNotifierItem::attentionMovieName() const {#attentionMovieName}

Returns the name of the movie to be displayed when the application is requesting the user attention.

### KStatusNotifierItem::ItemCategory KStatusNotifierItem::category() const {#category}

Returns the application category.

> **Note:** Getter function for property category.

*See also* [setCategory](kstatusnotifieritem.md#setCategory)()

### QMenu \*KStatusNotifierItem::contextMenu() const {#contextMenu}

Access the context menu associated to this status notifier item.

*See also* [setContextMenu](kstatusnotifieritem.md#setContextMenu)()

### \[slot, since 6.0\] void KStatusNotifierItem::hideAssociatedWindow() {#hideAssociatedWindow}

Hides the main window, if not already hidden.

Stores some information about the window which otherwise would be lost due to unmapping from the window system. Use when toggling the main window via activate(const [QPoint](https://doc.qt.io/qt-6/qpoint.html) &) is not wanted, but instead the hidden state should be reached in any case.

This function was introduced in Qt 6.0.

### QString KStatusNotifierItem::iconName() const {#iconName}

Returns the name of the main icon to be displayed.

If image() is not empty this will always return an empty string

> **Note:** Getter function for property iconName.

### QIcon KStatusNotifierItem::iconPixmap() const {#iconPixmap}

Returns a pixmap of the icon.

### QString KStatusNotifierItem::id() const {#id}

Returns the id which was specified in the constructor.

This should be guaranteed to be consistent between application starts and untranslated, as host applications displaying items may use it for storing configuration related to this item.

### \[since 6.14\] bool KStatusNotifierItem::isMenu() const {#isMenu}

Returns if the item indicates that it only supports the context menu.

This function was introduced in Qt 6.14.

*See also* [setIsMenu](kstatusnotifieritem.md#setIsMenu)()

### QString KStatusNotifierItem::overlayIconName() const {#overlayIconName}

Returns the name of the icon to be used as overlay fr the main one.

> **Note:** Getter function for property overlayIconName.

### QIcon KStatusNotifierItem::overlayIconPixmap() const {#overlayIconPixmap}

Returns a pixmap of the icon

### QString KStatusNotifierItem::providedToken() const {#providedToken}

Returns the last provided token to be used with Wayland's xdg\_activation\_v1.

### \[signal, since 6.5\] void KStatusNotifierItem::quitRequested() {#quitRequested}

Emitted when the Quit action is triggered.

If [abortQuit](kstatusnotifieritem.md#abortQuit)() is called from the slot the quit is cancelled. This allows to e.g. display a custom confirmation prompt.

This function was introduced in Qt 6.5.

### \[signal\] void KStatusNotifierItem::scrollRequested(int *delta*, Qt::Orientation *orientation*) {#scrollRequested}

Inform the host application that the mouse wheel (or another mean of scrolling that the visualization provides) has been used.

`delta` the amount of scrolling, can be either positive or negative

`orientation` direction of the scrolling, can be either horizontal or vertical

### \[signal\] void KStatusNotifierItem::secondaryActivateRequested(const QPoint &*pos*) {#secondaryActivateRequested}

Alternate activate action.

For instance right mouse click, but this is not guaranteed since it's dependent from the visualization

`pos` the position in the screen where the user clicked to trigger this signal, QPoint() if it's not the consequence of a mouse click.

### \[since 6.0\] void KStatusNotifierItem::setAssociatedWindow(QWindow \**window*) {#setAssociatedWindow}

Sets the main window associated with this StatusNotifierItem.

`window` The window to be used.

This function was introduced in Qt 6.0.

*See also* [associatedWindow](kstatusnotifieritem.md#associatedWindow)()

### void KStatusNotifierItem::setAttentionIconByName(const QString &*name*) {#setAttentionIconByName}

Sets a new icon that should be used when the application wants to request attention (usually the systemtray will blink between this icon and the main one).

`name` [QIcon::fromTheme](https://doc.qt.io/qt-6/qicon.html#fromTheme) compatible name of icon to use

> **Note:** Setter function for property attentionIconName.

### void KStatusNotifierItem::setAttentionIconByPixmap(const QIcon &*icon*) {#setAttentionIconByPixmap}

Sets the pixmap of the requesting attention icon.

Use setAttentionIcon(const [QString](https://doc.qt.io/qt-6/qstring.html)) instead when possible.

`icon` [QIcon](https://doc.qt.io/qt-6/qicon.html) to use for requesting attention.

### void KStatusNotifierItem::setAttentionMovieByName(const QString &*name*) {#setAttentionMovieByName}

Sets a movie `name` as the requesting attention icon.

This overrides anything set in setAttentionIcon()

### void KStatusNotifierItem::setCategory(const KStatusNotifierItem::ItemCategory *category*) {#setCategory}

Sets the category for this icon.

Usually it's needed to call this function only once.

`category` the new category for this icon

> **Note:** Setter function for property category.

*See also* [category](kstatusnotifieritem.md#category)()

### void KStatusNotifierItem::setContextMenu(QMenu \**menu*) {#setContextMenu}

Sets a new context `menu` for this StatusNotifierItem.

the menu will be shown with a [contextMenu](kstatusnotifieritem.md#contextMenu)(int,int) call by the systemtray over D-Bus

The [KStatusNotifierItem](kstatusnotifieritem.md) instance takes ownership of the menu, and will delete it upon its destruction.

*See also* [contextMenu](kstatusnotifieritem.md#contextMenu)()

### void KStatusNotifierItem::setIconByName(const QString &*name*) {#setIconByName}

Sets a new main icon for the system tray.

`name` it must be a [QIcon::fromTheme](https://doc.qt.io/qt-6/qicon.html#fromTheme) compatible name, this is the preferred way to set an icon

> **Note:** Setter function for property iconName.

### void KStatusNotifierItem::setIconByPixmap(const QIcon &*icon*) {#setIconByPixmap}

Sets a new main icon for the system tray.

`icon` our icon, use setIcon(const [QString](https://doc.qt.io/qt-6/qstring.html)) when possible

### \[since 6.14\] void KStatusNotifierItem::setIsMenu(bool *isMenu*) {#setIsMenu}

Indictates that this item only supports the context menu. Instead of sending activate the provided the menu will be shown.

This function was introduced in Qt 6.14.

*See also* [isMenu](kstatusnotifieritem.md#isMenu)(), [setContextMenu](kstatusnotifieritem.md#setContextMenu)

### void KStatusNotifierItem::setOverlayIconByName(const QString &*name*) {#setOverlayIconByName}

Sets an icon to be used as overlay for the main one.

`name` the icon name, if name is and empty QString() (and [overlayIconPixmap](kstatusnotifieritem.md#overlayIconPixmap)() is empty too) the icon will be removed

> **Note:** Setter function for property overlayIconName.

### void KStatusNotifierItem::setOverlayIconByPixmap(const QIcon &*icon*) {#setOverlayIconByPixmap}

Sets an icon to be used as overlay for the main one.

setOverlayIconByPixmap(QIcon()) will remove the overlay when [overlayIconName](kstatusnotifieritem.md#overlayIconName)() is empty too.

`icon` our overlay icon, use setOverlayIcon(const [QString](https://doc.qt.io/qt-6/qstring.html)) when possible.

### void KStatusNotifierItem::setStandardActionsEnabled(bool *enabled*) {#setStandardActionsEnabled}

`enabled` Whether to show the standard items in the menu, such as Quit.

*See also* [standardActionsEnabled](kstatusnotifieritem.md#standardActionsEnabled)()

### void KStatusNotifierItem::setStatus(const KStatusNotifierItem::ItemStatus *status*) {#setStatus}

Sets a new `status` for this icon.

> **Note:** Setter function for property status.

*See also* [status](kstatusnotifieritem.md#status)()

### void KStatusNotifierItem::setTitle(const QString &*title*) {#setTitle}

Sets a `title` for this icon.

> **Note:** Setter function for property title.

*See also* [title](kstatusnotifieritem.md#title)()

### void KStatusNotifierItem::setToolTip(const QString &*iconName*, const QString &*title*, const QString &*subTitle*) {#setToolTip}

Sets a new toolTip for this icon.

A toolTip is composed of an icon, a title and a text, all fields are optional.

`iconName` a [QIcon::fromTheme](https://doc.qt.io/qt-6/qicon.html#fromTheme) compatible name for the tootip icon

`title` tootip title

`subTitle` subtitle for the toolTip

### void KStatusNotifierItem::setToolTip(const QIcon &*icon*, const QString &*title*, const QString &*subTitle*) {#setToolTip-1}

Sets a new toolTip or this status notifier item.

`icon` a QIcon() pixmap for the tooltip icon

`title` tootip title

`subTitle` subtitle for the toolTip

This function overloads [KStatusNotifierItem::setTooltip()](kstatusnotifieritem-index.md).

### void KStatusNotifierItem::setToolTipIconByName(const QString &*name*) {#setToolTipIconByName}

Sets a new icon for the toolTip.

`name` the name for the icon

> **Note:** Setter function for property toolTipIconName.

### void KStatusNotifierItem::setToolTipIconByPixmap(const QIcon &*icon*) {#setToolTipIconByPixmap}

Set a new icon for the toolTip.

Use [setToolTipIconByName](kstatusnotifieritem.md#setToolTipIconByName)([QString](https://doc.qt.io/qt-6/qstring.html)) if possible.

`icon` representing the icon

### void KStatusNotifierItem::setToolTipSubTitle(const QString &*subTitle*) {#setToolTipSubTitle}

Sets a new `subTitle` for the toolTip.

> **Note:** Setter function for property toolTipSubTitle.

*See also* [toolTipSubTitle](kstatusnotifieritem.md#toolTipSubTitle)()

### void KStatusNotifierItem::setToolTipTitle(const QString &*title*) {#setToolTipTitle}

Sets a new `title` for the toolTip.

> **Note:** Setter function for property toolTipTitle.

*See also* [toolTipTitle](kstatusnotifieritem.md#toolTipTitle)()

### void KStatusNotifierItem::showMessage(const QString &*title*, const QString &*message*, const QString &*icon*, int *timeout* = 10000) {#showMessage}

Shows the user a notification.

If possible use KNotify instead.

`title` message title

`message` the actual text shown to the user

`icon` icon to be shown to the user

`timeout` how much time will elapse before hiding the message

### bool KStatusNotifierItem::standardActionsEnabled() const {#standardActionsEnabled}

Returns if the standard items in the menu, such as Quit.

*See also* [setStandardActionsEnabled](kstatusnotifieritem.md#setStandardActionsEnabled)()

### KStatusNotifierItem::ItemStatus KStatusNotifierItem::status() const {#status}

Returns the current application status.

> **Note:** Getter function for property status.

*See also* [setStatus](kstatusnotifieritem.md#setStatus)()

### QString KStatusNotifierItem::title() const {#title}

Returns the title of this icon.

> **Note:** Getter function for property title.

*See also* [setTitle](kstatusnotifieritem.md#setTitle)()

### QString KStatusNotifierItem::toolTipIconName() const {#toolTipIconName}

Returns the name of the toolTip icon.

If toolTipImage() is not empty this will always return an empty string.

> **Note:** Getter function for property toolTipIconName.

### QIcon KStatusNotifierItem::toolTipIconPixmap() const {#toolTipIconPixmap}

Returns a serialization of the toolTip icon data.

### QString KStatusNotifierItem::toolTipSubTitle() const {#toolTipSubTitle}

Returns the subtitle of the main icon toolTip.

> **Note:** Getter function for property toolTipSubTitle.

*See also* [setToolTipSubTitle](kstatusnotifieritem.md#setToolTipSubTitle)()

### QString KStatusNotifierItem::toolTipTitle() const {#toolTipTitle}

Returns the title of the main icon toolTip.

> **Note:** Getter function for property toolTipTitle.

*See also* [setToolTipTitle](kstatusnotifieritem.md#setToolTipTitle)()
