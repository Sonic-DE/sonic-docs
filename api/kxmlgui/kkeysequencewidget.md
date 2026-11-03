---
title: "KKeySequenceWidget Class"
description: "A widget to input a QKeySequence."
---

# KKeySequenceWidget Class

A widget to input a [QKeySequence](https://doc.qt.io/qt-6/qkeysequence.html). [More...](#details)

- **Header:** `#include <KKeySequenceWidget>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS XmlGui)`  
  `target_link_libraries(mytarget PRIVATE KF6::XmlGui)`
- **Inherits:** [QWidget](https://doc.qt.io/qt-6/qwidget.html)

[List of all members, including inherited members](kkeysequencewidget-members.md)  
[Deprecated members](kkeysequencewidget-obsolete.md)

## Public Types

- [enum KKeySequenceWidget::ShortcutType](#ShortcutType-enum)
- [enum KKeySequenceWidget::Validation](#Validation-enum)

## Properties

- [checkForConflictsAgainst : ShortcutTypes](#checkForConflictsAgainst-prop)
- [keySequence : QKeySequence](#keySequence-prop)
- [modifierOnlyAllowed : bool](#modifierOnlyAllowed-prop)
- [multiKeyShortcutsAllowed : bool](#multiKeyShortcutsAllowed-prop)
- [\[since 6.12\] patterns : KKeySequenceRecorder::Patterns](#patterns-prop)
- [\[read-only, since 6.12\] recording : bool](#recording-prop)

## Public Functions

- [KKeySequenceWidget(QWidget \*parent = nullptr)](#KKeySequenceWidget)
- [KKeySequenceWidget::ShortcutTypes checkForConflictsAgainst() const](#checkForConflictsAgainst)
- [bool isKeySequenceAvailable(const QKeySequence &seq) const](#isKeySequenceAvailable)
- [bool isRecording() const](#isRecording) (since 6.12)
- [QKeySequence keySequence() const](#keySequence)
- [bool multiKeyShortcutsAllowed() const](#multiKeyShortcutsAllowed)
- [KKeySequenceRecorder::Patterns patterns() const](#patterns) (since 6.12)
- [void setCheckActionCollections(const QList\<KActionCollection \*\> &actionCollections)](#setCheckActionCollections)
- [void setCheckForConflictsAgainst(KKeySequenceWidget::ShortcutTypes types)](#setCheckForConflictsAgainst)
- [void setClearButtonShown(bool show)](#setClearButtonShown)
- [void setComponentName(const QString &componentName)](#setComponentName)
- [void setMultiKeyShortcutsAllowed(bool)](#setMultiKeyShortcutsAllowed)
- [void setPatterns(KKeySequenceRecorder::Patterns patterns)](#setPatterns) (since 6.12)

## Public Slots

- [void applyStealShortcut()](#applyStealShortcut)
- [void captureKeySequence()](#captureKeySequence)
- [void clearKeySequence()](#clearKeySequence)
- [void setKeySequence(const QKeySequence &seq, KKeySequenceWidget::Validation val = NoValidate)](#setKeySequence)

## Signals

- [void keySequenceChanged(const QKeySequence &seq)](#keySequenceChanged)
- [void recordingChanged()](#recordingChanged) (since 6.12)
- [void stealShortcut(const QKeySequence &seq, QAction \*action)](#stealShortcut)

## Detailed Description {#details}

This widget lets the user choose a [QKeySequence](https://doc.qt.io/qt-6/qkeysequence.html), which is usually used as a shortcut key. The recording is initiated by calling [captureKeySequence](kkeysequencewidget.md#captureKeySequence)() or by the user clicking on the widget.

The widgets provides support for conflict handling.

*See also* [setCheckForConflictsAgainst](kkeysequencewidget.md#setCheckForConflictsAgainst)()

## Member Type Documentation {#member-type-documentation}

### enum KKeySequenceWidget::ShortcutType {#ShortcutType-enum}

**flags KKeySequenceWidget::ShortcutTypes**

| Constant | Value | Description |
| --- | --- | --- |
| `KKeySequenceWidget::None` | `0x00` | No checking for conflicts. |
| `KKeySequenceWidget::LocalShortcuts` | `0x01` | Check with local shortcuts. |
| `KKeySequenceWidget::StandardShortcuts` | `0x02` | Check against standard shortcuts. |
| `KKeySequenceWidget::GlobalShortcuts` | `0x04` | Check against global shortcuts. |

The `ShortcutTypes` type is a typedef for `QFlags<ShortcutType>. `It stores an OR combination of `ShortcutType` values.

*See also* [setCheckActionCollections](kkeysequencewidget.md#setCheckActionCollections)(), [KStandardShortcut](../kconfiggui/kstandardshortcut.md), [KGlobalAccel](../kglobalaccel/kglobalaccel-index.md)

### enum KKeySequenceWidget::Validation {#Validation-enum}

An enum about validation when setting a key sequence.

| Constant | Value | Description |
| --- | --- | --- |
| `KKeySequenceWidget::Validate` | `0` | Validate key sequence. |
| `KKeySequenceWidget::NoValidate` | `1` | Use key sequence without validation. |

*See also* [setKeySequence](kkeysequencewidget.md#setKeySequence)()

## Property Documentation {#property-documentation}

### checkForConflictsAgainst : ShortcutTypes {#checkForConflictsAgainst-prop}

**Access functions:**

- `KKeySequenceWidget::ShortcutTypes` **[checkForConflictsAgainst](kkeysequencewidget.md#checkForConflictsAgainst)**() const
- `void` **[setCheckForConflictsAgainst](kkeysequencewidget.md#setCheckForConflictsAgainst)**(`KKeySequenceWidget::ShortcutTypes` *types*)

### keySequence : QKeySequence {#keySequence-prop}

**Access functions:**

- `QKeySequence` **[keySequence](kkeysequencewidget.md#keySequence)**() const
- `void` **[setKeySequence](kkeysequencewidget.md#setKeySequence)**(const `QKeySequence` &*seq*, `KKeySequenceWidget::Validation` *val* = NoValidate)

**Notifier signal:**

- `void` **[keySequenceChanged](kkeysequencewidget.md#keySequenceChanged)**(const `QKeySequence` &*seq*)

### modifierOnlyAllowed : bool {#modifierOnlyAllowed-prop}

### multiKeyShortcutsAllowed : bool {#multiKeyShortcutsAllowed-prop}

**Access functions:**

- `bool` **[multiKeyShortcutsAllowed](kkeysequencewidget.md#multiKeyShortcutsAllowed)**() const
- `void` **[setMultiKeyShortcutsAllowed](kkeysequencewidget.md#setMultiKeyShortcutsAllowed)**(*bool*)

### \[since 6.12\] patterns : KKeySequenceRecorder::Patterns {#patterns-prop}

Specifies the accepted shortcut formats.

Default is KKeySequenceRecorder::ModifierAndKey.

This property was introduced in Qt 6.12.

**Access functions:**

- `KKeySequenceRecorder::Patterns` **[patterns](kkeysequencewidget.md#patterns)**() const
- `void` **[setPatterns](kkeysequencewidget.md#setPatterns)**(`KKeySequenceRecorder::Patterns` *patterns*)

### \[read-only, since 6.12\] recording : bool {#recording-prop}

Indicates whether a key sequence is currently being recorded.

This property was introduced in Qt 6.12.

**Access functions:**

- `bool` **[isRecording](kkeysequencewidget.md#isRecording)**() const

**Notifier signal:**

- `void` **[recordingChanged](kkeysequencewidget.md#recordingChanged)**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KKeySequenceWidget::KKeySequenceWidget(QWidget \**parent* = nullptr) {#KKeySequenceWidget}

Constructs a widget used to input a [QKeySequence](https://doc.qt.io/qt-6/qkeysequence.html).

### \[slot\] void KKeySequenceWidget::applyStealShortcut() {#applyStealShortcut}

Actually remove the shortcut that the user wanted to steal, from the action that was using it.

This only applies to actions provided to us by [setCheckActionCollections](kkeysequencewidget.md#setCheckActionCollections)() and setCheckActionList().

Global and Standard Shortcuts have to be stolen immediately when the user gives their consent (technical reasons). That means those changes will be active even if you never call applyStealShortcut().

To be called before you apply your changes. No local shortcuts are stolen until this function is called.

### \[slot\] void KKeySequenceWidget::captureKeySequence() {#captureKeySequence}

Capture a shortcut from the keyboard.

This call will only return once a key sequence has been captured or input was aborted.

If a key sequence was input, [keySequenceChanged](kkeysequencewidget.md#keySequenceChanged)() will be emitted.

*See also* [setModifierlessAllowed](kkeysequencewidget-obsolete.md#setModifierlessAllowed)()

### KKeySequenceWidget::ShortcutTypes KKeySequenceWidget::checkForConflictsAgainst() const {#checkForConflictsAgainst}

The shortcut types we check for conflicts.

> **Note:** Getter function for property [checkForConflictsAgainst](kkeysequencewidget.md#checkForConflictsAgainst-prop).

*See also* [setCheckForConflictsAgainst](kkeysequencewidget.md#setCheckForConflictsAgainst)()

### \[slot\] void KKeySequenceWidget::clearKeySequence() {#clearKeySequence}

Clears the key sequence.

### bool KKeySequenceWidget::isKeySequenceAvailable(const QKeySequence &*seq*) const {#isKeySequenceAvailable}

Returns whether the key sequence `seq` is available to grab.

The sequence is checked under the same rules as if it has been typed by the user. This method is useful if you get key sequences from another input source and want to check if it is save to set them.

### \[since 6.12\] bool KKeySequenceWidget::isRecording() const {#isRecording}

Returns `true` if a key sequence is currently being recorded; otherwise returns `false`.

> **Note:** Getter function for property [recording](kkeysequencewidget.md#recording-prop).

This function was introduced in Qt 6.12.

### QKeySequence KKeySequenceWidget::keySequence() const {#keySequence}

Returns the currently selected key sequence.

> **Note:** Getter function for property [keySequence](kkeysequencewidget.md#keySequence-prop).

*See also* [setKeySequence](kkeysequencewidget.md#setKeySequence)()

### \[signal\] void KKeySequenceWidget::keySequenceChanged(const QKeySequence &*seq*) {#keySequenceChanged}

This signal is emitted when the current key sequence `seq` has changed, be it by user input or programmatically.

> **Note:** Notifier signal for property [keySequence](kkeysequencewidget.md#keySequence-prop).

### bool KKeySequenceWidget::multiKeyShortcutsAllowed() const {#multiKeyShortcutsAllowed}

Returns whether multikey shortcuts are allowed.

> **Note:** Getter function for property [multiKeyShortcutsAllowed](kkeysequencewidget.md#multiKeyShortcutsAllowed-prop).

*See also* [setMultiKeyShortcutsAllowed](kkeysequencewidget.md#setMultiKeyShortcutsAllowed)()

### \[since 6.12\] KKeySequenceRecorder::Patterns KKeySequenceWidget::patterns() const {#patterns}

Returns the accepted shortcut patterns.

Default is Modifier \| Key

> **Note:** Getter function for property [patterns](kkeysequencewidget.md#patterns-prop).

This function was introduced in Qt 6.12.

*See also* [setPatterns](kkeysequencewidget.md#setPatterns)()

### \[signal, since 6.12\] void KKeySequenceWidget::recordingChanged() {#recordingChanged}

This signal is emitted when the user begins or finishes recording a key sequence. It is not emitted when the current key sequence is changed using [setKeySequence](kkeysequencewidget.md#setKeySequence)().

> **Note:** Notifier signal for property [recording](kkeysequencewidget.md#recording-prop).

This function was introduced in Qt 6.12.

### void KKeySequenceWidget::setCheckActionCollections(const QList\<KActionCollection \*\> &*actionCollections*) {#setCheckActionCollections}

Sets a list of `actionCollections` to check against for conflictuous shortcut.

If a [QAction](https://doc.qt.io/qt-6/qaction.html) with a conflicting shortcut is found inside this list and its shortcut can be configured (KActionCollection::isShortcutConfigurable() returns true) the user will be prompted whether to steal the shortcut from this action.

*See also* [setCheckForConflictsAgainst](kkeysequencewidget.md#setCheckForConflictsAgainst)()

### void KKeySequenceWidget::setCheckForConflictsAgainst(KKeySequenceWidget::ShortcutTypes *types*) {#setCheckForConflictsAgainst}

Configure if the widget should check for conflicts with existing shortcut `types`.

When capturing a key sequence for local shortcuts you should check against [GlobalShortcuts](kkeysequencewidget.md#ShortcutType-enum) and your other local shortcuts. This is the default.

You have to provide the local actions to check against with [setCheckActionCollections](kkeysequencewidget.md#setCheckActionCollections)().

When capturing a key sequence for a global shortcut you should check against [StandardShortcuts](kkeysequencewidget.md#ShortcutType-enum), [GlobalShortcuts](kkeysequencewidget.md#ShortcutType-enum) and your local shortcuts.

There are two ways to react to a user agreeing to steal a shortcut:

1. Listen to the [stealShortcut](kkeysequencewidget.md#stealShortcut)() signal and steal the shortcuts manually. It's your responsibility to save that change later when you think it is appropriate.

2. Call [applyStealShortcut](kkeysequencewidget.md#applyStealShortcut)() and [KKeySequenceWidget](kkeysequencewidget.md) will steal the shortcut. This will save the actionCollections the shortcut is part of so make sure it doesn't inadvertly save some unwanted changes too. Read its documentation for some limitation when handling global shortcuts.

If you want to do the conflict checking yourself here are some code snippets for global ...

```cpp
QStringList conflicting = KGlobalAccel::findActionNameSystemwide(keySequence);
if (!conflicting.isEmpty()) {
    // Inform and ask the user about the conflict and reassigning
    // the keys sequence
    if (!KGlobalAccel::promptStealShortcutSystemwide(q, conflicting, keySequence)) {
        return true;
    }
    KGlobalAccel::stealShortcutSystemwide(keySequence);
}
```

... and standard shortcuts

```cpp
KStandardShortcut::StandardShortcut ssc = KStandardShortcut::find(keySequence);
if (ssc != KStandardShortcut::AccelNone) {
    // We have a conflict
}
```

> **Note:** Setter function for property [checkForConflictsAgainst](kkeysequencewidget.md#checkForConflictsAgainst-prop).

*See also* [checkForConflictsAgainst](kkeysequencewidget.md#checkForConflictsAgainst)()

### void KKeySequenceWidget::setClearButtonShown(bool *show*) {#setClearButtonShown}

Sets whether to `show` a small button to set an empty key sequence next to the main input widget.

The default is to show the clear button.

### void KKeySequenceWidget::setComponentName(const QString &*componentName*) {#setComponentName}

Sets the `componentName` for the component using this widget.

If the component using this widget supports shortcuts contexts, it must set its component name so we can check conflicts correctly.

### \[slot\] void KKeySequenceWidget::setKeySequence(const QKeySequence &*seq*, KKeySequenceWidget::Validation *val* = NoValidate) {#setKeySequence}

Sets the key sequence `seq`.

If `val` == Validate, and the call is actually changing the key sequence, conflictuous shortcut will be checked.

> **Note:** Setter function for property [keySequence](kkeysequencewidget.md#keySequence-prop).

*See also* [keySequence](kkeysequencewidget.md#keySequence)()

### void KKeySequenceWidget::setMultiKeyShortcutsAllowed(*bool*) {#setMultiKeyShortcutsAllowed}

Sets whether to allow for multikey shortcuts.

> **Note:** Setter function for property [multiKeyShortcutsAllowed](kkeysequencewidget.md#multiKeyShortcutsAllowed-prop).

*See also* [multiKeyShortcutsAllowed](kkeysequencewidget.md#multiKeyShortcutsAllowed)()

### \[since 6.12\] void KKeySequenceWidget::setPatterns(KKeySequenceRecorder::Patterns *patterns*) {#setPatterns}

Sets the accepted shortcut patterns to `patterns`. A shortcut pattern specifies what components the recoreded shortcut must have, e.g. whether it should include modifier keys, etc.

> **Note:** Setter function for property [patterns](kkeysequencewidget.md#patterns-prop).

This function was introduced in Qt 6.12.

*See also* [patterns](kkeysequencewidget.md#patterns)()

### \[signal\] void KKeySequenceWidget::stealShortcut(const QKeySequence &*seq*, QAction \**action*) {#stealShortcut}

This signal is emitted after the user agreed to steal a shortcut sequence `seq` from an `action`.

This is only done for local shortcuts. So you can be sure `action` is one of the actions you provided with setCheckActionList() or [setCheckActionCollections](kkeysequencewidget.md#setCheckActionCollections)().

If you listen to that signal and don't call [applyStealShortcut](kkeysequencewidget.md#applyStealShortcut)() you are supposed to steal the shortcut and save this change.
