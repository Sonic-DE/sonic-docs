---
title: "KFilePlacesView Class"
description: "This class allows to display a KFilePlacesModel."
---

# KFilePlacesView Class

This class allows to display a [KFilePlacesModel](kfileplacesmodel.md). [More...](#details)

- **Header:** `#include <KFilePlacesView>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOFileWidgets)`
- **Inherits:** [QListView](https://doc.qt.io/qt-6/qlistview.html)

[List of all members, including inherited members](kfileplacesview-members.md)

## Public Functions

- [KFilePlacesView(QWidget \*parent = nullptr)](#KFilePlacesView)
- [bool allPlacesShown() const](#allPlacesShown)
- [int dragAutoActivationDelay() const](#dragAutoActivationDelay)
- [bool isAutoResizeItemsEnabled() const](#isAutoResizeItemsEnabled)
- [bool isDropOnPlaceEnabled() const](#isDropOnPlaceEnabled)
- [void setAutoResizeItemsEnabled(bool enabled)](#setAutoResizeItemsEnabled)
- [void setDragAutoActivationDelay(int delay)](#setDragAutoActivationDelay)
- [void setDropOnPlaceEnabled(bool enabled)](#setDropOnPlaceEnabled)
- [void setTeardownFunction(KFilePlacesView::TeardownFunction teardownFunc)](#setTeardownFunction)

## Public Slots

- [void setShowAll(bool showAll)](#setShowAll)
- [void setUrl(const QUrl &url)](#setUrl)

## Signals

- [void activeTabRequested(const QUrl &url)](#activeTabRequested)
- [void allPlacesShownChanged(bool allPlacesShown)](#allPlacesShownChanged)
- [void contextMenuAboutToShow(const QModelIndex &index, QMenu \*menu)](#contextMenuAboutToShow)
- [void newWindowRequested(const QUrl &url)](#newWindowRequested)
- [void placeActivated(const QUrl &url)](#placeActivated)
- [void tabRequested(const QUrl &url)](#tabRequested)
- [void urlsDropped(const QUrl &dest, QDropEvent \*event, QWidget \*parent)](#urlsDropped)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KFilePlacesView::KFilePlacesView(QWidget \**parent* = nullptr) {#KFilePlacesView}

### \[signal\] void KFilePlacesView::activeTabRequested(const QUrl &*url*) {#activeTabRequested}

\* Emitted when the URL `url` should be opened in a new active tab because \* the user clicked on a place with the middle mouse button with \* the Shift modifier pressed or left-clicked with both the Ctrl and Shift \* modifiers pressed.

\* If a storage device needs to be mounted first, this signal is emitted once \* mounting has completed successfully. \*

### bool KFilePlacesView::allPlacesShown() const {#allPlacesShown}

Returns whether hidden places, if any, are currently shown.

### \[signal\] void KFilePlacesView::allPlacesShownChanged(bool *allPlacesShown*) {#allPlacesShownChanged}

Emitted when [allPlacesShown](kfileplacesview.md#allPlacesShown) changes

### \[signal\] void KFilePlacesView::contextMenuAboutToShow(const QModelIndex &*index*, QMenu \**menu*) {#contextMenuAboutToShow}

Emitted just before the context menu opens. This can be used to add additional application actions to the menu.

`index` The model index of the place whose menu is about to open.

`menu` The menu that will be opened.

### int KFilePlacesView::dragAutoActivationDelay() const {#dragAutoActivationDelay}

*See also* [setDragAutoActivationDelay](kfileplacesview.md#setDragAutoActivationDelay)()

### bool KFilePlacesView::isAutoResizeItemsEnabled() const {#isAutoResizeItemsEnabled}

### bool KFilePlacesView::isDropOnPlaceEnabled() const {#isDropOnPlaceEnabled}

### \[signal\] void KFilePlacesView::newWindowRequested(const QUrl &*url*) {#newWindowRequested}

Emitted when the URL `url` should be opened in a new window because the user left-clicked on a place with Shift modifier pressed or selected "Open in New Window" from the context menu.

If a storage device needs to be mounted first, this signal is emitted once mounting has completed successfully.

### \[signal\] void KFilePlacesView::placeActivated(const QUrl &*url*) {#placeActivated}

Emitted when an item in the places view is clicked on with left mouse button with no modifier keys pressed.

If a storage device needs to be mounted first, this signal is emitted once mounting has completed successfully.

`url` The URL of the place

### void KFilePlacesView::setAutoResizeItemsEnabled(bool *enabled*) {#setAutoResizeItemsEnabled}

If `enabled` is true (the default), items will automatically resize themselves to fill the view.

*See also* [isAutoResizeItemsEnabled](kfileplacesview.md#isAutoResizeItemsEnabled)()

### void KFilePlacesView::setDragAutoActivationDelay(int *delay*) {#setDragAutoActivationDelay}

If `delay` (in ms) is greater than zero, the place will automatically be activated if an item is dragged over and held on top of a place for at least that duraton.

`delay` Delay in ms, default is zero.

*See also* [dragAutoActivationDelay](kfileplacesview.md#dragAutoActivationDelay)()

### void KFilePlacesView::setDropOnPlaceEnabled(bool *enabled*) {#setDropOnPlaceEnabled}

If `enabled` is true, it is allowed dropping items above a place for e. g. copy or move operations. The application has to take care itself to perform the operation (see [KFilePlacesView::urlsDropped](kfileplacesview.md#urlsDropped)()). If `enabled` is false, it is only possible adding items as additional place. Per default dropping on a place is disabled.

*See also* [isDropOnPlaceEnabled](kfileplacesview.md#isDropOnPlaceEnabled)()

### \[slot\] void KFilePlacesView::setShowAll(bool *showAll*) {#setShowAll}

### void KFilePlacesView::setTeardownFunction(KFilePlacesView::TeardownFunction *teardownFunc*) {#setTeardownFunction}

Sets a custom function that will be called when teardown of a device (e.g. unmounting a drive) is requested.

### \[slot\] void KFilePlacesView::setUrl(const QUrl &*url*) {#setUrl}

### \[signal\] void KFilePlacesView::tabRequested(const QUrl &*url*) {#tabRequested}

Emitted when the URL `url` should be opened in a new inactive tab because the user clicked on a place with the middle mouse button or left-clicked with the Ctrl modifier pressed or selected "Open in New Tab" from the context menu.

If a storage device needs to be mounted first, this signal is emitted once mounting has completed successfully.

### \[signal\] void KFilePlacesView::urlsDropped(const QUrl &*dest*, QDropEvent \**event*, QWidget \**parent*) {#urlsDropped}

Is emitted if items are dropped on the place `dest`.

The application has to take care itself about performing the corresponding action like copying or moving.
