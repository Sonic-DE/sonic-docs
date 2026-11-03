---
title: "KToolBarEditor Class"
description: "The toolbar editing of KEditToolBar, without widgets."
---

# KToolBarEditor Class

The toolbar editing of [KEditToolBar](kedittoolbar.md), without widgets. [More...](#details)

- **Header:** `#include <KToolBarEditor>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS XmlGui)`  
  `target_link_libraries(mytarget PRIVATE KF6::XmlGui)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](ktoolbareditor-members.md)

## Public Types

- [enum KToolBarEditor::Role](#Role-enum)

## Properties

- [\[read-only\] availableActions : QAbstractItemModel\* const](#availableActions-prop)
- [\[read-only\] currentActions : QAbstractItemModel\* const](#currentActions-prop)
- [currentToolBar : int](#currentToolBar-prop)
- [\[read-only\] toolBars : QStringList](#toolBars-prop)

## Public Functions

- [int insertAction(int availableRow, int currentRow, bool prepend = false)](#insertAction)
- [bool load(KXMLGUIFactory \*factory, const QString &defaultToolBar = QString())](#load)
- [bool load(KActionCollection \*collection, const QString &resourceFile, bool global = true, const QString &defaultToolBar = QString())](#load-1)
- [int moveAction(int currentRow, int afterRow)](#moveAction)
- [int moveDown(int currentRow)](#moveDown)
- [int moveUp(int currentRow)](#moveUp)
- [void rebuildClients()](#rebuildClients)
- [void removeAction(int currentRow)](#removeAction)
- [void restoreDefaults()](#restoreDefaults)
- [void save()](#save)
- [void setActionIcon(int currentRow, const QString &iconName)](#setActionIcon)
- [void setActionIconText(int currentRow, const QString &text, bool textAlongsideIconHidden)](#setActionIconText)
- [void setCurrentToolBar(int index)](#setCurrentToolBar)

## Signals

- [void changed()](#changed)

## Detailed Description {#details}

Loads the toolbars of a [KXMLGUIFactory](kxmlguifactory.md)'s clients (or of one resource file), lists the current toolbar's actions and the actions that can be added to it as item models, and changes the clients' XML as [KEditToolBar](kedittoolbar.md) does: insert, remove and move actions, change an action's icon and icon text, save, and restore the defaults. [KEditToolBar](kedittoolbar.md)'s widget and QML toolbar editors both use it.

Rows are those of [currentActions](ktoolbareditor.md#currentActions-prop)() and [availableActions](ktoolbareditor.md#availableActions-prop)(); -1 means none.

## Member Type Documentation {#member-type-documentation}

### enum KToolBarEditor::Role {#Role-enum}

The item models' roles, besides [Qt::DisplayRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum) (the text, role name "text") and [Qt::DecorationRole](https://doc.qt.io/qt-6/qt.html#ItemDataRole-enum) (the action's [QIcon](https://doc.qt.io/qt-6/qicon.html), role name "icon").

| Constant | Value | Description |
| --- | --- | --- |
| `KToolBarEditor::NameRole` | `Qt::UserRole + 1` | The element's name. |
| `KToolBarEditor::TagRole` | `258` | The element's tag: Action, Separator, Spacer, Merge or ActionList. |
| `KToolBarEditor::StatusTextRole` | `259` | The help text shown for a selected element. |
| `KToolBarEditor::IconNameRole` | `260` | The name of the action's icon. |
| `KToolBarEditor::TextAlongsideIconHiddenRole` | `261` | Whether the text is hidden when the toolbar shows text alongside icons. |

## Property Documentation {#property-documentation}

### \[read-only\] availableActions : QAbstractItemModel\* const {#availableActions-prop}

The separator, the expanding spacer and the client's actions not in the toolbar, sorted by text.

**Access functions:**

- `QAbstractItemModel` \***availableActions**() const

### \[read-only\] currentActions : QAbstractItemModel\* const {#currentActions-prop}

The toolbar's elements in their order.

**Access functions:**

- `QAbstractItemModel` \***currentActions**() const

### currentToolBar : int {#currentToolBar-prop}

The index in [toolBars](ktoolbareditor.md#toolBars-prop)() of the toolbar being edited.

**Access functions:**

- `int` **currentToolBar**() const
- `void` **[setCurrentToolBar](ktoolbareditor.md#setCurrentToolBar)**(`int` *index*)

**Notifier signal:**

- `void` **currentToolBarChanged**()

### \[read-only\] toolBars : QStringList {#toolBars-prop}

The user-visible names of the editable toolbars, in the factory's order.

**Access functions:**

- `QStringList` **toolBars**() const

**Notifier signal:**

- `void` **toolBarsChanged**()

## Member Function Documentation {#member-function-documentation}

### \[signal\] void KToolBarEditor::changed() {#changed}

Emitted for every change the user made.

### \[invokable\] int KToolBarEditor::insertAction(int *availableRow*, int *currentRow*, bool *prepend* = false) {#insertAction}

Puts the available element at `availableRow` into the toolbar after the element at `currentRow`, or at its start (`prepend`) or end when `currentRow` is -1. Returns the new row of the inserted element.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### bool KToolBarEditor::load(KXMLGUIFactory \**factory*, const QString &*defaultToolBar* = QString()) {#load}

Loads the toolbars of every client of `factory`, selecting `defaultToolBar` (by name) or the first. Returns false if this editor was already loaded.

### bool KToolBarEditor::load(KActionCollection \**collection*, const QString &*resourceFile*, bool *global* = true, const QString &*defaultToolBar* = QString()) {#load-1}

Loads the toolbars of `resourceFile` (merged with ui\_standards.rc if `global`) with the actions of `collection`. Returns false if this editor was already loaded.

### \[invokable\] int KToolBarEditor::moveAction(int *currentRow*, int *afterRow*) {#moveAction}

Moves the element at `currentRow` to after the element at `afterRow` (its row before the move), or to the start when `afterRow` is -1. Returns its new row.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] int KToolBarEditor::moveDown(int *currentRow*) {#moveDown}

Moves the element at `currentRow` one place down. Returns its new row.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] int KToolBarEditor::moveUp(int *currentRow*) {#moveUp}

Moves the element at `currentRow` one place up. Returns its new row.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void KToolBarEditor::rebuildClients() {#rebuildClients}

Removes and re-adds every client of the factory, so they read their XML again.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void KToolBarEditor::removeAction(int *currentRow*) {#removeAction}

Takes the element at `currentRow` out of the toolbar.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void KToolBarEditor::restoreDefaults() {#restoreDefaults}

Deletes the local XML files, rebuilds the GUI and loads the toolbars again.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void KToolBarEditor::save() {#save}

Saves the changed clients' local XML files and rebuilds the factory's GUI.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void KToolBarEditor::setActionIcon(int *currentRow*, const QString &*iconName*) {#setActionIcon}

Gives the action at `currentRow` the icon named `iconName`.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] void KToolBarEditor::setActionIconText(int *currentRow*, const QString &*text*, bool *textAlongsideIconHidden*) {#setActionIconText}

Gives the action at `currentRow` the icon text `text` (trimmed), shown or hidden alongside its icon.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### void KToolBarEditor::setCurrentToolBar(int *index*) {#setCurrentToolBar}

Selects the toolbar at `index` and reloads its lists, also when it is already the current one.

> **Note:** Setter function for property [currentToolBar](ktoolbareditor.md#currentToolBar-prop).

*See also* [currentToolBar](ktoolbareditor.md#currentToolBar-prop)()
