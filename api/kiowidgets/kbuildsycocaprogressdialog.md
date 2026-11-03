---
title: "KBuildSycocaProgressDialog Class"
description: "Progress dialog while ksycoca is being rebuilt (by kbuildsycoca)."
---

# KBuildSycocaProgressDialog Class

Progress dialog while ksycoca is being rebuilt (by kbuildsycoca). [More...](#details)

- **Header:** `#include <KBuildSycocaProgressDialog>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [QProgressDialog](https://doc.qt.io/qt-6/qprogressdialog.html)

[List of all members, including inherited members](kbuildsycocaprogressdialog-members.md)

## Static Public Members

- [void rebuildKSycoca(QWidget \*parent)](#rebuildKSycoca)

## Detailed Description {#details}

Usage:

```cpp
KBuildSycocaProgressDialog::rebuildKSycoca(parentWidget);
```

## Member Function Documentation {#member-function-documentation}

### \[static\] void KBuildSycocaProgressDialog::rebuildKSycoca(QWidget \**parent*) {#rebuildKSycoca}

Rebuild KSycoca and show a progress dialog while doing so.

`parent` Parent widget for the progress dialog
