---
title: "KFilePlacesModel Class"
description: "> Note: All functions in this class are reentrant."
---

# KFilePlacesModel Class

> **Note:** All functions in this class are reentrant. [More...](#details)

- **Header:** `#include <KFilePlacesModel>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOFileWidgets)`
- **Inherits:** [QAbstractItemModel](https://doc.qt.io/qt-6/qabstractitemmodel.html)

[List of all members, including inherited members](kfileplacesmodel-members.md)

## Public Types

- [enum KFilePlacesModel::AdditionalRoles](#AdditionalRoles-enum)
- [enum KFilePlacesModel::DeviceAccessibility](#DeviceAccessibility-enum)
- [enum KFilePlacesModel::GroupType](#GroupType-enum)

## Properties

- [supportedSchemes : QStringList](#supportedSchemes-prop)

## Public Functions

- [KFilePlacesModel(QObject \*parent = nullptr)](#KFilePlacesModel)
- [void addPlace(const QString &text, const QUrl &url, const QString &iconName = QString(), const QString &appName = QString())](#addPlace)
- [void addPlace(const QString &text, const QUrl &url, const QString &iconName, const QString &appName, const QModelIndex &after)](#addPlace-1)
- [KBookmark bookmarkForIndex(const QModelIndex &index) const](#bookmarkForIndex)
- [KBookmark bookmarkForUrl(const QUrl &searchUrl) const](#bookmarkForUrl)
- [QModelIndex closestItem(const QUrl &url) const](#closestItem)
- [KFilePlacesModel::DeviceAccessibility deviceAccessibility(const QModelIndex &index) const](#deviceAccessibility)
- [Solid::Device deviceForIndex(const QModelIndex &index) const](#deviceForIndex)
- [void editPlace(const QModelIndex &index, const QString &text, const QUrl &url, const QString &iconName = QString(), const QString &appName = QString())](#editPlace)
- [QAction \*ejectActionForIndex(const QModelIndex &index) const](#ejectActionForIndex)
- [QModelIndexList groupIndexes(const KFilePlacesModel::GroupType type) const](#groupIndexes)
- [KFilePlacesModel::GroupType groupType(const QModelIndex &index) const](#groupType)
- [int hiddenCount() const](#hiddenCount)
- [QIcon icon(const QModelIndex &index) const](#icon)
- [bool isDevice(const QModelIndex &index) const](#isDevice)
- [bool isEjectAllowed(const QModelIndex &index) const](#isEjectAllowed)
- [bool isGroupHidden(const KFilePlacesModel::GroupType type) const](#isGroupHidden)
- [bool isGroupHidden(const QModelIndex &index) const](#isGroupHidden-1)
- [bool isHidden(const QModelIndex &index) const](#isHidden)
- [bool isTeardownAllowed(const QModelIndex &index) const](#isTeardownAllowed)
- [bool isTeardownOverlayRecommended(const QModelIndex &index) const](#isTeardownOverlayRecommended)
- [bool movePlace(int itemRow, int row)](#movePlace)
- [QAction \*openRecentOption(const QModelIndex &index) const](#openRecentOption) (since 6.20)
- [QAction \*partitionActionForIndex(const QModelIndex &index) const](#partitionActionForIndex)
- [QString placeCollapsedUrl(const QUrl &url) const](#placeCollapsedUrl) (since 6.23)
- [void refresh() const](#refresh)
- [void removePlace(const QModelIndex &index) const](#removePlace)
- [void requestEject(const QModelIndex &index)](#requestEject)
- [void requestSetup(const QModelIndex &index)](#requestSetup)
- [void requestTeardown(const QModelIndex &index)](#requestTeardown)
- [void setGroupHidden(const KFilePlacesModel::GroupType type, bool hidden)](#setGroupHidden)
- [void setPlaceHidden(const QModelIndex &index, bool hidden)](#setPlaceHidden)
- [void setSupportedSchemes(const QStringList &schemes)](#setSupportedSchemes)
- [bool setupNeeded(const QModelIndex &index) const](#setupNeeded)
- [QStringList supportedSchemes() const](#supportedSchemes)
- [QAction \*teardownActionForIndex(const QModelIndex &index) const](#teardownActionForIndex)
- [QString text(const QModelIndex &index) const](#text)
- [QUrl url(const QModelIndex &index) const](#url)

## Signals

- [void errorMessage(const QString &message)](#errorMessage)
- [void groupHiddenChanged(KFilePlacesModel::GroupType group, bool hidden)](#groupHiddenChanged)
- [void reloaded()](#reloaded)
- [void setupDone(const QModelIndex &index, bool success)](#setupDone)
- [void supportedSchemesChanged()](#supportedSchemesChanged)
- [void teardownDone(const QModelIndex &index, Solid::ErrorType error, const QVariant &errorData)](#teardownDone)

## Static Public Members

- [QUrl convertedUrl(const QUrl &url)](#convertedUrl)

## Detailed Description {#details}

This class is a list view model. Each entry represents a "place" where user can access files. Only relevant when used with [QListView](https://doc.qt.io/qt-6/qlistview.html) or [QTableView](https://doc.qt.io/qt-6/qtableview.html).

## Member Type Documentation {#member-type-documentation}

### enum KFilePlacesModel::AdditionalRoles {#AdditionalRoles-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KFilePlacesModel::UrlRole` | `0x069CD12B` | roleName is "url". See [url](kfileplacesmodel.md#url)() |
| `KFilePlacesModel::HiddenRole` | `0x0741CAAC` | roleName is "[isHidden](kfileplacesmodel.md#isHidden)". See [isHidden](kfileplacesmodel.md#isHidden)() |
| `KFilePlacesModel::SetupNeededRole` | `0x059A935D` | roleName is "isSetupNeeded". See [setupNeeded](kfileplacesmodel.md#setupNeeded)() |
| `KFilePlacesModel::FixedDeviceRole` | `0x332896C1` | Whether the place is a fixed device (neither hotpluggable nor removable). roleName is "isFixedDevice". |
| `KFilePlacesModel::CapacityBarRecommendedRole` | `0x1548C5C4` | Whether the place should have its free space displayed in a capacity bar. roleName is "isCapacityBarRecommended". |
| `KFilePlacesModel::GroupRole (since Qt 5.40)` | `0x0a5b64ee` | The name of the group, for example "Remote" or "Devices". roleName is "group". |
| `KFilePlacesModel::IconNameRole (since Qt 5.41)` | `0x00a45c00` | roleName is "iconName". See [icon](kfileplacesmodel.md#icon)(). |
| `KFilePlacesModel::GroupHiddenRole (since Qt 5.42)` | `0x21a4b936` | roleName is "[isGroupHidden](kfileplacesmodel.md#isGroupHidden)". |
| `KFilePlacesModel::TeardownAllowedRole (since Qt 5.91)` | `0x02533364` | roleName is "[isTeardownAllowed](kfileplacesmodel.md#isTeardownAllowed)". |
| `KFilePlacesModel::EjectAllowedRole (since Qt 5.94)` | `0x0A16AC5B` | roleName is "[isEjectAllowed](kfileplacesmodel.md#isEjectAllowed)". |
| `KFilePlacesModel::TeardownOverlayRecommendedRole (since Qt 5.95)` | `0x032EDCCE` | roleName is "[isTeardownOverlayRecommended](kfileplacesmodel.md#isTeardownOverlayRecommended)". |
| `KFilePlacesModel::DeviceAccessibilityRole (since Qt 5.99)` | `0x023FFD93` | roleName is "[deviceAccessibility](kfileplacesmodel.md#deviceAccessibility)". |

### enum KFilePlacesModel::DeviceAccessibility {#DeviceAccessibility-enum}

| Constant |   |
| --- | --- |
| `KFilePlacesModel::SetupNeeded` | `0` |
| `KFilePlacesModel::SetupInProgress` | `1` |
| `KFilePlacesModel::Accessible` | `2` |
| `KFilePlacesModel::TeardownInProgress` | `3` |

### enum KFilePlacesModel::GroupType {#GroupType-enum}

Describes the available group types used in this model.

| Constant | Value | Description |
| --- | --- | --- |
| `KFilePlacesModel::PlacesType` | `0` | "Places" section |
| `KFilePlacesModel::RemoteType` | `1` | "Remote" section |
| `KFilePlacesModel::RecentlySavedType` | `2` | "Recent" section |
| `KFilePlacesModel::SearchForType` | `3` | "Search for" section |
| `KFilePlacesModel::DevicesType` | `4` | "Devices" section |
| `KFilePlacesModel::RemovableDevicesType` | `5` | "Removable Devices" section |
| `KFilePlacesModel::UnknownType` | `6` | Unknown GroupType |
| `KFilePlacesModel::TagsType (since Qt 5.54)` | `7` | "Tags" section |

## Property Documentation {#property-documentation}

### supportedSchemes : QStringList {#supportedSchemes-prop}

**Access functions:**

- `QStringList` **[supportedSchemes](kfileplacesmodel.md#supportedSchemes)**() const
- `void` **[setSupportedSchemes](kfileplacesmodel.md#setSupportedSchemes)**(const `QStringList` &*schemes*)

**Notifier signal:**

- `void` **[supportedSchemesChanged](kfileplacesmodel.md#supportedSchemesChanged)**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KFilePlacesModel::KFilePlacesModel(QObject \**parent* = nullptr) {#KFilePlacesModel}

### \[invokable\] void KFilePlacesModel::addPlace(const QString &*text*, const QUrl &*url*, const QString &*iconName* = QString(), const QString &*appName* = QString()) {#addPlace}

Adds a new place to the model.

`text` The user-visible text for the place

`url` The URL of the place. It will be stored in its [QUrl::FullyEncoded](https://doc.qt.io/qt-6/qurl.html#ComponentFormattingOption-enum) string format.

`iconName` The icon of the place

`appName` If set as the value of [QCoreApplication::applicationName](https://doc.qt.io/qt-6/qcoreapplication.html#applicationName-prop)(), will make the place visible only in this application.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void KFilePlacesModel::addPlace(const QString &*text*, const QUrl &*url*, const QString &*iconName*, const QString &*appName*, const QModelIndex &*after*) {#addPlace-1}

Adds a new place to the model. `text` The user-visible text for the place

`url` The URL of the place. It will be stored in its [QUrl::FullyEncoded](https://doc.qt.io/qt-6/qurl.html#ComponentFormattingOption-enum) string format.

`iconName` The icon of the place

`appName` If set as the value of [QCoreApplication::applicationName](https://doc.qt.io/qt-6/qcoreapplication.html#applicationName-prop)(), will make the place visible only in this application.

`after` The index after which the new place will be added.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### KBookmark KFilePlacesModel::bookmarkForIndex(const QModelIndex &*index*) const {#bookmarkForIndex}

Returns The [KBookmark](../kbookmarks/kbookmark.md) instance of the place at index `index`. If the index is not valid, a default [KBookmark](../kbookmarks/kbookmark.md) instance is returned.

### KBookmark KFilePlacesModel::bookmarkForUrl(const QUrl &*searchUrl*) const {#bookmarkForUrl}

Returns The [KBookmark](../kbookmarks/kbookmark.md) instance of the place with url `searchUrl`. If the bookmark corresponding to searchUrl is not found, a default [KBookmark](../kbookmarks/kbookmark.md) instance is returned.

### QModelIndex KFilePlacesModel::closestItem(const QUrl &*url*) const {#closestItem}

Returns the closest item for the URL `url`. The closest item is defined as item which is equal to the URL or at least is a parent URL. If there are more than one possible parent URL candidates, the item which covers the bigger range of the URL is returned.

Example: the url is '/home/peter/Documents/Music'. Available items are: - /home/peter - /home/peter/Documents

The returned item will the one for '/home/peter/Documents'.

### \[static\] QUrl KFilePlacesModel::convertedUrl(const QUrl &*url*) {#convertedUrl}

Converts the URL, which contains "virtual" URLs for system-items like "timeline:/lastmonth" into a Query-URL "timeline:/2017-10" that will be handled by the corresponding KIO worker. Virtual URLs for bookmarks are used to be independent from internal format changes.

`an` url

Returns the converted URL, which can be handled by a KIO worker

### \[invokable\] KFilePlacesModel::DeviceAccessibility KFilePlacesModel::deviceAccessibility(const QModelIndex &*index*) const {#deviceAccessibility}

Returns Whether this device is currently accessible or being (un)mounted.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### Solid::Device KFilePlacesModel::deviceForIndex(const QModelIndex &*index*) const {#deviceForIndex}

Returns The solid device of the place at index `index`, if it is a device. Otherwise a default Solid::Device() instance is returned.

*See also* [isDevice](kfileplacesmodel.md#isDevice)()

### \[invokable\] void KFilePlacesModel::editPlace(const QModelIndex &*index*, const QString &*text*, const QUrl &*url*, const QString &*iconName* = QString(), const QString &*appName* = QString()) {#editPlace}

Edits the place with index `index`.

`text` The new user-visible text for the place

`url` The new URL of the place

`iconName` The new icon of the place

`appName` The new application-local filter for the place (see [addPlace](kfileplacesmodel.md#addPlace)()).

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] QAction \*KFilePlacesModel::ejectActionForIndex(const QModelIndex &*index*) const {#ejectActionForIndex}

Returns A [QAction](https://doc.qt.io/qt-6/qaction.html) with a proper translated label that can be used to trigger the [requestEject](kfileplacesmodel.md#requestEject)() method for the place at index `index`.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [requestEject](kfileplacesmodel.md#requestEject)()

### \[signal\] void KFilePlacesModel::errorMessage(const QString &*message*) {#errorMessage}

`message` An error message explaining what went wrong.

### \[signal\] void KFilePlacesModel::groupHiddenChanged(KFilePlacesModel::GroupType *group*, bool *hidden*) {#groupHiddenChanged}

Emitted whenever the visibility of the group `group` changes.

`hidden` The new visibility of the group.

*See also* [setGroupHidden](kfileplacesmodel.md#setGroupHidden)()

### \[invokable\] QModelIndexList KFilePlacesModel::groupIndexes(const KFilePlacesModel::GroupType *type*) const {#groupIndexes}

Returns The list of model indexes that have @ type as their group type.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [groupType](kfileplacesmodel.md#groupType)()

### \[invokable\] KFilePlacesModel::GroupType KFilePlacesModel::groupType(const QModelIndex &*index*) const {#groupType}

Returns The group type of the place at index `index`.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] int KFilePlacesModel::hiddenCount() const {#hiddenCount}

Returns the number of hidden places in the model.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [isHidden](kfileplacesmodel.md#isHidden)()

### \[invokable\] QIcon KFilePlacesModel::icon(const QModelIndex &*index*) const {#icon}

Returns The icon of the place at index `index`.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] bool KFilePlacesModel::isDevice(const QModelIndex &*index*) const {#isDevice}

Returns Whether the place at index `index` is a device handled by Solid.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [deviceForIndex](kfileplacesmodel.md#deviceForIndex)()

### \[invokable\] bool KFilePlacesModel::isEjectAllowed(const QModelIndex &*index*) const {#isEjectAllowed}

Returns Whether the place is a device that can be ejected, e.g. it is a CD, DVD, etc.

It does not indicate whether the eject can succeed.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] bool KFilePlacesModel::isGroupHidden(const KFilePlacesModel::GroupType *type*) const {#isGroupHidden}

Returns Whether the group type `type` is hidden.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] bool KFilePlacesModel::isGroupHidden(const QModelIndex &*index*) const {#isGroupHidden-1}

Returns Whether the group of the place at index `index` is hidden.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] bool KFilePlacesModel::isHidden(const QModelIndex &*index*) const {#isHidden}

Returns Whether the place at index `index` is hidden or is inside an hidden group.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] bool KFilePlacesModel::isTeardownAllowed(const QModelIndex &*index*) const {#isTeardownAllowed}

Returns Whether the place is a device that can be unmounted, e.g. it is mounted but does not point at system Root or the user's Home directory.

It does not indicate whether the teardown can succeed.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] bool KFilePlacesModel::isTeardownOverlayRecommended(const QModelIndex &*index*) const {#isTeardownOverlayRecommended}

Returns Whether showing an inline teardown button is recommended, e.g. when it is a removable drive.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] bool KFilePlacesModel::movePlace(int *itemRow*, int *row*) {#movePlace}

Move place at `itemRow` to a position before `row`

Returns whether the place has been moved.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable, since 6.20\] QAction \*KFilePlacesModel::openRecentOption(const QModelIndex &*index*) const {#openRecentOption}

Returns a [QAction](https://doc.qt.io/qt-6/qaction.html) to open the systemsettings recent documents kcm

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

This function was introduced in Qt 6.20.

### \[invokable\] QAction \*KFilePlacesModel::partitionActionForIndex(const QModelIndex &*index*) const {#partitionActionForIndex}

Returns A [QAction](https://doc.qt.io/qt-6/qaction.html) with a proper translated label that can be used to open a partitioning menu for the device. nullptr if not a device.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[since 6.23\] QString KFilePlacesModel::placeCollapsedUrl(const QUrl &*url*) const {#placeCollapsedUrl}

Returns a string representing the URL relative to the closest item, similar to [KUrlNavigator](kurlnavigator.md). This is more user-friendly than [KShell::tildeCollapse](../kcoreaddons/kshell.md#tildeCollapse).

Example: the url is '/home/peter/Documents/Important/KDE', if the user has a 'Documents' place, this will return: 'Documents/Important/KDE'. If they only have a 'Home' pace, this will return 'Home/Documents/Important/KDE'.

If no [closestItem](kfileplacesmodel.md#closestItem) could be determined, returns empty string.

This function was introduced in Qt 6.23.

### \[invokable\] void KFilePlacesModel::refresh() const {#refresh}

Reload bookmark information

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[signal\] void KFilePlacesModel::reloaded() {#reloaded}

Called once the model has been reloaded

### \[invokable\] void KFilePlacesModel::removePlace(const QModelIndex &*index*) const {#removePlace}

Deletes the place with index `index` from the model.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void KFilePlacesModel::requestEject(const QModelIndex &*index*) {#requestEject}

Ejects the place at index `index` by triggering the eject functionality of its Solid device.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [deviceForIndex](kfileplacesmodel.md#deviceForIndex)()

### \[invokable\] void KFilePlacesModel::requestSetup(const QModelIndex &*index*) {#requestSetup}

Mounts the place at index `index` by triggering the setup functionality of its Solid device.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [deviceForIndex](kfileplacesmodel.md#deviceForIndex)()

### \[invokable\] void KFilePlacesModel::requestTeardown(const QModelIndex &*index*) {#requestTeardown}

Unmounts the place at index `index` by triggering the teardown functionality of its Solid device.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [deviceForIndex](kfileplacesmodel.md#deviceForIndex)()

### \[invokable\] void KFilePlacesModel::setGroupHidden(const KFilePlacesModel::GroupType *type*, bool *hidden*) {#setGroupHidden}

Changes the visibility of the group with type `type`.

`hidden` Whether the group should be hidden or visible.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [isGroupHidden](kfileplacesmodel.md#isGroupHidden)()

### \[invokable\] void KFilePlacesModel::setPlaceHidden(const QModelIndex &*index*, bool *hidden*) {#setPlaceHidden}

Changes the visibility of the place with index `index`, but only if the place is not inside an hidden group.

`hidden` Whether the place should be hidden or visible.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [isGroupHidden](kfileplacesmodel.md#isGroupHidden)()

### void KFilePlacesModel::setSupportedSchemes(const QStringList &*schemes*) {#setSupportedSchemes}

Set the URL schemes that the file widget should allow navigating to.

If the returned list is empty, all schemes are supported. Examples for schemes are "file" or "ftp".

> **Note:** Setter function for property [supportedSchemes](kfileplacesmodel.md#supportedSchemes-prop).

*See also* [supportedSchemes](kfileplacesmodel.md#supportedSchemes)(), [QFileDialog::setSupportedSchemes](https://doc.qt.io/qt-6/qfiledialog.html#supportedSchemes-prop)

### \[signal\] void KFilePlacesModel::setupDone(const QModelIndex &*index*, bool *success*) {#setupDone}

Emitted after the Solid setup ends.

`success` Whether the Solid setup has been successful.

*See also* [requestSetup](kfileplacesmodel.md#requestSetup)()

### \[invokable\] bool KFilePlacesModel::setupNeeded(const QModelIndex &*index*) const {#setupNeeded}

Returns Whether the place at index `index` needs to be mounted before it can be used.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### QStringList KFilePlacesModel::supportedSchemes() const {#supportedSchemes}

Returns the URL schemes that the file widget should allow navigating to.

If the returned list is empty, all schemes are supported.

> **Note:** Getter function for property [supportedSchemes](kfileplacesmodel.md#supportedSchemes-prop).

*See also* [setSupportedSchemes](kfileplacesmodel.md#setSupportedSchemes)(), [QFileDialog::supportedSchemes](https://doc.qt.io/qt-6/qfiledialog.html#supportedSchemes-prop)

### \[signal\] void KFilePlacesModel::supportedSchemesChanged() {#supportedSchemesChanged}

Emitted whenever the list of supported schemes has been changed

> **Note:** Notifier signal for property [supportedSchemes](kfileplacesmodel.md#supportedSchemes-prop).

### \[invokable\] QAction \*KFilePlacesModel::teardownActionForIndex(const QModelIndex &*index*) const {#teardownActionForIndex}

Returns A [QAction](https://doc.qt.io/qt-6/qaction.html) with a proper translated label that can be used to trigger the [requestTeardown](kfileplacesmodel.md#requestTeardown)() method for the place at index `index`.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [requestTeardown](kfileplacesmodel.md#requestTeardown)()

### \[signal\] void KFilePlacesModel::teardownDone(const QModelIndex &*index*, Solid::ErrorType *error*, const QVariant &*errorData*) {#teardownDone}

Emitted after the teardown of a device ends.

> **Note:** In case of an error, the [errorMessage](kfileplacesmodel.md#errorMessage)() signal will also be emitted with a message describing the error.

`error` Type of error that occurred, if any.

`errorData` More information about the error, if any.

### \[invokable\] QString KFilePlacesModel::text(const QModelIndex &*index*) const {#text}

Returns The user-visible text of the place at index `index`.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] QUrl KFilePlacesModel::url(const QModelIndex &*index*) const {#url}

Returns The URL of the place at index `index`.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.
