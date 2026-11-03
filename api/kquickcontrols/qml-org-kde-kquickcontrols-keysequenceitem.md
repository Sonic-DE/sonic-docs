---
title: "KeySequenceItem QML Type"
description: "Extensions to Qt Quick Controls."
---

# KeySequenceItem QML Type

Extensions to Qt Quick Controls. [More...](#details)

- Import Statement: import org.kde.kquickcontrols
- Inherits: [RowLayout](https://doc.qt.io/qt-6/qml-qtquick-layouts-rowlayout.html)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### checkForConflictsAgainst : enumeration {#checkForConflictsAgainst-prop}

Controls which types of shortcuts are checked for conflicts when the [keySequence](qml-org-kde-kquickcontrols-keysequenceitem.md#keySequence-prop) is set.

If a conflict is detected, a messagebox will be shown asking the user to confirm their input. Valid values are combinations of the following flags:

| Constant | Description |
| --- | --- |
| ShortcutType.None | Do not check for conflicts. |
| ShortcutType.StandardShortcuts | Check against standard shortcuts. |
| ShortcutType.GlobalShortcuts | Check against global shortcuts. |

The default is `ShortcutType.GlobalShortcuts | ShortcutType.StandardShortcut`.

*See also* KStandardShortcut, KGlobalAccel

### currentKeySequence : keySequence {#currentKeySequence-prop}

### keySequence : alias {#keySequence-prop}

### multiKeyShortcutsAllowed : bool {#multiKeyShortcutsAllowed-prop}

### \[since 6.16\] patterns : enumeration {#patterns-prop}

Specifies what components the recorded shortcut must have, for example whether the shortcut must contain only modifier keys (Modifier) or modifiers keys and a normal key (ModifierAndKey).

The patterns property can contain one or more recording patterns. For example, if the recorder accepts both normal and modifier only shortcuts, e.g. Modifier \| ModifierAndKey. Valid values are combinations of the following flags:

| Constant | Description |
| --- | --- |
| ShortcutPattern.Modifier | The recorded shortcut must contain one or more modifier keys (Meta, Shift, Ctrl, or Alt). |
| ShortcutPattern.Key | The recorded shortcut must contain only one regular key, e.g. "A". |
| ShortcutPattern.ModifierAndKey | The recorded shortcut must contain one or more modifier keys followed by a regular key, e.g. Meta+A. |

The default is `ShortcutPattern.ModifierAndKey`.

This property was introduced in Qt 6.16.

### showCancelButton : bool {#showCancelButton-prop}

### showClearButton : bool {#showClearButton-prop}

## Signal Documentation {#signal-documentation}

### keySequenceModified() {#keySequenceModified-signal}

Emitted whenever the key sequence is modified by the user, interacting with the component.

Either by interacting capturing a key sequence or pressing the clear button.

> **Note:** The corresponding handler is `onKeySequenceModified`.

## Method Documentation {#method-documentation}

### startCapturing() {#startCapturing-method}

Start capturing a key sequence.

This is equivalent to the user clicking on the main button of the item.
