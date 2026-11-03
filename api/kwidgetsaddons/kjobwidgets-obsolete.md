---
title: "Obsolete Members for KJobWidgets"
description: "Deprecated members of KJobWidgets Namespace."
parent: "kwidgetsaddons/kjobwidgets"
---

# Obsolete Members for KJobWidgets

**The following members of class [KJobWidgets](kjobwidgets.md) are deprecated.** We strongly advise against using them in new code.

## Obsolete Function Documentation {#obsolete-function-documentation}

### \[since 6.4, deprecated in 6.5\] void KJobWidgets::setWindowHandle(QObject \**job*, QWindow \**window*) {#setWindowHandle}

This function is deprecated since 6.5. We strongly advise against using it in new code.

Associate this job with a window given by `window`.

Note that [setWindow](kjobwidgets.md#setWindow)() will set the window handle too.

`job` should be a KJob subclass

use KJobWindows::setWindow() instead.

This function was introduced in Qt 6.4.

*See also* [windowHandle](kjobwidgets.md#windowHandle)()
