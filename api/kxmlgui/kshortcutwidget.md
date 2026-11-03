---
title: "KShortcutWidget Class"
description: "Collection of convenience classes and widgets to manage your own main QtWidgets window."
---

# KShortcutWidget Class

Collection of convenience classes and widgets to manage your own main QtWidgets window. [More...](#details)

- **Header:** `#include <KShortcutWidget>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS XmlGui)`  
  `target_link_libraries(mytarget PRIVATE KF6::XmlGui)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kshortcutwidget-members.md)

## Properties

- [modifierlessAllowed : bool](#modifierlessAllowed-prop)

## Public Functions

- [KShortcutWidget(QWidget \*parent = nullptr)](#KShortcutWidget)
- [~KShortcutWidget()](#dtor.KShortcutWidget)
- [bool isModifierlessAllowed()](#isModifierlessAllowed)
- [void setCheckActionCollections(const QList\<KActionCollection \*\> &actionCollections)](#setCheckActionCollections)
- [void setClearButtonsShown(bool show)](#setClearButtonsShown)
- [void setModifierlessAllowed(bool allow)](#setModifierlessAllowed)
- [QList\<QKeySequence\> shortcut() const](#shortcut)

## Public Slots

- [void applyStealShortcut()](#applyStealShortcut)
- [void clearShortcut()](#clearShortcut)
- [void setShortcut(const QList\<QKeySequence\> &cut)](#setShortcut)

## Signals

- [void shortcutChanged(const QList\<QKeySequence\> &cut)](#shortcutChanged)

## Detailed Description {#details}

Provides a widget that lets the user assign a main shortcut and an alternate shortcut for a certain action.

## Property Documentation {#property-documentation}

### modifierlessAllowed : bool {#modifierlessAllowed-prop}

**Access functions:**

- `bool` **[isModifierlessAllowed](kshortcutwidget.md#isModifierlessAllowed)**()
- `void` **[setModifierlessAllowed](kshortcutwidget.md#setModifierlessAllowed)**(`bool` *allow*)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KShortcutWidget::KShortcutWidget(QWidget \**parent* = nullptr) {#KShortcutWidget}

Creates a new shortcut widget as a child of `parent`.

### \[override virtual noexcept\] KShortcutWidget::~KShortcutWidget() {#dtor.KShortcutWidget}

Destructs the shortcut widget.

### \[slot\] void KShortcutWidget::applyStealShortcut() {#applyStealShortcut}

Actually remove the shortcut that the user wanted to steal, from the action that was using it.

To be called before you apply your changes. No shortcuts are stolen until this function is called.

### \[slot\] void KShortcutWidget::clearShortcut() {#clearShortcut}

Unassigns the widget's shortcut.

### bool KShortcutWidget::isModifierlessAllowed() {#isModifierlessAllowed}

Returns whether the set widget shortcut can be set without including a modifier key.

> **Note:** Getter function for property [modifierlessAllowed](kshortcutwidget.md#modifierlessAllowed-prop).

### void KShortcutWidget::setCheckActionCollections(const QList\<KActionCollection \*\> &*actionCollections*) {#setCheckActionCollections}

Sets a list of `actionCollections` to check against for a conflictuous shortcut.

If there is a conflictuous shortcut with a [QAction](https://doc.qt.io/qt-6/qaction.html), and that this shortcut can be configured (that is, KActionCollection::isShortcutConfigurable() returns `true`) the user will be prompted to eventually steal the shortcut from this action.

Global shortcuts are automatically checked for conflicts.

Don't forget to call [applyStealShortcut](kshortcutwidget.md#applyStealShortcut)() to actually steal the shortcut.

### void KShortcutWidget::setClearButtonsShown(bool *show*) {#setClearButtonsShown}

Sets whether to `show` the clear buttons next to the main and alternate shortcuts of the widget.

### void KShortcutWidget::setModifierlessAllowed(bool *allow*) {#setModifierlessAllowed}

Sets whether to `allow` a shortcut that doesn't include a modifier key.

> **Note:** Setter function for property [modifierlessAllowed](kshortcutwidget.md#modifierlessAllowed-prop).

*See also* [isModifierlessAllowed](kshortcutwidget.md#isModifierlessAllowed)()

### \[slot\] void KShortcutWidget::setShortcut(const QList\<QKeySequence\> &*cut*) {#setShortcut}

Sets the given shortcut `cut` to the widget.

*See also* [shortcut](kshortcutwidget.md#shortcut)()

### QList\<QKeySequence\> KShortcutWidget::shortcut() const {#shortcut}

Returns the set shortcut.

*See also* [setShortcut](kshortcutwidget.md#setShortcut)()

### \[signal\] void KShortcutWidget::shortcutChanged(const QList\<QKeySequence\> &*cut*) {#shortcutChanged}

Emitted when the given shortcut `cut` has changed.
