---
title: "KParts::NavigationExtension Class"
description: "An extension to KParts::ReadOnlyPart, which allows a better integration of parts with browsers (in particular Konqueror)."
---

# KParts::NavigationExtension Class

An extension to [KParts::ReadOnlyPart](kparts-readonlypart.md), which allows a better integration of parts with browsers (in particular Konqueror). [More...](#details)

- **Header:** `#include <KParts/NavigationExtension>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Parts)`  
  `target_link_libraries(mytarget PRIVATE KF6::Parts)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kparts-navigationextension-members.md)

## Public Types

- [NavigationExtension::ActionGroupMap](#ActionGroupMap-typedef)
- [NavigationExtension::ActionSlotMap](#ActionSlotMap-typedef)
- [enum NavigationExtension::PopupFlag](#PopupFlag-enum)

## Properties

- [urlDropHandling : bool](#urlDropHandling-prop)

## Public Functions

- [NavigationExtension(KParts::ReadOnlyPart \*parent)](#NavigationExtension)
- [QString actionText(const char \*name) const](#actionText)
- [bool isActionEnabled(const char \*name) const](#isActionEnabled)
- [bool isURLDropHandlingEnabled() const](#isURLDropHandlingEnabled)
- [void pasteRequest()](#pasteRequest)
- [void restoreState(QDataStream &stream)](#restoreState)
- [void saveState(QDataStream &stream)](#saveState)
- [void setURLDropHandlingEnabled(bool enable)](#setURLDropHandlingEnabled)
- [int xOffset()](#xOffset)
- [int yOffset()](#yOffset)

## Signals

- [void addWebSideBar(const QUrl &url, const QString &name)](#addWebSideBar)
- [void createNewWindow(const QUrl &url)](#createNewWindow)
- [void enableAction(const char \*name, bool enabled)](#enableAction)
- [void infoMessage(const QString &)](#infoMessage)
- [void itemsRemoved(const KFileItemList &items)](#itemsRemoved)
- [void loadingProgress(int percent)](#loadingProgress)
- [void mouseOverInfo(const KFileItem &item)](#mouseOverInfo)
- [void moveTopLevelWidget(int x, int y)](#moveTopLevelWidget)
- [void openUrlNotify()](#openUrlNotify)
- [void openUrlRequest(const QUrl &url, const KParts::OpenUrlArguments &arguments = OpenUrlArguments())](#openUrlRequest)
- [void openUrlRequestDelayed(const QUrl &url, const KParts::OpenUrlArguments &arguments)](#openUrlRequestDelayed)
- [void popupMenu(const QPoint &global, const KFileItemList &items, const KParts::OpenUrlArguments &arguments = OpenUrlArguments(), KParts::NavigationExtension::PopupFlags flags = KParts::NavigationExtension::DefaultPopupItems, const KParts::NavigationExtension::ActionGroupMap &actionGroups = ActionGroupMap())](#popupMenu)
- [void popupMenu(const QPoint &global, const QUrl &url, mode\_t mode = static\_cast\<mode\_t\>(-1), const KParts::OpenUrlArguments &arguments = OpenUrlArguments(), KParts::NavigationExtension::PopupFlags flags = KParts::NavigationExtension::DefaultPopupItems, const KParts::NavigationExtension::ActionGroupMap &actionGroups = ActionGroupMap())](#popupMenu-1)
- [void requestFocus(KParts::ReadOnlyPart \*part)](#requestFocus)
- [void resizeTopLevelWidget(int w, int h)](#resizeTopLevelWidget)
- [void selectionInfo(const KFileItemList &items)](#selectionInfo)
- [void setActionText(const char \*name, const QString &text)](#setActionText)
- [void setIconUrl(const QUrl &url)](#setIconUrl)
- [void setLocationBarUrl(const QString &url)](#setLocationBarUrl)
- [void setPageSecurity(int)](#setPageSecurity)
- [void speedProgress(int bytesPerSecond)](#speedProgress)

## Static Public Members

- [KParts::NavigationExtension::ActionSlotMap \*actionSlotMap()](#actionSlotMap)
- [KParts::NavigationExtension \*childObject(QObject \*obj)](#childObject)

## Detailed Description {#details}

Remember that [ReadOnlyPart](kparts-readonlypart.md) only has openUrl([QUrl](https://doc.qt.io/qt-6/qurl.html)) and a few arguments() but not much more. For full-fledged browsing, we need much more than that, including enabling/disabling of standard actions (print, copy, paste...), allowing parts to save and restore their data into the back/forward history, allowing parts to control the location bar URL, to requests URLs to be opened by the hosting browser, etc.

The part developer needs to define its own class derived from BrowserExtension, to implement the virtual methods \[and the standard-actions slots, see below\].

The way to associate the BrowserExtension with the part is to simply create the BrowserExtension as a child of the part (in [QObject](https://doc.qt.io/qt-6/qobject.html)'s terms). The hosting application will look for it automatically.

Another aspect of the browser integration is that a set of standard actions are provided by the browser, but implemented by the part (for the actions it supports).

The following standard actions are defined by the host of the view:

\[selection-dependent actions\]

- cut : Copy selected items to clipboard and store 'not cut' in clipboard.
- copy : Copy selected items to clipboard and store 'cut' in clipboard.
- paste : Paste clipboard into view URL.
- pasteTo(const [QUrl](https://doc.qt.io/qt-6/qurl.html) &) : Paste clipboard into given URL.
- searchProvider : Lookup selected text at default search provider

\[normal actions\]

- None anymore.

The view defines a slot with the name of the action in order to implement the action. The browser will detect the slot automatically and connect its action to it when appropriate (i.e. when the view is active).

The selection-dependent actions are disabled by default and the view should enable them when the selection changes, emitting [enableAction](kparts-navigationextension.md#enableAction)().

The normal actions do not depend on the selection.

A special case is the configuration slots, not connected to any action directly.

\[configuration slot\]

- reparseConfiguration : Re-read configuration and apply it.
- disableScrolling: no scrollbars

## Member Type Documentation {#member-type-documentation}

### NavigationExtension::ActionGroupMap {#ActionGroupMap-typedef}

Associates a list of actions with a predefined name known by the host's popupmenu:

"editactions" for actions related text editing,

"linkactions" for actions related to hyperlinks,

"partactions" for any other actions provided by the part

### NavigationExtension::ActionSlotMap {#ActionSlotMap-typedef}

### enum NavigationExtension::PopupFlag {#PopupFlag-enum}

**flags NavigationExtension::PopupFlags**

Set of flags passed via the [popupMenu](kparts-navigationextension.md#popupMenu) signal, to ask for some items in the popup menu.

| Constant | Value | Description |
| --- | --- | --- |
| `KParts::NavigationExtension::DefaultPopupItems` | `0x0000` | Default value, no additional menu item |
| `KParts::NavigationExtension::ShowBookmark` | `0x0008` | Show "add to bookmarks" (usually not done on the local filesystem) |
| `KParts::NavigationExtension::ShowCreateDirectory` | `0x0010` | Show "create directory" (usually only done on the background of the view, or in hierarchical views like directory trees, where the new dir would be visible) |
| `KParts::NavigationExtension::ShowTextSelectionItems` | `0x0020` | Set when selecting text, for a popup that only contains text-related items. |
| `KParts::NavigationExtension::NoDeletion` | `0x0040` | Deletion, trashing and renaming not allowed (e.g. parent dir not writeable). (this is only needed if the protocol itself supports deletion, unlike e.g. HTTP) |
| `KParts::NavigationExtension::IsLink` | `0x0080` | Show "Bookmark This Link" and other link-related actions (linkactions merging group) |
| `KParts::NavigationExtension::ShowUrlOperations` | `0x0100` | Show copy, paste, as well as cut if NoDeletion is not set. |
| `KParts::NavigationExtension::ShowProperties` | `0x200` | Show "Properties" action (usually done by directory views) |

The `PopupFlags` type is a typedef for `QFlags<PopupFlag>. `It stores an OR combination of `PopupFlag` values.

## Property Documentation {#property-documentation}

### urlDropHandling : bool {#urlDropHandling-prop}

**Access functions:**

- `bool` **[isURLDropHandlingEnabled](kparts-navigationextension.md#isURLDropHandlingEnabled)**() const
- `void` **[setURLDropHandlingEnabled](kparts-navigationextension.md#setURLDropHandlingEnabled)**(`bool` *enable*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] NavigationExtension::NavigationExtension(KParts::ReadOnlyPart \**parent*) {#NavigationExtension}

Constructor

`parent` The [KParts::ReadOnlyPart](kparts-readonlypart.md) that this extension ... "extends" :)

### \[static\] KParts::NavigationExtension::ActionSlotMap \*NavigationExtension::actionSlotMap() {#actionSlotMap}

Returns a pointer to the static map containing the action names as keys and corresponding SLOT()'ified method names as data entries. The map is created if it doesn't exist yet.

This is very useful for the host component, when connecting the own signals with the extension's slots. Basically you iterate over the map, check if the extension implements the slot and connect to the slot using the data value of your map iterator. Checking if the extension implements a certain slot can be done like this:

```cpp
extension->metaObject()->slotNames().contains( actionName + "()" )
```

(note that `actionName` is the iterator's key value if already iterating over the action slot map, returned by this method)

Connecting to the slot can be done like this:

```cpp
connect( yourObject, SIGNAL( yourSignal() ),
         extension, mapIterator.data() )
```

(where "mapIterator" is your [ActionSlotMap](kparts-navigationextension.md#ActionSlotMap-typedef) iterator)

### QString NavigationExtension::actionText(const char \**name*) const {#actionText}

Returns the text of an action, if it was set explicitly by the part. When the [setActionText](kparts-navigationextension.md#setActionText) signal is emitted, the browserextension stores the text of the action internally, so that it's possible to query later for the text of the action, using this method.

*See also* [setActionText](kparts-navigationextension.md#setActionText)()

### \[signal\] void NavigationExtension::addWebSideBar(const QUrl &*url*, const QString &*name*) {#addWebSideBar}

Ask the hosting application to add a new HTML (aka Mozilla/Netscape) SideBar entry.

### \[static\] KParts::NavigationExtension \*NavigationExtension::childObject(QObject \**obj*) {#childObject}

Queries `obj` for a child object which inherits from this BrowserExtension class. Convenience method.

### \[signal\] void NavigationExtension::createNewWindow(const QUrl &*url*) {#createNewWindow}

Asks the hosting browser to open a new window for the given `url` and return a reference to the content part.

### \[signal\] void NavigationExtension::enableAction(const char \**name*, bool *enabled*) {#enableAction}

Enables or disable a standard action held by the browser.

See class documentation for the list of standard actions.

### \[signal\] void NavigationExtension::infoMessage(*const QString &*) {#infoMessage}

### bool NavigationExtension::isActionEnabled(const char \**name*) const {#isActionEnabled}

Returns the status (enabled/disabled) of an action. When the [enableAction](kparts-navigationextension.md#enableAction) signal is emitted, the browserextension stores the status of the action internally, so that it's possible to query later for the status of the action, using this method.

### bool NavigationExtension::isURLDropHandlingEnabled() const {#isURLDropHandlingEnabled}

Returns whether url drop handling is enabled. See [setURLDropHandlingEnabled](kparts-navigationextension.md#setURLDropHandlingEnabled) for more information about this property.

> **Note:** Getter function for property [urlDropHandling](kparts-navigationextension.md#urlDropHandling-prop).

### \[signal\] void NavigationExtension::itemsRemoved(const KFileItemList &*items*) {#itemsRemoved}

Inform the host about items that have been removed.

### \[signal\] void NavigationExtension::loadingProgress(int *percent*) {#loadingProgress}

Since the part emits the jobid in the started() signal, progress information is automatically displayed.

However, if you don't use a [KIO::Job](../kiocore/kio-job.md) in the part, you can use loadingProgress() and [speedProgress](kparts-navigationextension.md#speedProgress)() to display progress information.

### \[signal\] void NavigationExtension::mouseOverInfo(const KFileItem &*item*) {#mouseOverInfo}

Inform the hosting application that the user moved the mouse over an item. Used when the mouse is on an URL.

### \[signal\] void NavigationExtension::moveTopLevelWidget(int *x*, int *y*) {#moveTopLevelWidget}

Ask the hosting application to move the top level widget.

### \[signal\] void NavigationExtension::openUrlNotify() {#openUrlNotify}

Tells the hosting browser that the part opened a new URL (which can be queried via KParts::Part::url().

This helps the browser to update/create an entry in the history. The part may not emit this signal together with [openUrlRequest](kparts-navigationextension.md#openUrlRequest)().

Emit [openUrlRequest](kparts-navigationextension.md#openUrlRequest)() if you want the browser to handle a URL the user asked to open (from within your part/document). This signal however is useful if you want to handle URLs all yourself internally, while still telling the hosting browser about new opened URLs, in order to provide a proper history functionality to the user.

An example of usage is a html rendering component which wants to emit this signal when a child frame document changed its URL.

Conclusion: you probably want to use [openUrlRequest](kparts-navigationextension.md#openUrlRequest)() instead.

### \[signal\] void NavigationExtension::openUrlRequest(const QUrl &*url*, const KParts::OpenUrlArguments &*arguments* = KParts::OpenUrlArguments()) {#openUrlRequest}

Asks the host (browser) to open `url`.

To set a reload, the x and y offsets, the service type etc., fill in the appropriate fields in the `arguments` structure. Hosts should not connect to this signal but to [openUrlRequestDelayed](kparts-navigationextension.md#openUrlRequestDelayed)().

### \[signal\] void NavigationExtension::openUrlRequestDelayed(const QUrl &*url*, const KParts::OpenUrlArguments &*arguments*) {#openUrlRequestDelayed}

This signal is emitted when [openUrlRequest](kparts-navigationextension.md#openUrlRequest)() is called, after a 0-seconds timer. This allows the caller to terminate what it's doing first, before (usually) being destroyed. Parts should never use this signal, hosts should only connect to this signal.

### void NavigationExtension::pasteRequest() {#pasteRequest}

Asks the hosting browser to perform a paste (using [openUrlRequestDelayed](kparts-navigationextension.md#openUrlRequestDelayed)())

### \[signal\] void NavigationExtension::popupMenu(const QPoint &*global*, const KFileItemList &*items*, const KParts::OpenUrlArguments &*arguments* = KParts::OpenUrlArguments(), KParts::NavigationExtension::PopupFlags *flags* = KParts::NavigationExtension::DefaultPopupItems, const KParts::NavigationExtension::ActionGroupMap &*actionGroups* = ActionGroupMap()) {#popupMenu}

Emit this to make the browser show a standard popup menu for the files `items`.

`global` global coordinates where the popup should be shown

`items` list of file items which the popup applies to

`args` [OpenUrlArguments](kparts-openurlarguments.md), mostly for metadata here

`flags` enables/disables certain builtin actions in the popupmenu

`actionGroups` named groups of actions which should be inserted into the popup, see [ActionGroupMap](kparts-navigationextension.md#ActionGroupMap-typedef)

> **Note:** This signal is overloaded. To connect to this signal:
>
> ```
> // Connect using qOverload:
> connect(navigationExtension, qOverload<const QPoint &, const KFileItemList &, const KParts::OpenUrlArguments &, KParts::NavigationExtension::PopupFlags, const KParts::NavigationExtension::ActionGroupMap &>(&NavigationExtension::popupMenu),
>         receiver, &ReceiverClass::slot);
>
> // Or using a lambda:
> connect(navigationExtension, qOverload<const QPoint &, const KFileItemList &, const KParts::OpenUrlArguments &, KParts::NavigationExtension::PopupFlags, const KParts::NavigationExtension::ActionGroupMap &>(&NavigationExtension::popupMenu),
>         this, [](const QPoint &global, const KFileItemList &items, const KParts::OpenUrlArguments &arguments, KParts::NavigationExtension::PopupFlags flags, const KParts::NavigationExtension::ActionGroupMap &actionGroups) { /* handle popupMenu */ });
> ```
>
> For more examples and approaches, see [connecting to overloaded signals](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-signals).

### \[signal\] void NavigationExtension::popupMenu(const QPoint &*global*, const QUrl &*url*, mode\_t *mode* = static\_cast\<mode\_t\>(-1), const KParts::OpenUrlArguments &*arguments* = KParts::OpenUrlArguments(), KParts::NavigationExtension::PopupFlags *flags* = KParts::NavigationExtension::DefaultPopupItems, const KParts::NavigationExtension::ActionGroupMap &*actionGroups* = ActionGroupMap()) {#popupMenu-1}

Emit this to make the browser show a standard popup menu for the given `url`.

Give as much information about this URL as possible, like `arguments.mimeType` and the file type `mode`

`global` global coordinates where the popup should be shown

`url` the URL this popup applies to

`mode` the file type of the url (S\_IFREG, S\_IFDIR...)

`arguments` [OpenUrlArguments](kparts-openurlarguments.md), set the mimetype of the URL using setMimeType()

`flags` enables/disables certain builtin actions in the popupmenu

`actionGroups` named groups of actions which should be inserted into the popup, see [ActionGroupMap](kparts-navigationextension.md#ActionGroupMap-typedef)

> **Note:** This signal is overloaded. To connect to this signal:
>
> ```
> // Connect using qOverload:
> connect(navigationExtension, qOverload<const QPoint &, const QUrl &, mode_t, const KParts::OpenUrlArguments &, KParts::NavigationExtension::PopupFlags, const KParts::NavigationExtension::ActionGroupMap &>(&NavigationExtension::popupMenu),
>         receiver, &ReceiverClass::slot);
>
> // Or using a lambda:
> connect(navigationExtension, qOverload<const QPoint &, const QUrl &, mode_t, const KParts::OpenUrlArguments &, KParts::NavigationExtension::PopupFlags, const KParts::NavigationExtension::ActionGroupMap &>(&NavigationExtension::popupMenu),
>         this, [](const QPoint &global, const QUrl &url, mode_t mode, const KParts::OpenUrlArguments &arguments, KParts::NavigationExtension::PopupFlags flags, const KParts::NavigationExtension::ActionGroupMap &actionGroups) { /* handle popupMenu */ });
> ```
>
> For more examples and approaches, see [connecting to overloaded signals](https://doc.qt.io/qt-6/signalsandslots.html#connecting-overloaded-signals).

### \[signal\] void NavigationExtension::requestFocus(KParts::ReadOnlyPart \**part*) {#requestFocus}

Ask the hosting application to focus `part`.

### \[signal\] void NavigationExtension::resizeTopLevelWidget(int *w*, int *h*) {#resizeTopLevelWidget}

Ask the hosting application to resize the top level widget.

### \[virtual\] void NavigationExtension::restoreState(QDataStream &*stream*) {#restoreState}

Used by the browser to restore the view in the state it was when we left it.

If you saved additional properties, reimplement it but don't forget to call the parent method (probably first).

### \[virtual\] void NavigationExtension::saveState(QDataStream &*stream*) {#saveState}

Used by the browser to save the current state of the view (in order to restore it if going back in navigation).

If you want to save additional properties, reimplement it but don't forget to call the parent method (probably first).

### \[signal\] void NavigationExtension::selectionInfo(const KFileItemList &*items*) {#selectionInfo}

Inform the hosting application about the current selection. Used when a set of files/URLs is selected (with full information about those URLs, including size, permissions etc.)

### \[signal\] void NavigationExtension::setActionText(const char \**name*, const QString &*text*) {#setActionText}

Change the text of a standard action held by the browser. This can be used to change "Paste" into "Paste Image" for instance.

See class documentation for the list of standard actions.

*See also* [actionText](kparts-navigationextension.md#actionText)()

### \[signal\] void NavigationExtension::setIconUrl(const QUrl &*url*) {#setIconUrl}

Sets the URL of an icon for the currently displayed page.

### \[signal\] void NavigationExtension::setLocationBarUrl(const QString &*url*) {#setLocationBarUrl}

Updates the URL shown in the browser's location bar to `url`.

### \[signal\] void NavigationExtension::setPageSecurity(*int*) {#setPageSecurity}

Tell the host (browser) about security state of current page enum PageSecurity { NotCrypted, Encrypted, Mixed };

### void NavigationExtension::setURLDropHandlingEnabled(bool *enable*) {#setURLDropHandlingEnabled}

Enables or disables url drop handling. URL drop handling is a property describing whether the hosting shell component is allowed to install an event filter on the part's widget, to listen for URI drop events. Set it to true if you are exporting a BrowserExtension implementation and do not provide any special URI drop handling. If set to false you can be sure to receive all those URI drop events unfiltered. Also note that the implementation as of Konqueror installs the event filter only on the part's widget itself, not on child widgets.

> **Note:** Setter function for property [urlDropHandling](kparts-navigationextension.md#urlDropHandling-prop).

*See also* [isURLDropHandlingEnabled](kparts-navigationextension.md#isURLDropHandlingEnabled)()

### \[signal\] void NavigationExtension::speedProgress(int *bytesPerSecond*) {#speedProgress}

*See also* [loadingProgress](kparts-navigationextension.md#loadingProgress)

### \[virtual\] int NavigationExtension::xOffset() {#xOffset}

Returns the current x offset.

For a scrollview, implement this using contentsX().

### \[virtual\] int NavigationExtension::yOffset() {#yOffset}

Returns the current y offset.

For a scrollview, implement this using contentsY().
