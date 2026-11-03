---
title: "Obsolete Members for KNewPasswordDialog"
description: "Deprecated members of KNewPasswordDialog."
parent: "kwidgetsaddons/knewpassworddialog"
---

# Obsolete Members for KNewPasswordDialog

**The following members of class [KNewPasswordDialog](knewpassworddialog.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [bool isRevealPasswordAvailable() const](#isRevealPasswordAvailable) (deprecated in 6.0)
- [void setRevealPasswordAvailable(bool reveal)](#setRevealPasswordAvailable) (deprecated in 6.0)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[deprecated in 6.0\] bool KNewPasswordDialog::isRevealPasswordAvailable() const {#isRevealPasswordAvailable}

This function is deprecated since 6.0. We strongly advise against using it in new code.

Whether the visibility trailing action in the line edit is visible.

### \[deprecated in 6.0\] void KNewPasswordDialog::setRevealPasswordAvailable(bool *reveal*) {#setRevealPasswordAvailable}

This function is deprecated since 6.0. We strongly advise against using it in new code.

Whether to show the visibility trailing action in the line edit. Default is true. This can be used to honor the lineedit\_reveal\_password kiosk key, for example:

```cpp
passwordDialog.setRevealPasswordAvailable(KAuthorized::authorize(QStringLiteral("lineedit_reveal_password")));
```

*See also* [isRevealPasswordAvailable](knewpassworddialog-obsolete.md#isRevealPasswordAvailable)()
