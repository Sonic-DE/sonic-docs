---
title: "KStandardShortcut::StandardShortcutWatcher Class"
description: "Persistent platform-independent application settings."
---

# KStandardShortcut::StandardShortcutWatcher Class

Persistent platform-independent application settings.

- **Header:** `#include <StandardShortcutWatcher>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigGui)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

## Signals

- [void shortcutChanged(KStandardShortcut::StandardShortcut id, const QList\<QKeySequence\> &shortcut)](#shortcutChanged)

## Detailed Description {#details}

Watches for changes made to standard shortcuts and notifies about those changes.

*See also* [KStandardShortcut::shortcutWatcher](kstandardshortcut-standardshortcutwatcher.md#shortcutWatcher)

## Member Function Documentation {#member-function-documentation}

### \[signal\] void StandardShortcutWatcher::shortcutChanged(KStandardShortcut::StandardShortcut *id*, const QList\<QKeySequence\> &*shortcut*) {#shortcutChanged}

The standardshortcut `id` was changed to `shortcut`

## Related Non-Members {#related-non-members}

### KStandardShortcut::StandardShortcutWatcher \*shortcutWatcher() {#shortcutWatcher}

Returns the global KStandardShortcutWatcher instance of this program. In addition to the notifying about changes it also keeps the information returned by the functions in [KStandardShortcut](kstandardshortcut.md) up to date. The object is created by the first call to this function.
