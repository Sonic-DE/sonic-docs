---
title: "KShortcutsEditor Class"
description: "Widget for configuration of KAccel and KGlobalAccel."
---

# KShortcutsEditor Class

Widget for configuration of KAccel and [KGlobalAccel](../kglobalaccel/kglobalaccel-module.md). [More...](#details)

- **Header:** `#include <KShortcutsEditor>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS XmlGui)`  
  `target_link_libraries(mytarget PRIVATE KF6::XmlGui)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kshortcutseditor-members.md)

## Public Types

- [enum KShortcutsEditor::ActionType](#ActionType-enum)
- [enum KShortcutsEditor::LetterShortcuts](#LetterShortcuts-enum)

## Properties

- [actionTypes : ActionTypes](#actionTypes-prop)

## Public Functions

- [KShortcutsEditor(KActionCollection \*collection, QWidget \*parent, KShortcutsEditor::ActionTypes actionTypes = AllActions, KShortcutsEditor::LetterShortcuts allowLetterShortcuts = LetterShortcutsAllowed)](#KShortcutsEditor)
- [KShortcutsEditor(QWidget \*parent, KShortcutsEditor::ActionTypes actionTypes = AllActions, KShortcutsEditor::LetterShortcuts allowLetterShortcuts = LetterShortcutsAllowed)](#KShortcutsEditor-1)
- [~KShortcutsEditor()](#dtor.KShortcutsEditor)
- [KShortcutsEditor::ActionTypes actionTypes() const](#actionTypes)
- [void addCollection(KActionCollection \*, const QString &title = QString())](#addCollection)
- [void clearCollections()](#clearCollections)
- [bool isModified() const](#isModified)
- [void save()](#save)
- [void setActionTypes(KShortcutsEditor::ActionTypes actionTypes)](#setActionTypes)
- [void undo()](#undo)

## Public Slots

- [void allDefault()](#allDefault)

## Signals

- [void keyChange()](#keyChange)

## Detailed Description {#details}

Configure dictionaries of key/action associations for QActions, including global shortcuts.

The class takes care of all aspects of configuration, including handling key conflicts internally. Connect to the [allDefault](kshortcutseditor.md#allDefault)() slot if you want to set all configurable shortcuts to their default values.

*See also* [KShortcutsDialog](kshortcutsdialog.md)

## Member Type Documentation {#member-type-documentation}

### enum KShortcutsEditor::ActionType {#ActionType-enum}

**flags KShortcutsEditor::ActionTypes**

| Constant | Value | Description |
| --- | --- | --- |
| `KShortcutsEditor::WidgetAction` | `Qt::WidgetShortcut` | Actions which are triggered by any keypress in a widget that has the action added to it. |
| `KShortcutsEditor::WindowAction` | `Qt::WindowShortcut` | Actions which are triggered by any keypress in a window that has the action added to it or its child widget(s). |
| `KShortcutsEditor::ApplicationAction` | `Qt::ApplicationShortcut` | Actions that are triggered by any keypress in the application. |
| `KShortcutsEditor::GlobalAction` | `4` | Actions which are triggered by any keypress in the windowing system. |
| `KShortcutsEditor::AllActions` | `0xffffffff` | A combination of all available actions. > **Note:** Since 5.95, GlobalAction is ignored if there are no actual Global shortcuts in any of the action collections that are added. |

The `ActionTypes` type is a typedef for `QFlags<ActionType>. `It stores an OR combination of `ActionType` values.

### enum KShortcutsEditor::LetterShortcuts {#LetterShortcuts-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KShortcutsEditor::LetterShortcutsDisallowed` | `0` | Shortcuts without a modifier are not allowed, so 'A' would not be valid, whereas 'Ctrl+A' would be. This only applies to printable characters, however. 'F1', 'Insert' etc. could still be used. |
| `KShortcutsEditor::LetterShortcutsAllowed` | `1` | Letter shortcuts are allowed. |

## Property Documentation {#property-documentation}

### actionTypes : ActionTypes {#actionTypes-prop}

**Access functions:**

- `KShortcutsEditor::ActionTypes` **[actionTypes](kshortcutseditor.md#actionTypes)**() const
- `void` **[setActionTypes](kshortcutseditor.md#setActionTypes)**(`KShortcutsEditor::ActionTypes` *actionTypes*)

## Member Function Documentation {#member-function-documentation}

### KShortcutsEditor::KShortcutsEditor(KActionCollection \**collection*, QWidget \**parent*, KShortcutsEditor::ActionTypes *actionTypes* = AllActions, KShortcutsEditor::LetterShortcuts *allowLetterShortcuts* = LetterShortcutsAllowed) {#KShortcutsEditor}

Constructor.

`collection` The [KActionCollection](kactioncollection.md) to configure.

`parent` Parent widget.

`actionTypes` Types of actions to display in this widget.

`allowLetterShortcuts` Set to [LetterShortcutsDisallowed](kshortcutseditor.md#LetterShortcuts-enum) if unmodified alphanumeric keys ('A', '1', etc.) are not permissible shortcuts.

### \[explicit\] KShortcutsEditor::KShortcutsEditor(QWidget \**parent*, KShortcutsEditor::ActionTypes *actionTypes* = AllActions, KShortcutsEditor::LetterShortcuts *allowLetterShortcuts* = LetterShortcutsAllowed) {#KShortcutsEditor-1}

Creates a key chooser without a starting action collection.

`parent` Parent widget.

`actionTypes` Types of actions to display in this widget.

`allowLetterShortcuts` Set to [LetterShortcutsDisallowed](kshortcutseditor.md#LetterShortcuts-enum) if unmodified alphanumeric keys ('A', '1', etc.) are not permissible shortcuts.

This function overloads [KShortcutsEditor::KShortcutsEditor()](kshortcutseditor.md#KShortcutsEditor).

### \[override virtual noexcept\] KShortcutsEditor::~KShortcutsEditor() {#dtor.KShortcutsEditor}

Destructor

### KShortcutsEditor::ActionTypes KShortcutsEditor::actionTypes() const {#actionTypes}

Returns The types of actions currently displayed in this widget.

> **Note:** Getter function for property [actionTypes](kshortcutseditor.md#actionTypes-prop).

*See also* [setActionTypes](kshortcutseditor.md#setActionTypes)()

### void KShortcutsEditor::addCollection(*KActionCollection \**, const QString &*title* = QString()) {#addCollection}

Insert an action collection, i.e. add all its actions to the ones already associated with the [KShortcutsEditor](kshortcutseditor.md) object.

`title` Subtree title of this collection of shortcut.

### \[slot\] void KShortcutsEditor::allDefault() {#allDefault}

Sets all shortcuts to their default values (bindings).

### void KShortcutsEditor::clearCollections() {#clearCollections}

Removes all action collections from the editor

### bool KShortcutsEditor::isModified() const {#isModified}

Returns whether there are unsaved changes.

### \[signal\] void KShortcutsEditor::keyChange() {#keyChange}

Emitted when an action's shortcut has been changed.

### void KShortcutsEditor::save() {#save}

Save the changes.

This saves the actions to disk. Any [KActionCollection](kactioncollection.md) objects with the xmlFile() value set will be written to an XML file. All others will be written to the application's rc file.

### void KShortcutsEditor::setActionTypes(KShortcutsEditor::ActionTypes *actionTypes*) {#setActionTypes}

Sets the types of actions to display in this widget.

`actionTypes` New types of actions.

> **Note:** Setter function for property [actionTypes](kshortcutseditor.md#actionTypes-prop).

*See also* [actionTypes](kshortcutseditor.md#actionTypes)()

### void KShortcutsEditor::undo() {#undo}

Undo all changes made since the last [save](kshortcutseditor.md#save)().
