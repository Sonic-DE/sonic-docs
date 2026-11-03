---
title: "KShortcutsDialog Class"
description: "Dialog for configuration of KActionCollection and KGlobalAccel."
---

# KShortcutsDialog Class

Dialog for configuration of [KActionCollection](kactioncollection.md) and [KGlobalAccel](../kglobalaccel/kglobalaccel-module.md). [More...](#details)

- **Header:** `#include <KShortcutsDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS XmlGui)`  
  `target_link_libraries(mytarget PRIVATE KF6::XmlGui)`
- **Inherits:** [QDialog](https://doc.qt.io/qt-6/qdialog.html)

[List of all members, including inherited members](kshortcutsdialog-members.md)

## Public Functions

- [KShortcutsDialog(QWidget \*parent)](#KShortcutsDialog)
- [KShortcutsDialog(KShortcutsEditor::ActionTypes actionTypes = KShortcutsEditor::AllActions, KShortcutsEditor::LetterShortcuts allowLetterShortcuts = KShortcutsEditor::LetterShortcutsAllowed, QWidget \*parent = nullptr)](#KShortcutsDialog-1)
- [~KShortcutsDialog()](#dtor.KShortcutsDialog)
- [QList\<KActionCollection \*\> actionCollections() const](#actionCollections)
- [void addActionToSchemesMoreButton(QAction \*action)](#addActionToSchemesMoreButton)
- [void addCollection(KActionCollection \*collection, const QString &title = {})](#addCollection)
- [bool configure(bool saveSettings = true)](#configure)
- [void exportConfiguration(const QString &path) const](#exportConfiguration)
- [void importConfiguration(const QString &path)](#importConfiguration)
- [void refreshSchemes()](#refreshSchemes)
- [QSize sizeHint() const](#sizeHint)

## Public Slots

- [void accept()](#accept)

## Signals

- [void saved()](#saved)

## Static Public Members

- [void showDialog(KActionCollection \*collection, KShortcutsEditor::LetterShortcuts allowLetterShortcuts = KShortcutsEditor::LetterShortcutsAllowed, QWidget \*parent = nullptr)](#showDialog)

## Detailed Description {#details}

This dialog can be used to configure keyboard shortcuts associated with actions in [KActionCollection](kactioncollection.md) and [KGlobalAccel](../kglobalaccel/kglobalaccel-module.md). It integrates the [KShortcutsEditor](kshortcutseditor.md) widget and offers various functionalities related to keyboard shortcuts (e.g. reset all shortcuts to defaults, manage shortcuts schemes ...etc).

Several static methods are supplied, which provide a convenient interface to the dialog. The most common, and most encouraged, use is with a [KActionCollection](kactioncollection.md).

```cpp
KShortcutsDialog::configure(actionCollection(), KShortcutsEditor::LetterShortcutsAllowed, parent);

// Alternatively, since 5.84, you can use:
KShortcutsDialog::showDialog(actionCollection(), KShortcutsEditor::LetterShortcutsAllowed, parent);
```

By default this dialog is modal (since 4.3). If you don't want that, call `setModal(false)` and then the non-static [configure](kshortcutsdialog.md#configure)() method to show the dialog.

If you need to run some extra code when the dialog is closed, connect to the signals emitted by `QDialog` ([accepted](https://doc.qt.io/qt-6/qdialog.html#accepted)(), [rejected](https://doc.qt.io/qt-6/qdialog.html#rejected)(), [finished](https://doc.qt.io/qt-6/qdialog.html#finished)() ...etc.). However, note that if that extra code depends on the changed settings having already been saved, connect to the `saved()` signal instead to be on the safe side (if you connect to e.g. `QDialog::accepted()` your function might be called before the changes have actually been saved).

> **Note:** Starting from 5.95, if there are no Global shortcuts in any of the action collections shown in the dialog, the relevant columns ("Global" and "Global Alternate") will be hidden.

Example:

```cpp
// Create the dialog; alternatively you can use the other constructor if e.g.
// you need to only show certain action types, or disallow single letter shortcuts
KShortcutsDialog *dlg = new KShortcutsDialog(parent);

// Set the Qt::WA_DeleteOnClose attribute, so that the dialog is automatically
// deleted after it's closed
dlg->setAttribute(Qt::WA_DeleteOnClose);

// Add an action collection (otherwise the dialog would be empty)
dlg->addCollection(actionCollection());

// Run some extra code after the settings are saved
connect(dlg, &KShortcutsDialog::saved, this, &ClassFoo::doExtraStuff);

// Called with "true" so that the changes are saved if the dialog is accepted,
// see the configure(bool) method for more details
dlg->configure(true);
```

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KShortcutsDialog::KShortcutsDialog(QWidget \**parent*) {#KShortcutsDialog}

Constructs a [KShortcutsDialog](kshortcutsdialog.md) as a child of `parent`, with the default settings.

The default settings are [KShortcutsEditor::AllActions](kshortcutseditor.md#ActionType-enum) and [KShortcutsEditor::LetterShortcutsAllowed](kshortcutseditor.md#LetterShortcuts-enum).

Typically a [KActionCollection](kactioncollection.md) is added by using [addCollection](kshortcutsdialog.md#addCollection)().

`parent` The parent widget of the dialog. If not, `nullptr` will be used by the window manager to place the dialog relative to it.

### \[explicit\] KShortcutsDialog::KShortcutsDialog(KShortcutsEditor::ActionTypes *actionTypes* = KShortcutsEditor::AllActions, KShortcutsEditor::LetterShortcuts *allowLetterShortcuts* = KShortcutsEditor::LetterShortcutsAllowed, QWidget \**parent* = nullptr) {#KShortcutsDialog-1}

Constructs a [KShortcutsDialog](kshortcutsdialog.md) as a child of `parent`.

`actionTypes` Sets the action types to be shown in the dialog. This is an OR combination of `KShortcutsEditor::ActionTypes`; the default is `KShortcutsEditor::AllActions`.

`allowLetterShortcuts` Set to false if unmodified alphanumeric keys ('A', '1', etc.) are not permissible shortcuts.

`parent` parent widget of the dialog, if not set `nullptr` will be used by the window manager to place the dialog relative to it.

*See also* [KShortcutsEditor::LetterShortcuts](kshortcutseditor.md#LetterShortcuts-enum)

### \[override virtual noexcept\] KShortcutsDialog::~KShortcutsDialog() {#dtor.KShortcutsDialog}

Destructor.

Deletes all resources used by a [KShortcutsDialog](kshortcutsdialog.md) object.

### \[override virtual slot\] void KShortcutsDialog::accept() {#accept}

Reimplements: [QDialog::accept()](https://doc.qt.io/qt-6/qdialog.html#accept).

### QList\<KActionCollection \*\> KShortcutsDialog::actionCollections() const {#actionCollections}

Returns the list of action collections that are available for configuration in the dialog.

### void KShortcutsDialog::addActionToSchemesMoreButton(QAction \**action*) {#addActionToSchemesMoreButton}

Adds an `action` to the "More Actions" menu.

This is useful to add for example an action to download more keyboard schemes via KNewStuff.

### void KShortcutsDialog::addCollection(KActionCollection \**collection*, const QString &*title* = {}) {#addCollection}

Adds all actions of the `collection` to the ones displayed and configured by the dialog.

`title` The title associated with the collection. If null, the KAboutData::progName() of the collection's componentData is used).

### bool KShortcutsDialog::configure(bool *saveSettings* = true) {#configure}

Runs the dialog and call writeSettings() on the action collections that were added if `saveSettings` is true.

If the dialog is modal this method will use `QDialog::exec()` to open the dialog, otherwise it will use `QDialog::show()`.

### void KShortcutsDialog::exportConfiguration(const QString &*path*) const {#exportConfiguration}

Exports a shortcut set up from `path`.

### void KShortcutsDialog::importConfiguration(const QString &*path*) {#importConfiguration}

Imports a shortcut set up from `path`.

### void KShortcutsDialog::refreshSchemes() {#refreshSchemes}

Reloads the list of schemes in the "Manage Schemes" section.

This is useful if the available scheme files changed for some reason (for example, because KNewStuff was used).

### \[signal\] void KShortcutsDialog::saved() {#saved}

Emitted after the dialog is accepted (by clicking the OK button) and settings are saved.

Connect to this signal if you need to run some extra code after the settings are saved.

### \[static\] void KShortcutsDialog::showDialog(KActionCollection \**collection*, KShortcutsEditor::LetterShortcuts *allowLetterShortcuts* = KShortcutsEditor::LetterShortcutsAllowed, QWidget \**parent* = nullptr) {#showDialog}

This static method shows a modal dialog that can be used to configure the shortcuts associated with each action in `collection`.

The new shortcut settings will be saved and applied if the dialog is accepted.

The dialog is opened by using `QDialog::show()`, and it will be deleted automatically when it's closed.

Example usage:

```cpp
// Typical usage is with a KActionCollection:
KShortcutsDialog::showDialog(actionCollection(), KShortcutsEditor::LetterShortcutsAllowed, parent);
```

`collection` The [KActionCollection](kactioncollection.md) to configure.

`allowLetterShortcuts` Set to `KShortcutsEditor::LetterShortcutsDisallowed` if unmodified alphanumeric keys ('A', '1', etc.) are not permissible shortcuts.

`parent` The parent widget of the dialog, if not set `nullptr` will be used by the window manager to place the dialog relative to it.

### \[override virtual\] QSize KShortcutsDialog::sizeHint() const {#sizeHint}

Reimplements: [QDialog::sizeHint() const](https://doc.qt.io/qt-6/qdialog.html#sizeHint).

*See also* [QWidget::sizeHint](https://doc.qt.io/qt-6/qwidget.html#sizeHint-prop)()
