---
title: "Obsolete Members for KKeySequenceRecorder"
description: "Deprecated members of KKeySequenceRecorder."
parent: "kguiaddons/kkeysequencerecorder"
---

# Obsolete Members for KKeySequenceRecorder

**The following members of class [KKeySequenceRecorder](kkeysequencerecorder.md) are deprecated.** We strongly advise against using them in new code.

## Properties

- [\[deprecated in 6.12\] modifierOnlyAllowed : bool](#modifierOnlyAllowed-prop)
- [\[deprecated in 6.12\] modifierlessAllowed : bool](#modifierlessAllowed-prop)

## Public Functions

- [bool modifierOnlyAllowed() const](#modifierOnlyAllowed) (deprecated in 6.12)
- [bool modifierlessAllowed() const](#modifierlessAllowed) (deprecated in 6.12)
- [void setModifierOnlyAllowed(bool allowed)](#setModifierOnlyAllowed) (deprecated in 6.12)
- [void setModifierlessAllowed(bool allowed)](#setModifierlessAllowed) (deprecated in 6.12)

## Obsolete Property Documentation {#obsolete-property-documentation}

### \[deprecated in 6.12\] modifierOnlyAllowed : bool {#modifierOnlyAllowed-prop}

This property is deprecated since 6.12. We strongly advise against using it in new code.

It makes it acceptable for the key sequence to be just a modifier (e.g. Shift or Control)

By default, if only a modifier is pressed and then released, the component will remain waiting for the sequence. When enabled, it will take the modifier key as the key sequence.

By default this is `false`.

Use the patterns property instead.

**Access functions:**

- `bool` **[modifierOnlyAllowed](kkeysequencerecorder-obsolete.md#modifierOnlyAllowed)**() const
- `void` **[setModifierOnlyAllowed](kkeysequencerecorder-obsolete.md#setModifierOnlyAllowed)**(`bool` *allowed*)

**Notifier signal:**

- `void` **modifierOnlyAllowedChanged**()

### \[deprecated in 6.12\] modifierlessAllowed : bool {#modifierlessAllowed-prop}

This property is deprecated since 6.12. We strongly advise against using it in new code.

If key presses of "plain" keys without a modifier are considered to be a valid finished key combination. Plain keys include letter and symbol keys and text editing keys (Return, Space, Tab, Backspace, Delete). Other keys like F1, Cursor keys, Insert, PageDown will always work.

By default this is `false`.

Use the patterns property instead.

**Access functions:**

- `bool` **[modifierlessAllowed](kkeysequencerecorder-obsolete.md#modifierlessAllowed)**() const
- `void` **[setModifierlessAllowed](kkeysequencerecorder-obsolete.md#setModifierlessAllowed)**(`bool` *allowed*)

**Notifier signal:**

- `void` **modifierlessAllowedChanged**()

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[deprecated in 6.12\] bool KKeySequenceRecorder::modifierOnlyAllowed() const {#modifierOnlyAllowed}

This function is deprecated since 6.12. We strongly advise against using it in new code.

Use [patterns](kkeysequencerecorder.md#patterns-prop)() instead

> **Note:** Getter function for property [modifierOnlyAllowed](kkeysequencerecorder-obsolete.md#modifierOnlyAllowed-prop).

*See also* [setModifierOnlyAllowed](kkeysequencerecorder-obsolete.md#setModifierOnlyAllowed)()

### \[deprecated in 6.12\] bool KKeySequenceRecorder::modifierlessAllowed() const {#modifierlessAllowed}

This function is deprecated since 6.12. We strongly advise against using it in new code.

Use [patterns](kkeysequencerecorder.md#patterns-prop)() instead

> **Note:** Getter function for property [modifierlessAllowed](kkeysequencerecorder-obsolete.md#modifierlessAllowed-prop).

*See also* [setModifierlessAllowed](kkeysequencerecorder-obsolete.md#setModifierlessAllowed)()

### \[deprecated in 6.12\] void KKeySequenceRecorder::setModifierOnlyAllowed(bool *allowed*) {#setModifierOnlyAllowed}

This function is deprecated since 6.12. We strongly advise against using it in new code.

Use [setPatterns](kkeysequencerecorder.md#patterns-prop)() instead

> **Note:** Setter function for property [modifierOnlyAllowed](kkeysequencerecorder-obsolete.md#modifierOnlyAllowed-prop).

*See also* [modifierOnlyAllowed](kkeysequencerecorder-obsolete.md#modifierOnlyAllowed)()

### \[deprecated in 6.12\] void KKeySequenceRecorder::setModifierlessAllowed(bool *allowed*) {#setModifierlessAllowed}

This function is deprecated since 6.12. We strongly advise against using it in new code.

Use [setPatterns](kkeysequencerecorder.md#patterns-prop)() instead

> **Note:** Setter function for property [modifierlessAllowed](kkeysequencerecorder-obsolete.md#modifierlessAllowed-prop).

*See also* [modifierlessAllowed](kkeysequencerecorder-obsolete.md#modifierlessAllowed)()
