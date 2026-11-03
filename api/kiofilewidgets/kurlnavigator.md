---
title: "KUrlNavigator Class"
description: "Widget that allows to navigate through the paths of an URL."
---

# KUrlNavigator Class

Widget that allows to navigate through the paths of an URL. [More...](#details)

- **Header:** `#include <KUrlNavigator>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOFileWidgets)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kurlnavigator-members.md)

## Public Functions

- [KUrlNavigator(QWidget \*parent = nullptr)](#KUrlNavigator)
- [KUrlNavigator(KFilePlacesModel \*placesModel, const QUrl &url, QWidget \*parent)](#KUrlNavigator-1)
- [QWidget \*badgeWidget() const](#badgeWidget) (since 6.2)
- [QWidget \*dropWidget() const](#dropWidget)
- [KUrlComboBox \*editor() const](#editor)
- [bool goBack()](#goBack)
- [bool goForward()](#goForward)
- [void goHome()](#goHome)
- [bool goUp()](#goUp)
- [int historyIndex() const](#historyIndex)
- [int historySize() const](#historySize)
- [QUrl homeUrl() const](#homeUrl)
- [bool isActive() const](#isActive)
- [bool isBackgroundEnabled() const](#isBackgroundEnabled) (since 6.14)
- [bool isPlacesSelectorVisible() const](#isPlacesSelectorVisible)
- [bool isUrlEditable() const](#isUrlEditable)
- [QByteArray locationState(int historyIndex = -1) const](#locationState)
- [QUrl locationUrl(int historyIndex = -1) const](#locationUrl)
- [void saveLocationState(const QByteArray &state)](#saveLocationState)
- [void setActive(bool active)](#setActive)
- [void setBackgroundEnabled(bool enabled)](#setBackgroundEnabled) (since 6.14)
- [void setBadgeWidget(QWidget \*widget)](#setBadgeWidget) (since 6.2)
- [void setHighlightFocusIndicator(bool show)](#setHighlightFocusIndicator) (since 6.21)
- [void setHomeUrl(const QUrl &url)](#setHomeUrl)
- [void setPlacesSelectorVisible(bool visible)](#setPlacesSelectorVisible)
- [void setShowFullPath(bool show)](#setShowFullPath)
- [void setShowHiddenFolders(bool showHiddenFolders)](#setShowHiddenFolders)
- [void setSortHiddenFoldersLast(bool sortHiddenFoldersLast)](#setSortHiddenFoldersLast)
- [void setSupportedSchemes(const QStringList &schemes)](#setSupportedSchemes)
- [void setUrlEditable(bool editable)](#setUrlEditable)
- [bool showFullPath() const](#showFullPath)
- [bool showHiddenFolders() const](#showHiddenFolders)
- [bool sortHiddenFoldersLast() const](#sortHiddenFoldersLast)
- [QStringList supportedSchemes() const](#supportedSchemes)
- [QUrl uncommittedUrl() const](#uncommittedUrl)

## Public Slots

- [void requestActivation()](#requestActivation)
- [void setLocationUrl(const QUrl &url)](#setLocationUrl)

## Signals

- [void activated()](#activated)
- [void activeTabRequested(const QUrl &url)](#activeTabRequested)
- [void editableStateChanged(bool editable)](#editableStateChanged)
- [void historyChanged()](#historyChanged)
- [void layoutChanged()](#layoutChanged) (since 6.11)
- [void newWindowRequested(const QUrl &url)](#newWindowRequested)
- [void returnPressed()](#returnPressed)
- [void tabRequested(const QUrl &url)](#tabRequested)
- [void urlAboutToBeChanged(const QUrl &newUrl)](#urlAboutToBeChanged)
- [void urlChanged(const QUrl &url)](#urlChanged)
- [void urlSelectionRequested(const QUrl &url)](#urlSelectionRequested)
- [void urlsDropped(const QUrl &destination, QDropEvent \*event)](#urlsDropped)

## Detailed Description {#details}

The URL navigator offers two modes:

- Editable: The URL of the location is editable inside an editor. By pressing RETURN the URL will get activated.
- Non editable ("breadcrumb view"): The URL of the location is represented by a number of buttons, where each button represents a path of the URL. By clicking on a button the path will get activated. This mode also supports drag and drop of items.

The mode can be changed by clicking on the empty area of the URL navigator. It is recommended that the application remembers the setting or allows to configure the default mode (see [KUrlNavigator::setUrlEditable](kurlnavigator.md#setUrlEditable)()).

The URL navigator remembers the URL history during navigation and allows to go back and forward within this history.

In the non editable mode ("breadcrumb view") it can be configured whether the full path should be shown. It is recommended that the application remembers the setting or allows to configure the default mode (see [KUrlNavigator::setShowFullPath](kurlnavigator.md#setShowFullPath)()).

The typical usage of the [KUrlNavigator](kurlnavigator.md) is:

- Create an instance providing a places model and an URL.
- Create an instance of [QAbstractItemView](https://doc.qt.io/qt-6/qabstractitemview.html) which shows the content of the URL given by the URL navigator.
- Connect to the signal [KUrlNavigator::urlChanged](kurlnavigator.md#urlChanged)() and synchronize the content of [QAbstractItemView](https://doc.qt.io/qt-6/qabstractitemview.html) with the URL given by the URL navigator.

It is recommended, that the application remembers the state of the [QAbstractItemView](https://doc.qt.io/qt-6/qabstractitemview.html) when the URL has been changed. This allows to restore the view state when going back in history. [KUrlNavigator](kurlnavigator.md) offers support for remembering the view state:

- The signal [urlAboutToBeChanged](kurlnavigator.md#urlAboutToBeChanged)() will be emitted before the URL change takes places. This allows the application to store the view state by [KUrlNavigator::saveLocationState](kurlnavigator.md#saveLocationState)().
- The signal [urlChanged](kurlnavigator.md#urlChanged)() will be emitted after the URL change took place. This allows the application to restore the view state by getting the values from [KUrlNavigator::locationState](kurlnavigator.md#locationState)().

## Member Function Documentation {#member-function-documentation}

### KUrlNavigator::KUrlNavigator(QWidget \**parent* = nullptr) {#KUrlNavigator}

### KUrlNavigator::KUrlNavigator(KFilePlacesModel \**placesModel*, const QUrl &*url*, QWidget \**parent*) {#KUrlNavigator-1}

`placesModel` Model for the places which are selectable inside a menu. A place can be a bookmark or a device. If it is 0, no places selector is displayed.

`url` URL which is used for the navigation or editing.

`parent` Parent widget.

### \[signal\] void KUrlNavigator::activated() {#activated}

Is emitted, if the URL navigator has been activated by an user interaction

*See also* [setActive](kurlnavigator.md#setActive)()

### \[signal\] void KUrlNavigator::activeTabRequested(const QUrl &*url*) {#activeTabRequested}

Is emitted if the URL `url` should be opened in a new active tab because the user clicked on a breadcrumb with the middle mouse button with the shift modifier pressed or left-clicked with both the ctrl and shift modifiers pressed or pressed return with both the alt and shift modifiers pressed.

### \[since 6.2\] QWidget \*KUrlNavigator::badgeWidget() const {#badgeWidget}

Returns the badge widget set by [setBadgeWidget](kurlnavigator.md#setBadgeWidget)(). If [setBadgeWidget](kurlnavigator.md#setBadgeWidget)() hasn't been called, returns nullptr.

This function was introduced in Qt 6.2.

*See also* [setBadgeWidget](kurlnavigator.md#setBadgeWidget)()

### QWidget \*KUrlNavigator::dropWidget() const {#dropWidget}

The child widget that received the [QDropEvent](https://doc.qt.io/qt-6/qdropevent.html) when dropping on the URL navigator. You can pass this widget to KJobWidgets::setWindow() if you need to show a drop menu with [KIO::drop](../kiowidgets/kio-dropjob.md#drop)().

Returns Child widget that has received the last drop event, or nullptr if nothing has been dropped yet on the URL navigator.

*See also* [KIO::drop](../kiowidgets/kio-dropjob.md#drop)()

### \[signal\] void KUrlNavigator::editableStateChanged(bool *editable*) {#editableStateChanged}

Is emitted, if the editable state for the URL has been changed (see [KUrlNavigator::setUrlEditable](kurlnavigator.md#setUrlEditable)()).

### KUrlComboBox \*KUrlNavigator::editor() const {#editor}

Returns the used editor when the navigator is in the edit mode

*See also* [KUrlNavigator::setUrlEditable](kurlnavigator.md#setUrlEditable)()

### bool KUrlNavigator::goBack() {#goBack}

Goes back one step in the URL history. The signals [KUrlNavigator::urlAboutToBeChanged](kurlnavigator.md#urlAboutToBeChanged)(), [KUrlNavigator::urlChanged](kurlnavigator.md#urlChanged)() and [KUrlNavigator::historyChanged](kurlnavigator.md#historyChanged)() are emitted if true is returned. False is returned if the beginning of the history has already been reached and hence going back was not possible. The history index (see [KUrlNavigator::historyIndex](kurlnavigator.md#historyIndex)()) is increased by one if the operation was successful.

### bool KUrlNavigator::goForward() {#goForward}

Goes forward one step in the URL history. The signals [KUrlNavigator::urlAboutToBeChanged](kurlnavigator.md#urlAboutToBeChanged)(), [KUrlNavigator::urlChanged](kurlnavigator.md#urlChanged)() and [KUrlNavigator::historyChanged](kurlnavigator.md#historyChanged)() are emitted if true is returned. False is returned if the end of the history has already been reached and hence going forward was not possible. The history index (see [KUrlNavigator::historyIndex](kurlnavigator.md#historyIndex)()) is decreased by one if the operation was successful.

### void KUrlNavigator::goHome() {#goHome}

Goes to the home URL and remembers the old URL in the history. The signals [KUrlNavigator::urlAboutToBeChanged](kurlnavigator.md#urlAboutToBeChanged)(), [KUrlNavigator::urlChanged](kurlnavigator.md#urlChanged)() and [KUrlNavigator::historyChanged](kurlnavigator.md#historyChanged)() are emitted.

*See also* [setHomeUrl](kurlnavigator.md#setHomeUrl)()

### bool KUrlNavigator::goUp() {#goUp}

Goes up one step of the URL path and remembers the old path in the history. The signals [KUrlNavigator::urlAboutToBeChanged](kurlnavigator.md#urlAboutToBeChanged)(), [KUrlNavigator::urlChanged](kurlnavigator.md#urlChanged)() and [KUrlNavigator::historyChanged](kurlnavigator.md#historyChanged)() are emitted if true is returned. False is returned if going up was not possible as the root has been reached.

### \[signal\] void KUrlNavigator::historyChanged() {#historyChanged}

Is emitted, if the history has been changed. Usually the history is changed if a new URL has been selected.

### int KUrlNavigator::historyIndex() const {#historyIndex}

Returns the history index of the current location, where 0 \<= history index \< [KUrlNavigator::historySize](kurlnavigator.md#historySize)(). 0 is the most recent history entry.

### int KUrlNavigator::historySize() const {#historySize}

Returns the amount of locations in the history. The data for each location can be retrieved by [KUrlNavigator::locationUrl](kurlnavigator.md#locationUrl)() and [KUrlNavigator::locationState](kurlnavigator.md#locationState)().

### QUrl KUrlNavigator::homeUrl() const {#homeUrl}

*See also* [setHomeUrl](kurlnavigator.md#setHomeUrl)()

### bool KUrlNavigator::isActive() const {#isActive}

Returns `true`, if the URL navigator is in the active mode.

*See also* [setActive](kurlnavigator.md#setActive)()

### \[since 6.14\] bool KUrlNavigator::isBackgroundEnabled() const {#isBackgroundEnabled}

Returns true if the background and frame is being painted.

This function was introduced in Qt 6.14.

### bool KUrlNavigator::isPlacesSelectorVisible() const {#isPlacesSelectorVisible}

Returns `true`, if the places selector is visible.

### bool KUrlNavigator::isUrlEditable() const {#isUrlEditable}

Returns `true`, if the URL is editable within a line editor. If false is returned, each part of the URL is presented by a button for fast navigation ("breadcrumb view").

### \[signal, since 6.11\] void KUrlNavigator::layoutChanged() {#layoutChanged}

The internal layout and graphical representation of components has changed, either after an url change or after a switch between editable mode and breadcrumb mode

This function was introduced in Qt 6.11.

### QByteArray KUrlNavigator::locationState(int *historyIndex* = -1) const {#locationState}

Returns Location state given by `historyIndex`. If `historyIndex` is smaller than 0, the state of the current location is returned.

*See also* [KUrlNavigator::saveLocationState](kurlnavigator.md#saveLocationState)()

### QUrl KUrlNavigator::locationUrl(int *historyIndex* = -1) const {#locationUrl}

Returns URL of the location given by the `historyIndex`. If `historyIndex` is smaller than 0, the URL of the current location is returned.

*See also* [setLocationUrl](kurlnavigator.md#setLocationUrl)()

### \[signal\] void KUrlNavigator::newWindowRequested(const QUrl &*url*) {#newWindowRequested}

Is emitted if the URL `url` should be opened in a new window because the user left-clicked on a breadcrumb with the shift modifier pressed or pressed return with the shift modifier pressed.

### \[slot\] void KUrlNavigator::requestActivation() {#requestActivation}

Activates the URL navigator ([KUrlNavigator::isActive](kurlnavigator.md#isActive)() will return true) and emits the signal [KUrlNavigator::activated](kurlnavigator.md#activated)().

*See also* [setActive](kurlnavigator.md#setActive)()

### \[signal\] void KUrlNavigator::returnPressed() {#returnPressed}

This signal is emitted when the Return or Enter key is pressed.

### void KUrlNavigator::saveLocationState(const QByteArray &*state*) {#saveLocationState}

Saves the location state described by `state` for the current location. It is recommended that at least the scroll position of a view is remembered and restored when traversing through the history. Saving the location state should be done when the signal [KUrlNavigator::urlAboutToBeChanged](kurlnavigator.md#urlAboutToBeChanged)() has been emitted. Restoring the location state (see [KUrlNavigator::locationState](kurlnavigator.md#locationState)()) should be done when the signal [KUrlNavigator::urlChanged](kurlnavigator.md#urlChanged)() has been emitted.

Example:

```cpp
QByteArray state;
QDataStream data(&state, QIODevice::WriteOnly);
data << QPoint(x, y);
data << ...;
...
urlNavigator->saveLocationState(state);
```

### void KUrlNavigator::setActive(bool *active*) {#setActive}

Set the URL navigator to the active mode, if `active` is true. The active mode is default. The inactive mode only differs visually from the active mode, no change of the behavior is given.

Using the URL navigator in the inactive mode is useful when having split views, where the inactive view is indicated by an inactive URL navigator visually.

*See also* [isActive](kurlnavigator.md#isActive)()

### \[since 6.14\] void KUrlNavigator::setBackgroundEnabled(bool *enabled*) {#setBackgroundEnabled}

Sets whether painting of the background and frame is enabled.

In frameless styles, its recommended to set the background to disabled.

This function was introduced in Qt 6.14.

*See also* [isBackgroundEnabled](kurlnavigator.md#isBackgroundEnabled)()

### \[since 6.2\] void KUrlNavigator::setBadgeWidget(QWidget \**widget*) {#setBadgeWidget}

Puts `widget` to the right of the breadcrumb.

[KUrlNavigator](kurlnavigator.md) takes ownership over `widget`. Any existing badge widget is deleted.

> **Note:** There is no limit to the size of the badge widget. If your badge widget is taller than other controls in [KUrlNavigator](kurlnavigator.md), then the whole [KUrlNavigator](kurlnavigator.md) will be resized to accommodate it. Also, [KUrlNavigator](kurlnavigator.md) has fixed minimumWidth of 100, so if your badge widget is too wide, it might be clipped when the space is tight. You might want to call [KUrlNavigator::setMinimumWidth](https://doc.qt.io/qt-6/qwidget.html#minimumWidth-prop)() with a larger value in that case. In general, it is recommended to keep the badge widget small and not expanding, to avoid layout issues.

This function was introduced in Qt 6.2.

*See also* [badgeWidget](kurlnavigator.md#badgeWidget)()

### \[since 6.21\] void KUrlNavigator::setHighlightFocusIndicator(bool *show*) {#setHighlightFocusIndicator}

Sets whether to show additional focus indicator which has been implemented as thick line rounded at the ends and clipped at the bottom drawing in accent color (active or inactive - based on m\_active state).

This function was introduced in Qt 6.21.

### void KUrlNavigator::setHomeUrl(const QUrl &*url*) {#setHomeUrl}

Sets the home URL used by [KUrlNavigator::goHome](kurlnavigator.md#goHome)(). If no home URL is set, the default home path of the user is used.

*See also* [homeUrl](kurlnavigator.md#homeUrl)()

### \[slot\] void KUrlNavigator::setLocationUrl(const QUrl &*url*) {#setLocationUrl}

Sets the location to `url`. The old URL is added to the history. The signals [KUrlNavigator::urlAboutToBeChanged](kurlnavigator.md#urlAboutToBeChanged)(), [KUrlNavigator::urlChanged](kurlnavigator.md#urlChanged)() and [KUrlNavigator::historyChanged](kurlnavigator.md#historyChanged)() are emitted. Use [KUrlNavigator::locationUrl](kurlnavigator.md#locationUrl)() to read the location.

*See also* [locationUrl](kurlnavigator.md#locationUrl)()

### void KUrlNavigator::setPlacesSelectorVisible(bool *visible*) {#setPlacesSelectorVisible}

Sets the places selector visible, if `visible` is true. The places selector allows to select the places provided by the places model passed in the constructor. Per default the places selector is visible.

*See also* [isPlacesSelectorVisible](kurlnavigator.md#isPlacesSelectorVisible)()

### void KUrlNavigator::setShowFullPath(bool *show*) {#setShowFullPath}

Shows the full path of the URL even if a place represents a part of the URL. Assuming that a place called "Pictures" uses the URL /home/user/Pictures. An URL like /home/user/Pictures/2008 is shown as \[Pictures\] \> \[2008\] in the breadcrumb view, if showing the full path is turned off. If showing the full path is turned on, the URL is shown as \[/\] \> \[home\] \> \[Pictures\] \> \[2008\].

*See also* [showFullPath](kurlnavigator.md#showFullPath)()

### void KUrlNavigator::setShowHiddenFolders(bool *showHiddenFolders*) {#setShowHiddenFolders}

Sets whether to show hidden folders in the subdirectories popup.

*See also* [showHiddenFolders](kurlnavigator.md#showHiddenFolders)()

### void KUrlNavigator::setSortHiddenFoldersLast(bool *sortHiddenFoldersLast*) {#setSortHiddenFoldersLast}

Sets whether to sort hidden folders in the subdirectories popup last.

*See also* [sortHiddenFoldersLast](kurlnavigator.md#sortHiddenFoldersLast)()

### void KUrlNavigator::setSupportedSchemes(const QStringList &*schemes*) {#setSupportedSchemes}

Set the URL schemes that the navigator should allow navigating to.

If the passed list is empty, all schemes are supported. Examples for schemes are `"file"` or `"ftp"`.

*See also* [supportedSchemes](kurlnavigator.md#supportedSchemes)(), [QFileDialog::setSupportedSchemes](https://doc.qt.io/qt-6/qfiledialog.html#supportedSchemes-prop)

### void KUrlNavigator::setUrlEditable(bool *editable*) {#setUrlEditable}

Allows to edit the URL of the navigation bar if `editable` is true, and sets the focus accordingly. If `editable` is false, each part of the URL is presented by a button for a fast navigation ("breadcrumb view").

*See also* [isUrlEditable](kurlnavigator.md#isUrlEditable)()

### bool KUrlNavigator::showFullPath() const {#showFullPath}

Returns `true`, if the full path of the URL should be shown in the breadcrumb view.

*See also* [setShowFullPath](kurlnavigator.md#setShowFullPath)()

### bool KUrlNavigator::showHiddenFolders() const {#showHiddenFolders}

Returns whether to show hidden folders in the subdirectories popup.

*See also* [setShowHiddenFolders](kurlnavigator.md#setShowHiddenFolders)()

### bool KUrlNavigator::sortHiddenFoldersLast() const {#sortHiddenFoldersLast}

Returns whether to sort hidden folders in the subdirectories popup last.

*See also* [setSortHiddenFoldersLast](kurlnavigator.md#setSortHiddenFoldersLast)()

### QStringList KUrlNavigator::supportedSchemes() const {#supportedSchemes}

Returns the URL schemes that the navigator should allow navigating to.

If the returned list is empty, all schemes are supported.

*See also* [setSupportedSchemes](kurlnavigator.md#setSupportedSchemes)(), [QFileDialog::supportedSchemes](https://doc.qt.io/qt-6/qfiledialog.html#supportedSchemes-prop)

### \[signal\] void KUrlNavigator::tabRequested(const QUrl &*url*) {#tabRequested}

Is emitted if the URL `url` should be opened in a new inactive tab because the user clicked on a breadcrumb with the middle mouse button or left-clicked with the ctrl modifier pressed or pressed return with the alt modifier pressed.

### QUrl KUrlNavigator::uncommittedUrl() const {#uncommittedUrl}

Returns the currently entered, but not accepted URL. It is possible that the returned URL is not valid.

### \[signal\] void KUrlNavigator::urlAboutToBeChanged(const QUrl &*newUrl*) {#urlAboutToBeChanged}

Is emitted, before the location URL is going to be changed to `newUrl`. The signal [KUrlNavigator::urlChanged](kurlnavigator.md#urlChanged)() will be emitted after the change has been done. Connecting to this signal is useful to save the state of a view with [KUrlNavigator::saveLocationState](kurlnavigator.md#saveLocationState)().

### \[signal\] void KUrlNavigator::urlChanged(const QUrl &*url*) {#urlChanged}

Is emitted, if the location URL has been changed e. g. by the user.

*See also* setUrl()

### \[signal\] void KUrlNavigator::urlSelectionRequested(const QUrl &*url*) {#urlSelectionRequested}

When the URL is changed and the new URL (e.g. /home/user1/) is a parent of the previous URL (e.g. /home/user1/data/stuff), then this signal is emitted and `url` is set to the child directory of the new URL which is an ancestor of the old URL (in the example paths this would be /home/user1/data/). This signal allows file managers to pre-select the directory that the user is navigating up from.

### \[signal\] void KUrlNavigator::urlsDropped(const QUrl &*destination*, QDropEvent \**event*) {#urlsDropped}

Is emitted if a dropping has been done above the destination `destination`. The receiver must accept the drop event if the dropped data can be handled.
