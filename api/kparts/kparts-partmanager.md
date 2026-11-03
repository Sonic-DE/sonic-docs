---
title: "KParts::PartManager Class"
description: "The part manager is an object which knows about a collection of parts (even nested ones) and handles activation/deactivation."
---

# KParts::PartManager Class

The part manager is an object which knows about a collection of parts (even nested ones) and handles activation/deactivation. [More...](#details)

- **Header:** `#include <KParts/PartManager>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Parts)`  
  `target_link_libraries(mytarget PRIVATE KF6::Parts)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kparts-partmanager-members.md)

## Public Types

- [enum PartManager::Reason](#Reason-enum)
- [enum PartManager::SelectionPolicy](#SelectionPolicy-enum)

## Properties

- [allowNestedParts : bool](#allowNestedParts-prop)
- [ignoreScrollBars : bool](#ignoreScrollBars-prop)
- [selectionPolicy : SelectionPolicy](#selectionPolicy-prop)

## Public Functions

- [PartManager(QWidget \*parent)](#PartManager)
- [PartManager(QWidget \*topLevel, QObject \*parent)](#PartManager-1)
- [short activationButtonMask() const](#activationButtonMask)
- [KParts::Part \*activePart() const](#activePart)
- [QWidget \*activeWidget() const](#activeWidget)
- [void addManagedTopLevelWidget(const QWidget \*topLevel)](#addManagedTopLevelWidget)
- [void addPart(KParts::Part \*part, bool setActive = true)](#addPart)
- [bool allowNestedParts() const](#allowNestedParts)
- [bool ignoreScrollBars() const](#ignoreScrollBars)
- [const QList\<KParts::Part \*\> parts() const](#parts)
- [int reason() const](#reason)
- [void removeManagedTopLevelWidget(const QWidget \*topLevel)](#removeManagedTopLevelWidget)
- [void removePart(KParts::Part \*part)](#removePart)
- [void replacePart(KParts::Part \*oldPart, KParts::Part \*newPart, bool setActive = true)](#replacePart)
- [KParts::PartManager::SelectionPolicy selectionPolicy() const](#selectionPolicy)
- [void setActivationButtonMask(short buttonMask)](#setActivationButtonMask)
- [void setActivePart(KParts::Part \*part, QWidget \*widget = nullptr)](#setActivePart)
- [void setAllowNestedParts(bool allow)](#setAllowNestedParts)
- [void setIgnoreScrollBars(bool ignore)](#setIgnoreScrollBars)
- [void setSelectionPolicy(KParts::PartManager::SelectionPolicy policy)](#setSelectionPolicy)

## Public Slots

- [void slotObjectDestroyed()](#slotObjectDestroyed)

## Signals

- [void activePartChanged(KParts::Part \*newPart)](#activePartChanged)
- [void partAdded(KParts::Part \*part)](#partAdded)
- [void partRemoved(KParts::Part \*part)](#partRemoved)

## Protected Functions

- [void setIgnoreExplictFocusRequests(bool)](#setIgnoreExplictFocusRequests)

## Detailed Description {#details}

Applications that want to embed parts without merging GUIs only use a [KParts::PartManager](kparts-partmanager.md). Those who want to merge GUIs use a [KParts::MainWindow](kparts-mainwindow.md) for example, in addition to a part manager.

Parts know about the part manager to add nested parts to it. See also KParts::Part::manager() and KParts::Part::setManager().

## Member Type Documentation {#member-type-documentation}

### enum PartManager::Reason {#Reason-enum}

This extends QFocusEvent::Reason with the non-focus-event reasons for partmanager to activate a part. To test for "any focusin reason", use \< ReasonLeftClick NoReason usually means: explicit activation with [setActivePart](kparts-partmanager.md#setActivePart).

| Constant |   |
| --- | --- |
| `KParts::PartManager::ReasonLeftClick` | `100` |
| `KParts::PartManager::ReasonMidClick` | `101` |
| `KParts::PartManager::ReasonRightClick` | `102` |
| `KParts::PartManager::NoReason` | `103` |

### enum PartManager::SelectionPolicy {#SelectionPolicy-enum}

Selection policy. The default policy of a [PartManager](kparts-partmanager.md) is Direct.

| Constant |   |
| --- | --- |
| `KParts::PartManager::Direct` | `0` |
| `KParts::PartManager::TriState` | `1` |

## Property Documentation {#property-documentation}

### allowNestedParts : bool {#allowNestedParts-prop}

**Access functions:**

- `bool` **[allowNestedParts](kparts-partmanager.md#allowNestedParts)**() const
- `void` **[setAllowNestedParts](kparts-partmanager.md#setAllowNestedParts)**(`bool` *allow*)

### ignoreScrollBars : bool {#ignoreScrollBars-prop}

**Access functions:**

- `bool` **[ignoreScrollBars](kparts-partmanager.md#ignoreScrollBars)**() const
- `void` **[setIgnoreScrollBars](kparts-partmanager.md#setIgnoreScrollBars)**(`bool` *ignore*)

### selectionPolicy : SelectionPolicy {#selectionPolicy-prop}

**Access functions:**

- `KParts::PartManager::SelectionPolicy` **[selectionPolicy](kparts-partmanager.md#selectionPolicy)**() const
- `void` **[setSelectionPolicy](kparts-partmanager.md#setSelectionPolicy)**(`KParts::PartManager::SelectionPolicy` *policy*)

## Member Function Documentation {#member-function-documentation}

### PartManager::PartManager(QWidget \**parent*) {#PartManager}

Constructs a part manager.

`parent` The toplevel widget (window / dialog) the partmanager should monitor for activation/selection events

### PartManager::PartManager(QWidget \**topLevel*, QObject \**parent*) {#PartManager-1}

Constructs a part manager.

`topLevel` The toplevel widget (window / dialog ) the partmanager should monitor for activation/selection events `parent` The parent [QObject](https://doc.qt.io/qt-6/qobject.html).

### short PartManager::activationButtonMask() const {#activationButtonMask}

*See also* [setActivationButtonMask](kparts-partmanager.md#setActivationButtonMask)

### \[virtual\] KParts::Part \*PartManager::activePart() const {#activePart}

Returns the active part.

*See also* [setActivePart](kparts-partmanager.md#setActivePart)()

### \[signal\] void PartManager::activePartChanged(KParts::Part \**newPart*) {#activePartChanged}

Emitted when the active part has changed.

*See also* [setActivePart](kparts-partmanager.md#setActivePart)()

### \[virtual\] QWidget \*PartManager::activeWidget() const {#activeWidget}

Returns the active widget of the current active part (see [activePart](kparts-partmanager.md#activePart) ).

### void PartManager::addManagedTopLevelWidget(const QWidget \**topLevel*) {#addManagedTopLevelWidget}

Adds the `topLevel` widget to the list of managed toplevel widgets.

Usually a [PartManager](kparts-partmanager.md) only listens for events (for activation/selection) for one toplevel widget (and its children) , the one specified in the constructor. Sometimes however (like for example when using the KDE dockwidget library) , it is necessary to extend this.

### \[virtual\] void PartManager::addPart(KParts::Part \**part*, bool *setActive* = true) {#addPart}

Adds a part to the manager.

Sets it to the active part automatically if `setActive` is true (default).

### bool PartManager::allowNestedParts() const {#allowNestedParts}

> **Note:** Getter function for property [allowNestedParts](kparts-partmanager.md#allowNestedParts-prop).

*See also* [setAllowNestedParts](kparts-partmanager.md#setAllowNestedParts)

### bool PartManager::ignoreScrollBars() const {#ignoreScrollBars}

> **Note:** Getter function for property [ignoreScrollBars](kparts-partmanager.md#ignoreScrollBars-prop).

*See also* [setIgnoreScrollBars](kparts-partmanager.md#setIgnoreScrollBars)

### \[signal\] void PartManager::partAdded(KParts::Part \**part*) {#partAdded}

Emitted when a new part has been added.

*See also* [addPart](kparts-partmanager.md#addPart)()

### \[signal\] void PartManager::partRemoved(KParts::Part \**part*) {#partRemoved}

Emitted when a part has been removed.

*See also* [removePart](kparts-partmanager.md#removePart)()

### const QList\<KParts::Part \*\> PartManager::parts() const {#parts}

Returns the list of parts being managed by the partmanager.

### int PartManager::reason() const {#reason}

Returns the reason for the last [activePartChanged](kparts-partmanager.md#activePartChanged) signal emitted.

*See also* [Reason](kparts-partmanager.md#Reason-enum)

### void PartManager::removeManagedTopLevelWidget(const QWidget \**topLevel*) {#removeManagedTopLevelWidget}

Removes the `topLevel` widget from the list of managed toplevel widgets.

*See also* [addManagedTopLevelWidget](kparts-partmanager.md#addManagedTopLevelWidget)

### \[virtual\] void PartManager::removePart(KParts::Part \**part*) {#removePart}

Removes a part from the manager (this does not delete the object) .

Sets the active part to 0 if `part` is the [activePart](kparts-partmanager.md#activePart)() .

### \[virtual\] void PartManager::replacePart(KParts::Part \**oldPart*, KParts::Part \**newPart*, bool *setActive* = true) {#replacePart}

Replaces `oldPart` with `newPart`, and sets `newPart` as active if `setActive` is true. This is an optimised version of [removePart](kparts-partmanager.md#removePart) + [addPart](kparts-partmanager.md#addPart)

### KParts::PartManager::SelectionPolicy PartManager::selectionPolicy() const {#selectionPolicy}

Returns the current selection policy.

> **Note:** Getter function for property [selectionPolicy](kparts-partmanager.md#selectionPolicy-prop).

*See also* [setSelectionPolicy](kparts-partmanager.md#setSelectionPolicy)()

### void PartManager::setActivationButtonMask(short *buttonMask*) {#setActivationButtonMask}

Specifies which mouse buttons the partmanager should react upon.

By default it reacts on all mouse buttons (LMB/MMB/RMB).

`buttonMask` a combination of Qt::ButtonState values e.g. [Qt::LeftButton](https://doc.qt.io/qt-6/qt.html#MouseButton-enum) \| [Qt::MiddleButton](https://doc.qt.io/qt-6/qt.html#MouseButton-enum)

*See also* [activationButtonMask](kparts-partmanager.md#activationButtonMask)()

### \[virtual\] void PartManager::setActivePart(KParts::Part \**part*, QWidget \**widget* = nullptr) {#setActivePart}

Sets the active part.

The active part receives activation events.

`widget` can be used to specify which widget was responsible for the activation. This is important if you have multiple views for a document/part , like in KOffice .

*See also* [activePart](kparts-partmanager.md#activePart)()

### void PartManager::setAllowNestedParts(bool *allow*) {#setAllowNestedParts}

Specifies whether the partmanager should handle/allow nested parts or not.

This is a property the shell has to set/specify. Per default we assume that the shell cannot handle nested parts. However in case of a KOffice shell for example we allow nested parts. A Part is nested (a child part) if its parent object inherits [KParts::Part](kparts-part.md). If a child part is activated and nested parts are not allowed/handled, then the top parent part in the tree is activated.

> **Note:** Setter function for property [allowNestedParts](kparts-partmanager.md#allowNestedParts-prop).

*See also* [allowNestedParts](kparts-partmanager.md#allowNestedParts)()

### \[protected\] void PartManager::setIgnoreExplictFocusRequests(*bool*) {#setIgnoreExplictFocusRequests}

Sets whether the [PartManager](kparts-partmanager.md) ignores explicit set focus requests from the part.

By default this option is set to false. Set it to true to prevent the part from sending explicit set focus requests to the client application.

### void PartManager::setIgnoreScrollBars(bool *ignore*) {#setIgnoreScrollBars}

Specifies whether the partmanager should ignore mouse click events for scrollbars or not. If the partmanager ignores them, then clicking on the scrollbars of a non-active/non-selected part will not change the selection or activation state.

The default value is false (read: scrollbars are NOT ignored).

> **Note:** Setter function for property [ignoreScrollBars](kparts-partmanager.md#ignoreScrollBars-prop).

*See also* [ignoreScrollBars](kparts-partmanager.md#ignoreScrollBars)()

### void PartManager::setSelectionPolicy(KParts::PartManager::SelectionPolicy *policy*) {#setSelectionPolicy}

Sets the selection policy of the partmanager.

> **Note:** Setter function for property [selectionPolicy](kparts-partmanager.md#selectionPolicy-prop).

*See also* [selectionPolicy](kparts-partmanager.md#selectionPolicy)()

### \[protected slot\] void PartManager::slotObjectDestroyed() {#slotObjectDestroyed}

Removes a part when it is destroyed.
