---
title: "Obsolete Members for KPasswordLineEdit"
description: "Deprecated members of KPasswordLineEdit."
parent: "kwidgetsaddons/kpasswordlineedit"
---

# Obsolete Members for KPasswordLineEdit

**The following members of class [KPasswordLineEdit](kpasswordlineedit.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [bool isRevealPasswordAvailable() const](#isRevealPasswordAvailable) (deprecated in 6.0)
- [void setRevealPasswordAvailable(bool reveal)](#setRevealPasswordAvailable) (deprecated in 6.0)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[deprecated in 6.0\] bool KPasswordLineEdit::isRevealPasswordAvailable() const {#isRevealPasswordAvailable}

This function is deprecated since 6.0. We strongly advise against using it in new code.

Whether the visibility trailing action in the line edit is visible.

### \[deprecated in 6.0\] void KPasswordLineEdit::setRevealPasswordAvailable(bool *reveal*) {#setRevealPasswordAvailable}

This function is deprecated since 6.0. We strongly advise against using it in new code.

Whether to show the visibility trailing action in the line edit. Default is true. This can be used to honor the lineedit\_reveal\_password kiosk key, for example:

```cpp
passwordLineEdit.setRevealPasswordAvailable(KAuthorized::authorize(QStringLiteral("lineedit_reveal_password")));
```

*See also* [isRevealPasswordAvailable](kpasswordlineedit-obsolete.md#isRevealPasswordAvailable)()
