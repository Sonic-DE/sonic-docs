---
title: "Obsolete Members for KKeySequenceWidget"
description: "Deprecated members of KKeySequenceWidget."
parent: "kxmlgui/kkeysequencewidget"
---

# Obsolete Members for KKeySequenceWidget

**The following members of class [KKeySequenceWidget](kkeysequencewidget.md) are deprecated.** We strongly advise against using them in new code.

## Properties

- [\[deprecated in 6.12\] modifierlessAllowed : bool](#modifierlessAllowed-prop)

## Public Functions

- [bool isModifierlessAllowed()](#isModifierlessAllowed) (deprecated in 6.12)
- [bool modifierOnlyAllowed() const](#modifierOnlyAllowed) (deprecated in 6.12)
- [void setModifierOnlyAllowed(bool allow)](#setModifierOnlyAllowed) (since 6.1) (deprecated in 6.12)
- [void setModifierlessAllowed(bool allow)](#setModifierlessAllowed) (deprecated in 6.12)

## Obsolete Property Documentation {#obsolete-property-documentation}

### \[deprecated in 6.12\] modifierlessAllowed : bool {#modifierlessAllowed-prop}

This property is deprecated since 6.12. We strongly advise against using it in new code.

Use the patterns property

**Access functions:**

- `bool` **[isModifierlessAllowed](kkeysequencewidget-obsolete.md#isModifierlessAllowed)**()
- `void` **[setModifierlessAllowed](kkeysequencewidget-obsolete.md#setModifierlessAllowed)**(`bool` *allow*)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[deprecated in 6.12\] bool KKeySequenceWidget::isModifierlessAllowed() {#isModifierlessAllowed}

This function is deprecated since 6.12. We strongly advise against using it in new code.

Use [patterns](kkeysequencewidget.md#patterns)() instead

Returns whether "plain" keys without modifiers (like Ctrl, Alt, Meta) are allowed.

> **Note:** Getter function for property [modifierlessAllowed](kkeysequencewidget-obsolete.md#modifierlessAllowed-prop).

*See also* [setModifierlessAllowed](kkeysequencewidget-obsolete.md#setModifierlessAllowed)(), [setModifierlessAllowed](kkeysequencewidget-obsolete.md#setModifierlessAllowed)()

### \[deprecated in 6.12\] bool KKeySequenceWidget::modifierOnlyAllowed() const {#modifierOnlyAllowed}

This function is deprecated since 6.12. We strongly advise against using it in new code.

Use [patterns](kkeysequencewidget.md#patterns)() instead

*See also* [setModifierOnlyAllowed](kkeysequencewidget-obsolete.md#setModifierOnlyAllowed)()

### \[since 6.1, deprecated in 6.12\] void KKeySequenceWidget::setModifierOnlyAllowed(bool *allow*) {#setModifierOnlyAllowed}

This function is deprecated since 6.12. We strongly advise against using it in new code.

Whether to allow modifier-only key sequences. Use [setPatterns](kkeysequencewidget.md#setPatterns)() instead

This function was introduced in Qt 6.1.

*See also* [modifierOnlyAllowed](kkeysequencewidget-obsolete.md#modifierOnlyAllowed)()

### \[deprecated in 6.12\] void KKeySequenceWidget::setModifierlessAllowed(bool *allow*) {#setModifierlessAllowed}

This function is deprecated since 6.12. We strongly advise against using it in new code.

Sets whether to `allow` "plain" keys without modifiers (like Ctrl, Alt, Meta).

This only applies to user input, not to [setKeySequence](kkeysequencewidget.md#setKeySequence)().

Plain keys by our definition include letter and symbol keys and text editing keys (Return, Space, Tab, Backspace, Delete).

"Special" keys like F1, Cursor keys, Insert, PageDown will always work.

Use [setPatterns](kkeysequencewidget.md#setPatterns)() instead

> **Note:** Setter function for property [modifierlessAllowed](kkeysequencewidget-obsolete.md#modifierlessAllowed-prop).

*See also* [isModifierlessAllowed](kkeysequencewidget-obsolete.md#isModifierlessAllowed)()
