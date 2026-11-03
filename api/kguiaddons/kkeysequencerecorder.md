---
title: "KKeySequenceRecorder Class"
description: "Record a QKeySequence by listening to key events in a window. This class was introduced in Qt 6.0."
---

# KKeySequenceRecorder Class

Record a [QKeySequence](https://doc.qt.io/qt-6/qkeysequence.html) by listening to key events in a window. This class was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <KKeySequenceRecorder>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS GuiAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::GuiAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kkeysequencerecorder-members.md)  
[Deprecated members](kkeysequencerecorder-obsolete.md)

## Public Types

- [enum KKeySequenceRecorder::Pattern](#Pattern-enum)

## Properties

- [currentKeySequence : QKeySequence](#currentKeySequence-prop)
- [\[read-only\] isRecording : bool](#isRecording-prop)
- [multiKeyShortcutsAllowed : bool](#multiKeyShortcutsAllowed-prop)
- [\[since 6.12\] patterns : Patterns](#patterns-prop)
- [window : QWindow\*](#window-prop)

## Public Functions

- [KKeySequenceRecorder(QWindow \*window, QObject \*parent = nullptr)](#KKeySequenceRecorder)
- [void startRecording()](#startRecording)

## Public Slots

- [void cancelRecording()](#cancelRecording)

## Signals

- [void gotKeySequence(const QKeySequence &keySequence)](#gotKeySequence)

## Detailed Description {#details}

After calling [startRecording](kkeysequencerecorder.md#startRecording) key events in the set window will be captured until a valid [QKeySequence](https://doc.qt.io/qt-6/qkeysequence.html) has been recorded and [gotKeySequence](kkeysequencerecorder.md#gotKeySequence) is emitted. See [multiKeyShortcutsAllowed](kkeysequencerecorder.md#multiKeyShortcutsAllowed-prop) and modifierlessAllowed for what constitutes a valid key sequence.

During recording any shortcuts are inhibited and cannot be triggered by grabbing the keyboard.

For graphical elements that record key sequences and can optionally perform conflict checking against existing shortcuts see [KKeySequenceWidget](../kxmlgui/kkeysequencewidget.md) and [KeySequenceItem](../kquickcontrols/qml-org-kde-kquickcontrols-keysequenceitem.md).

Porting from KF5 to KF6:

The class KeySequenceRecorder was renamed to [KKeySequenceRecorder](kkeysequencerecorder.md).

*See also* [KKeySequenceWidget](../kxmlgui/kkeysequencewidget.md), [KeySequenceItem](../kquickcontrols/qml-org-kde-kquickcontrols-keysequenceitem.md)

## Member Type Documentation {#member-type-documentation}

### enum KKeySequenceRecorder::Pattern {#Pattern-enum}

**flags KKeySequenceRecorder::Patterns**

The Pattern type specifies what components the recorded shortcut must have, e.g. modifiers or just a key.

| Constant | Value | Description |
| --- | --- | --- |
| `KKeySequenceRecorder::Modifier` | `0x1` | The recorded shortcut must contain one or more modifier keys (Meta, Shift, Ctrl, or Alt). |
| `KKeySequenceRecorder::Key` | `0x2` | The recorded shortcut must contain only one regular key, e.g. "A". |
| `KKeySequenceRecorder::ModifierAndKey` | `0x4` | The recorded shortcut must contain one or more modifier keys followed by a regular key, e.g. Meta+A. Note: with this pattern, special keys like "Insert" without any pressed modifier will be captured too. Please do not rely on this behavior and instead use Key \| ModifierAndKey explicitly. The future versions of [KKeySequenceRecorder](kkeysequencerecorder.md) are expected not to record special keys in the ModifierAndKey mode. |

The `Patterns` type is a typedef for `QFlags<Pattern>. `It stores an OR combination of `Pattern` values.

## Property Documentation {#property-documentation}

### currentKeySequence : QKeySequence {#currentKeySequence-prop}

The recorded key sequence. After construction this is empty.

During recording it is continuously updated with the newest user input.

After recording it contains the last recorded [QKeySequence](https://doc.qt.io/qt-6/qkeysequence.html)

**Access functions:**

- `QKeySequence` **currentKeySequence**() const
- `void` **setCurrentKeySequence**(const `QKeySequence` &*sequence*)

**Notifier signal:**

- `void` **currentKeySequenceChanged**()

### \[read-only\] isRecording : bool {#isRecording-prop}

Whether key events are currently recorded

**Access functions:**

- `bool` **isRecording**() const

**Notifier signal:**

- `void` **recordingChanged**()

### multiKeyShortcutsAllowed : bool {#multiKeyShortcutsAllowed-prop}

Controls the amount of key combinations that are captured until recording stops and [gotKeySequence](kkeysequencerecorder.md#gotKeySequence) is emitted. By default this is `true` and "Emacs-style" key sequences are recorded. Recording does not stop until four valid key combination have been recorded. Afterwards [currentKeySequence](kkeysequencerecorder.md#currentKeySequence-prop)().count() will be 4.

Otherwise only one key combination is recorded before [gotKeySequence](kkeysequencerecorder.md#gotKeySequence) is emitted with a [QKeySequence](https://doc.qt.io/qt-6/qkeysequence.html) with a count() of 1.

**Access functions:**

- `bool` **multiKeyShortcutsAllowed**() const
- `void` **setMultiKeyShortcutsAllowed**(`bool` *allowed*)

**Notifier signal:**

- `void` **multiKeyShortcutsAllowedChanged**()

*See also* [QKeySequence](https://doc.qt.io/qt-6/qkeysequence.html)

### \[since 6.12\] patterns : Patterns {#patterns-prop}

Specifies what components the recorded shortcut must have, for example whether the shortcut must contain only modifier keys (Modifier) or modifiers keys and a normal key ([ModifierAndKey](kkeysequencerecorder.md#Pattern-enum)).

The patterns property can contain one or more recording patterns. For example, if the recorder accepts both normal and modifier only shortcuts, e.g. Modifier \| [ModifierAndKey](kkeysequencerecorder.md#Pattern-enum).

By default this is [ModifierAndKey](kkeysequencerecorder.md#Pattern-enum).

This property was introduced in Qt 6.12.

**Access functions:**

- `KKeySequenceRecorder::Patterns` **patterns**() const
- `void` **setPatterns**(`KKeySequenceRecorder::Patterns` *patterns*)

**Notifier signal:**

- `void` **patternsChanged**()

### window : QWindow\* {#window-prop}

The window in which the key events are happening that should be recorded

**Access functions:**

- `QWindow` \***window**() const
- `void` **setWindow**(`QWindow` \**window*)

**Notifier signal:**

- `void` **windowChanged**()

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KKeySequenceRecorder::KKeySequenceRecorder(QWindow \**window*, QObject \**parent* = nullptr) {#KKeySequenceRecorder}

Constructor.

`window` The window whose key events will be recorded.

*See also* [window](kkeysequencerecorder.md#window-prop)

### \[slot\] void KKeySequenceRecorder::cancelRecording() {#cancelRecording}

Stops the recording session

### \[signal\] void KKeySequenceRecorder::gotKeySequence(const QKeySequence &*keySequence*) {#gotKeySequence}

This signal is emitted when a key sequence has been recorded.

Compared to [currentKeySequenceChanged](kkeysequencerecorder.md#currentKeySequence-prop) and [currentKeySequence](kkeysequencerecorder.md#currentKeySequence-prop) this is signal is not emitted continuously during recording but only after recording has finished.

### \[invokable\] void KKeySequenceRecorder::startRecording() {#startRecording}

Start recording. Calling startRecording when [window](kkeysequencerecorder.md#window-prop)() is `nullptr` has no effect.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.
