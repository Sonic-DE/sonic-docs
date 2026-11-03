---
title: "Obsolete Members for KNewPasswordWidget"
description: "Deprecated members of KNewPasswordWidget."
parent: "kwidgetsaddons/knewpasswordwidget"
---

# Obsolete Members for KNewPasswordWidget

**The following members of class [KNewPasswordWidget](knewpasswordwidget.md) are deprecated.** We strongly advise against using them in new code.

## Properties

- [\[deprecated in 6.0\] revealPasswordAvailable : bool](#revealPasswordAvailable-prop)

## Public Functions

- [bool isRevealPasswordAvailable() const](#isRevealPasswordAvailable) (deprecated in 6.0)

## Public Slots

- [void setRevealPasswordAvailable(bool reveal)](#setRevealPasswordAvailable) (deprecated in 6.0)

## Obsolete Property Documentation {#obsolete-property-documentation}

### \[deprecated in 6.0\] revealPasswordAvailable : bool {#revealPasswordAvailable-prop}

This property is deprecated since 6.0. We strongly advise against using it in new code.

**Access functions:**

- `bool` **[isRevealPasswordAvailable](knewpasswordwidget-obsolete.md#isRevealPasswordAvailable)**() const
- `void` **[setRevealPasswordAvailable](knewpasswordwidget-obsolete.md#setRevealPasswordAvailable)**(`bool` *reveal*)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[deprecated in 6.0\] bool KNewPasswordWidget::isRevealPasswordAvailable() const {#isRevealPasswordAvailable}

This function is deprecated since 6.0. We strongly advise against using it in new code.

Whether the visibility trailing action in the line edit is visible.

> **Note:** Getter function for property [revealPasswordAvailable](knewpasswordwidget-obsolete.md#revealPasswordAvailable-prop).

### \[slot, deprecated in 6.0\] void KNewPasswordWidget::setRevealPasswordAvailable(bool *reveal*) {#setRevealPasswordAvailable}

This function is deprecated since 6.0. We strongly advise against using it in new code.

Whether to show the visibility trailing action in the line edit. Default is true. This can be used to honor the lineedit\_reveal\_password kiosk key, for example:

```cpp
passwordWidget.setRevealPasswordAvailable(KAuthorized::authorize(QStringLiteral("lineedit_reveal_password")));
```

> **Note:** Setter function for property [revealPasswordAvailable](knewpasswordwidget-obsolete.md#revealPasswordAvailable-prop).

*See also* [isRevealPasswordAvailable](knewpasswordwidget-obsolete.md#isRevealPasswordAvailable)()
