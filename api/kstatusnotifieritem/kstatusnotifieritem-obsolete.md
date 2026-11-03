---
title: "Obsolete Members for KStatusNotifierItem"
description: "Deprecated members of KStatusNotifierItem."
parent: "kstatusnotifieritem/kstatusnotifieritem"
---

# Obsolete Members for KStatusNotifierItem

**The following members of class [KStatusNotifierItem](kstatusnotifieritem.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [QAction \*action(const QString &name) const](#action) (deprecated in 6.6)
- [QList\<QAction \*\> actionCollection() const](#actionCollection) (deprecated in 6.6)
- [void addAction(const QString &name, QAction \*action)](#addAction) (deprecated in 6.6)
- [void removeAction(const QString &name)](#removeAction) (deprecated in 6.6)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[deprecated in 6.6\] QAction \*KStatusNotifierItem::action(const QString &*name*) const {#action}

This function is deprecated since 6.6. We strongly advise against using it in new code.

Retrieves an action from the action collection by the action name.

`name` the name of the action to retrieve

Read actions using [contextMenu](kstatusnotifieritem.md#contextMenu)(). For controlling the behavior of the Quit action use [quitRequested](kstatusnotifieritem.md#quitRequested)() and [abortQuit](kstatusnotifieritem.md#abortQuit)()

### \[deprecated in 6.6\] QList\<QAction \*\> KStatusNotifierItem::actionCollection() const {#actionCollection}

This function is deprecated since 6.6. We strongly advise against using it in new code.

All the actions present in the menu.

Read actions using [contextMenu](kstatusnotifieritem.md#contextMenu)() instead.

### \[deprecated in 6.6\] void KStatusNotifierItem::addAction(const QString &*name*, QAction \**action*) {#addAction}

This function is deprecated since 6.6. We strongly advise against using it in new code.

Adds an action to the [actionCollection](kstatusnotifieritem-obsolete.md#actionCollection)().

`name` the name of the action

`action` the action we want to add

Add actions using [contextMenu](kstatusnotifieritem.md#contextMenu)() instead.

### \[deprecated in 6.6\] void KStatusNotifierItem::removeAction(const QString &*name*) {#removeAction}

This function is deprecated since 6.6. We strongly advise against using it in new code.

Removes an action from the collection.

`name` the name of the action

Remove actions using [contextMenu](kstatusnotifieritem.md#contextMenu)() instead.
