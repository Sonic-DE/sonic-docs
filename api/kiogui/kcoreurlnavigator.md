---
title: "KCoreUrlNavigator Class"
description: "Object that helps with keeping track of URLs in file-manager like interfaces."
---

# KCoreUrlNavigator Class

Object that helps with keeping track of URLs in file-manager like interfaces. [More...](#details)

- **Header:** `#include <KCoreUrlNavigator>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KIOGui)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kcoreurlnavigator-members.md)

## Properties

- [currentLocationUrl : QUrl](#currentLocationUrl-prop)
- [\[read-only\] historyIndex : int](#historyIndex-prop)
- [\[read-only\] historySize : int](#historySize-prop)

## Public Functions

- [bool goBack()](#goBack)
- [bool goForward()](#goForward)
- [bool goUp()](#goUp)
- [QVariant locationState(int historyIndex = -1) const](#locationState)
- [QUrl locationUrl(int historyIndex = -1) const](#locationUrl)
- [void saveLocationState(const QVariant &state)](#saveLocationState)

## Signals

- [void currentUrlAboutToChange(const QUrl &newUrl)](#currentUrlAboutToChange)
- [void historyChanged()](#historyChanged)
- [void urlSelectionRequested(const QUrl &url)](#urlSelectionRequested)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### currentLocationUrl : QUrl {#currentLocationUrl-prop}

**Access functions:**

- `QUrl` **currentLocationUrl**() const
- `void` **setCurrentLocationUrl**(const `QUrl` &*url*)

**Notifier signal:**

- `void` **currentLocationUrlChanged**()

### \[read-only\] historyIndex : int {#historyIndex-prop}

The history index of the current location, where 0 \<= history index \< [KCoreUrlNavigator::historySize](kcoreurlnavigator.md#historySize-prop)(). 0 is the most recent history entry.

**Access functions:**

- `int` **historyIndex**() const

**Notifier signal:**

- `void` **historyIndexChanged**()

### \[read-only\] historySize : int {#historySize-prop}

The amount of locations in the history. The data for each location can be retrieved by [KCoreUrlNavigator::locationUrl](kcoreurlnavigator.md#locationUrl)() and [KCoreUrlNavigator::locationState](kcoreurlnavigator.md#locationState)().

**Access functions:**

- `int` **historySize**() const

**Notifier signal:**

- `void` **historySizeChanged**()

## Member Function Documentation {#member-function-documentation}

### \[signal\] void KCoreUrlNavigator::currentUrlAboutToChange(const QUrl &*newUrl*) {#currentUrlAboutToChange}

Is emitted, before the location URL is going to be changed to `newUrl`.

The signal KCoreUrlNavigator::urlChanged() will be emitted after the change has been done. Connecting to this signal is useful to save the state of a view with [KCoreUrlNavigator::saveLocationState](kcoreurlnavigator.md#saveLocationState)().

### \[invokable\] bool KCoreUrlNavigator::goBack() {#goBack}

Goes back one step in the URL history. The signals KCoreUrlNavigator::urlAboutToBeChanged(), KCoreUrlNavigator::urlChanged() and [KCoreUrlNavigator::historyChanged](kcoreurlnavigator.md#historyChanged)() are emitted if true is returned. False is returned if the beginning of the history has already been reached and hence going back was not possible. The history index (see [KCoreUrlNavigator::historyIndex](kcoreurlnavigator.md#historyIndex-prop)()) is increased by one if the operation was successful.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] bool KCoreUrlNavigator::goForward() {#goForward}

Goes forward one step in the URL history. The signals KCoreUrlNavigator::urlAboutToBeChanged(), KCoreUrlNavigator::urlChanged() and [KCoreUrlNavigator::historyChanged](kcoreurlnavigator.md#historyChanged)() are emitted if true is returned. False is returned if the end of the history has already been reached and hence going forward was not possible. The history index (see [KCoreUrlNavigator::historyIndex](kcoreurlnavigator.md#historyIndex-prop)()) is decreased by one if the operation was successful.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] bool KCoreUrlNavigator::goUp() {#goUp}

Goes up one step of the URL path and remembers the old path in the history. The signals KCoreUrlNavigator::urlAboutToBeChanged(), KCoreUrlNavigator::urlChanged() and [KCoreUrlNavigator::historyChanged](kcoreurlnavigator.md#historyChanged)() are emitted if true is returned. False is returned if going up was not possible as the root has been reached.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[signal\] void KCoreUrlNavigator::historyChanged() {#historyChanged}

Is emitted, if the history has been changed. Usually the history is changed if a new URL has been selected.

### \[invokable\] QVariant KCoreUrlNavigator::locationState(int *historyIndex* = -1) const {#locationState}

Returns Location state given by `historyIndex`. If `historyIndex` is smaller than 0, the state of the current location is returned.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [KCoreUrlNavigator::saveLocationState](kcoreurlnavigator.md#saveLocationState)()

### \[invokable\] QUrl KCoreUrlNavigator::locationUrl(int *historyIndex* = -1) const {#locationUrl}

Returns URL of the location given by the `historyIndex`. If `historyIndex` is smaller than 0, the URL of the current location is returned.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void KCoreUrlNavigator::saveLocationState(const QVariant &*state*) {#saveLocationState}

Saves the location state described by `state` for the current location. It is recommended that at least the scroll position of a view is remembered and restored when traversing through the history. Saving the location state should be done when the signal KCoreUrlNavigator::urlAboutToBeChanged() has been emitted. Restoring the location state (see [KCoreUrlNavigator::locationState](kcoreurlnavigator.md#locationState)()) should be done when the signal KCoreUrlNavigator::urlChanged() has been emitted.

Example:

```cpp
urlNavigator->saveLocationState(QPoint(x, y));
```

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[signal\] void KCoreUrlNavigator::urlSelectionRequested(const QUrl &*url*) {#urlSelectionRequested}

When the URL is changed and the new URL (e.g. /home/user1/) is a parent of the previous URL (e.g. /home/user1/data/stuff), then this signal is emitted and `url` is set to the child directory of the new URL which is an ancestor of the old URL (in the example paths this would be /home/user1/data/). This signal allows file managers to pre-select the directory that the user is navigating up from.
