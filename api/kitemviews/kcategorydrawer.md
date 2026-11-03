---
title: "KCategoryDrawer Class"
description: "The category drawing is performed by this class."
---

# KCategoryDrawer Class

The category drawing is performed by this class. [More...](#details)

- **Header:** `#include <KCategoryDrawer>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ItemViews)`  
  `target_link_libraries(mytarget PRIVATE KF6::ItemViews)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kcategorydrawer-members.md)

## Public Functions

- [KCategoryDrawer(KCategorizedView \*view)](#KCategoryDrawer)
- [int categoryHeight(const QModelIndex &index, const QStyleOption &option) const](#categoryHeight)
- [void drawCategory(const QModelIndex &index, int sortRole, const QStyleOption &option, QPainter \*painter) const](#drawCategory)
- [int leftMargin() const](#leftMargin)
- [int rightMargin() const](#rightMargin)
- [KCategorizedView \*view() const](#view)

## Signals

- [void actionRequested(int action, const QModelIndex &index)](#actionRequested)
- [void collapseOrExpandClicked(const QModelIndex &index)](#collapseOrExpandClicked)

## Protected Functions

- [void mouseButtonDoubleClicked(const QModelIndex &index, const QRect &blockRect, QMouseEvent \*event)](#mouseButtonDoubleClicked)
- [void mouseButtonPressed(const QModelIndex &index, const QRect &blockRect, QMouseEvent \*event)](#mouseButtonPressed)
- [void mouseButtonReleased(const QModelIndex &index, const QRect &blockRect, QMouseEvent \*event)](#mouseButtonReleased)
- [void mouseLeft(const QModelIndex &index, const QRect &blockRect)](#mouseLeft)
- [void mouseMoved(const QModelIndex &index, const QRect &blockRect, QMouseEvent \*event)](#mouseMoved)

## Detailed Description {#details}

It also gives information about the category height and margins.

## Member Function Documentation {#member-function-documentation}

### KCategoryDrawer::KCategoryDrawer(KCategorizedView \**view*) {#KCategoryDrawer}

Construct a category drawer for a given view

### \[signal\] void KCategoryDrawer::actionRequested(int *action*, const QModelIndex &*index*) {#actionRequested}

Emit this signal on your subclass implementation to notify that something happened. Usually this will be triggered when you have received an event, and its position matched some "hot spot".

You give this action the integer you want, and having connected this signal to your code, the connected slot can perform the needed changes (view, model, selection model, delegate...)

### \[virtual\] int KCategoryDrawer::categoryHeight(const QModelIndex &*index*, const QStyleOption &*option*) const {#categoryHeight}

Returns the category height for the category represented by index `index` with style options `option`.

### \[signal\] void KCategoryDrawer::collapseOrExpandClicked(const QModelIndex &*index*) {#collapseOrExpandClicked}

This signal becomes emitted when collapse or expand has been clicked.

### \[virtual\] void KCategoryDrawer::drawCategory(const QModelIndex &*index*, int *sortRole*, const QStyleOption &*option*, QPainter \**painter*) const {#drawCategory}

This method purpose is to draw a category represented by the given `index` with the given `sortRole` sorting role

> **Note:** This method will be called one time per category, always with the first element in that category

### \[virtual\] int KCategoryDrawer::leftMargin() const {#leftMargin}

> **Note:** 0 by default

### \[virtual protected\] void KCategoryDrawer::mouseButtonDoubleClicked(const QModelIndex &*index*, const QRect &*blockRect*, QMouseEvent \**event*) {#mouseButtonDoubleClicked}

Method called when the mouse button has been double clicked.

`index` The representative index of the block of items.

`blockRect` The rect occupied by the block of items.

`event` The mouse event.

> **Warning:** You explicitly have to determine whether the event has been accepted or not. You have to call event-\>accept() or event-\>ignore() at all possible case branches in your code.

### \[virtual protected\] void KCategoryDrawer::mouseButtonPressed(const QModelIndex &*index*, const QRect &*blockRect*, QMouseEvent \**event*) {#mouseButtonPressed}

Method called when the mouse button has been pressed.

`index` The representative index of the block of items.

`blockRect` The rect occupied by the block of items.

`event` The mouse event.

> **Warning:** You explicitly have to determine whether the event has been accepted or not. You have to call event-\>accept() or event-\>ignore() at all possible case branches in your code.

### \[virtual protected\] void KCategoryDrawer::mouseButtonReleased(const QModelIndex &*index*, const QRect &*blockRect*, QMouseEvent \**event*) {#mouseButtonReleased}

Method called when the mouse button has been released.

`index` The representative index of the block of items.

`blockRect` The rect occupied by the block of items.

`event` The mouse event.

> **Warning:** You explicitly have to determine whether the event has been accepted or not. You have to call event-\>accept() or event-\>ignore() at all possible case branches in your code.

### \[virtual protected\] void KCategoryDrawer::mouseLeft(const QModelIndex &*index*, const QRect &*blockRect*) {#mouseLeft}

Method called when the mouse button has left this block.

`index` The representative index of the block of items.

`blockRect` The rect occupied by the block of items.

### \[virtual protected\] void KCategoryDrawer::mouseMoved(const QModelIndex &*index*, const QRect &*blockRect*, QMouseEvent \**event*) {#mouseMoved}

Method called when the mouse has been moved.

`index` The representative index of the block of items.

`blockRect` The rect occupied by the block of items.

`event` The mouse event.

### \[virtual\] int KCategoryDrawer::rightMargin() const {#rightMargin}

> **Note:** 0 by default

### KCategorizedView \*KCategoryDrawer::view() const {#view}

Returns the view this category drawer is associated with.
