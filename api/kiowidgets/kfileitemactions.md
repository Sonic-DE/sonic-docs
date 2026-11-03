---
title: "KFileItemActions Class"
description: "productname."
---

# KFileItemActions Class

productname. [More...](#details)

- **Header:** `#include <KFileItemActions>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kfileitemactions-members.md)

## Public Types

- [enum KFileItemActions::MenuActionSource](#MenuActionSource-enum)

## Public Functions

- [KFileItemActions(QObject \*parent = nullptr)](#KFileItemActions)
- [void addActionsTo(QMenu \*menu, KFileItemActions::MenuActionSources sources = MenuActionSource::All, const QList\<QAction \*\> &additionalActions = {}, const QStringList &excludeList = {})](#addActionsTo)
- [QList\<QAction \*\> createServiceMenuActions()](#createServiceMenuActions) (since 6.24)
- [void insertOpenWithActionsTo(QAction \*before, QMenu \*topMenu, const QStringList &excludedDesktopEntryNames)](#insertOpenWithActionsTo)
- [void setCurrentWorkingDirectory(const QUrl &currentWorkingDirectory)](#setCurrentWorkingDirectory) (since 6.32)
- [void setItemListProperties(const KFileItemListProperties &itemList)](#setItemListProperties)
- [void setParentObject(QObject \*parent)](#setParentObject) (since 6.32)
- [void setParentWidget(QWidget \*widget)](#setParentWidget)

## Public Slots

- [void runPreferredApplications(const KFileItemList &fileOpenList)](#runPreferredApplications)

## Signals

- [void error(const QString &errorMessage)](#error)
- [void openWithDialogAboutToBeShown()](#openWithDialogAboutToBeShown)

## Static Public Members

- [KService::List associatedApplications(const QStringList &mimeTypeList)](#associatedApplications)

## Detailed Description {#details}

This class creates and handles the actions for a url (or urls) in a popupmenu.

This includes:

- "open with \<application\>" actions, but also
- user-defined actions for a .desktop file, defined in the file itself (see the desktop entry standard)
- servicemenus actions, defined in .desktop files and selected based on the MIME type of the url

[KFileItemActions](kfileitemactions.md) respects Kiosk-based restrictions (see the KAuthorized namespace in the KConfig framework). In particular, the "action/openwith" action is checked when determining actions for opening files (see addOpenWithActionsTo()) and service-specific actions are checked before adding service actions to a menu (see addServiceActionsTo()).

For user-defined actions in a .desktop file, the "X-KDE-AuthorizeAction" key can be used to determine which actions are checked before the user-defined action is allowed. The action is ignored if any of the listed actions are not authorized.

> **Note:** The builtin services like mount/unmount for old-style device desktop files (which mainly concerns CDROM and Floppy drives) have been deprecated since 5.82; those menu entries were hidden long before that, since the FSDevice .desktop template file hadn't been installed for quite a while.

## Member Type Documentation {#member-type-documentation}

### enum KFileItemActions::MenuActionSource {#MenuActionSource-enum}

**flags KFileItemActions::MenuActionSources**

| Constant | Value | Description |
| --- | --- | --- |
| `KFileItemActions::MenuActionSource::Services` | `0x1` | Add user defined actions and servicemenu actions (this used to include builtin actions, which have been deprecated since 5.82 see class API documentation) |
| `KFileItemActions::MenuActionSource::Plugins` | `0x2` | Add actions implemented by plugins. See [KAbstractFileItemActionPlugin](kabstractfileitemactionplugin.md) base class |
| `KFileItemActions::MenuActionSource::All` | `Services | Plugins` |   |

The `MenuActionSources` type is a typedef for `QFlags<MenuActionSource>. `It stores an OR combination of `MenuActionSource` values.

## Member Function Documentation {#member-function-documentation}

### KFileItemActions::KFileItemActions(QObject \**parent* = nullptr) {#KFileItemActions}

Creates a [KFileItemActions](kfileitemactions.md) instance. Note that this instance must stay alive for at least as long as the popupmenu; it has the slots for the actions created by addOpenWithActionsTo/addServiceActionsTo.

### void KFileItemActions::addActionsTo(QMenu \**menu*, KFileItemActions::MenuActionSources *sources* = MenuActionSource::All, const QList\<QAction \*\> &*additionalActions* = {}, const QStringList &*excludeList* = {}) {#addActionsTo}

This methods adds additional actions to the menu.

`menu` Menu to which the actions/submenus will be added.

`sources` sources from which the actions should be fetched. By default all sources are used.

`additionalActions` additional actions that should be added to the "Actions" submenu or top level menu if there are less than three entries in total.

`excludeList` list of action names or plugin ids that should be excluded

### \[static\] KService::List KFileItemActions::associatedApplications(const QStringList &*mimeTypeList*) {#associatedApplications}

Returns the applications associated with all the given MIME types.

This is basically a KApplicationTrader::query, but it supports multiple MIME types, and also cleans up "apparent" duplicates, such as different versions of the same application installed in parallel.

The list is sorted according to the user preferences for the given MIME type(s). In case multiple MIME types appear in the URL list, the logic is: applications that on average appear earlier on the associated applications list for the given MIME types also appear earlier on the final applications list.

Note that for a single MIME type there is no need to use this, you should use KApplicationTrader instead, e.g. query() or preferredService().

This will return an empty list if the "openwith" Kiosk action is not authorized (see KAuthorized::authorize()).

`mimeTypeList` the MIME types

Returns the sorted list of services.

### \[since 6.24\] QList\<QAction \*\> KFileItemActions::createServiceMenuActions() {#createServiceMenuActions}

Creates [QAction](https://doc.qt.io/qt-6/qaction.html) objects for enabled service menu actions.

The returned actions are connected to the internal execution handler and will execute the service menu command on the current file selection when triggered. The file selection is determined by [setItemListProperties](kfileitemactions.md#setItemListProperties)().

Use this method to register service menu actions in a KActionCollection to enable keyboard shortcuts.

Actions are parented to this [KFileItemActions](kfileitemactions.md) instance. Calling this method multiple times will return new action instances each time.

Returns List of QActions ready for use with KActionCollection

This function was introduced in Qt 6.24.

### \[signal\] void KFileItemActions::error(const QString &*errorMessage*) {#error}

Forwards the errors from the [KAbstractFileItemActionPlugin](kabstractfileitemactionplugin.md) instances

### void KFileItemActions::insertOpenWithActionsTo(QAction \**before*, QMenu \**topMenu*, const QStringList &*excludedDesktopEntryNames*) {#insertOpenWithActionsTo}

Generates the "Open With \<Application\>" actions, and inserts them in `menu`, before action `before`. If `before` is nullptr or doesn't exist in the menu the actions will be appended to the menu.

All actions are created as children of the menu.

No actions will be added if the "openwith" Kiosk action is not authorized (see KAuthorized::authorize()).

`before` the "open with" actions will be inserted before this action; if this action is nullptr or isn't available in `topMenu`, the "open with" actions will be appended

`menu` the [QMenu](https://doc.qt.io/qt-6/qmenu.html) where the actions will be added

`excludedDesktopEntryNames` list of desktop entry names that will not be shown

### \[signal\] void KFileItemActions::openWithDialogAboutToBeShown() {#openWithDialogAboutToBeShown}

Emitted before the "Open With" dialog is shown This is used e.g in folderview to close the folder peek popups on invoking the "Open With" menu action

### \[slot\] void KFileItemActions::runPreferredApplications(const KFileItemList &*fileOpenList*) {#runPreferredApplications}

Slot used to execute a list of files in their respective preferred application.

`fileOpenList` the list of KFileItems to open.

### \[since 6.32\] void KFileItemActions::setCurrentWorkingDirectory(const QUrl &*currentWorkingDirectory*) {#setCurrentWorkingDirectory}

Set the folder the actions are being requested for (e.g. the folder currently shown in the view), passed on to [KFileItemActionPluginV2::actionsForParent](kfileitemactionpluginv2.md#actionsForParent)() so plugins can tell whether the item list refers to this folder itself or to item(s) within it, and present different actions accordingly.

This function was introduced in Qt 6.32.

### void KFileItemActions::setItemListProperties(const KFileItemListProperties &*itemList*) {#setItemListProperties}

Sets all the data for the next instance of the popupmenu.

*See also* [KFileItemListProperties](../kiocore/kfileitemlistproperties.md)

### \[since 6.32\] void KFileItemActions::setParentObject(QObject \**parent*) {#setParentObject}

Set an additional [QObject](https://doc.qt.io/qt-6/qobject.html) to use as the owner for actions returned by plugins that implement [KFileItemActionPluginV2](kfileitemactionpluginv2.md), for use when no suitable [QWidget](https://doc.qt.io/qt-6/qwidget.html) is available to pass to [setParentWidget](kfileitemactions.md#setParentWidget)().

This is only needed by callers that have no widget at all (e.g. QML-based callers such as Plasma's desktop containment); when a parent widget has been set via [setParentWidget](kfileitemactions.md#setParentWidget)(), it is used instead and this is not needed.

This function was introduced in Qt 6.32.

### void KFileItemActions::setParentWidget(QWidget \**widget*) {#setParentWidget}

Set the parent widget for any dialogs being shown.

This should normally be your mainwindow, not a popup menu, so that it still exists even after the popup is closed (e.g. error message from KRun) and so that [QAction::setStatusTip](https://doc.qt.io/qt-6/qaction.html#statusTip-prop) can find a statusbar, too.
