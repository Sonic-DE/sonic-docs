---
title: "Obsolete Members for KSycoca"
description: "Deprecated members of KSycoca."
parent: "kservice/ksycoca"
---

# Obsolete Members for KSycoca

**The following members of class [KSycoca](ksycoca.md) are deprecated.** We strongly advise against using them in new code.

## Static Public Members

- [void setupTestMenu()](#setupTestMenu) (since 6.0) (deprecated in 6.29)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[static, since 6.0, deprecated in 6.29\] void KSycoca::setupTestMenu() {#setupTestMenu}

This function is deprecated since 6.29. We strongly advise against using it in new code.

Sets up a minimal applications.menu file in the appropriate location.

This is useful when writing unit tests that interact with [KService](kservice-module.md).

You should call [QStandardPaths::setTestModeEnabled](https://doc.qt.io/qt-6/qstandardpaths.html#setTestModeEnabled)(true) before calling this.

Unused

This function was introduced in Qt 6.0.
