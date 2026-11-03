---
title: "KWindowStateSaver Class"
description: "Saves and restores a window size and (when possible) position."
---

# KWindowStateSaver Class

Saves and restores a window size and (when possible) position.

- **Header:** `#include <KWindowStateSaver>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigGui)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

## Public Functions

- [KWindowStateSaver(QWindow \*window, const KConfigGroup &configGroup)](#KWindowStateSaver)
- [KWindowStateSaver(QWindow \*window, const QString &configGroupName)](#KWindowStateSaver-1)
- [template \<typename Widget\> KWindowStateSaver(Widget \*widget, const KConfigGroup &configGroup)](#KWindowStateSaver-2)
- [template \<typename Widget\> KWindowStateSaver(Widget \*widget, const QString &configGroupName)](#KWindowStateSaver-3)

## Detailed Description {#details}

This is useful for retrofitting persisting window geometry on existing windows or dialogs, without having to modify those classes themselves, or having to inherit from them.

For this:

- Create a new instance of [KWindowStateSaver](kwindowstatesaver.md) for every window that should have its state persisted
- Pass it the window
- Pass it the config group the state should be stored in

The [KWindowStateSaver](kwindowstatesaver.md) will restore an existing state and then monitor the window for subsequent changes to persist. It will delete itself once the window is deleted.

```cpp
QPrintPreviewDialog previewDialog = ...
new KWindowStateSaver(&previewDialog, "printPreviewDialogState");
...
previewDialog.exec();
```

Note that freshly created top-level QWidgets (such as the dialog in the above example) do not have an associated [QWindow](https://doc.qt.io/qt-6/qwindow.html) yet (that is, windowHandle() returns `nullptr`). [KWindowStateSaver](kwindowstatesaver.md) monitors suchs widgets for any later-associated QWindows to allow for this use case.

When implementing your own windows/dialogs, using [KWindowConfig](kwindowconfig.md) directly can be an alternative.

*See also* [KWindowConfig](kwindowconfig.md)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KWindowStateSaver::KWindowStateSaver(QWindow \**window*, const KConfigGroup &*configGroup*) {#KWindowStateSaver}

Creates a new window state saver for the given `window` with the `configGroup` that holds the window state.

*See also* [KSharedConfig::openStateConfig](../kconfigcore/ksharedconfig.md#openStateConfig)

### \[explicit\] KWindowStateSaver::KWindowStateSaver(QWindow \**window*, const QString &*configGroupName*) {#KWindowStateSaver-1}

Creates a new window state saver for the given `window` with the `configGroupName` that holds the window state.

*See also* [KSharedConfig::openStateConfig](../kconfigcore/ksharedconfig.md#openStateConfig)

### \[explicit\] template \<typename Widget\> KWindowStateSaver::KWindowStateSaver(Widget \**widget*, const KConfigGroup &*configGroup*) {#KWindowStateSaver-2}

Creates a new window state saver for `widget` with the `configGroup` that holds the window state.

Use this for widgets that aren't shown yet and would still return `nullptr` from windowHandle().

### \[explicit\] template \<typename Widget\> KWindowStateSaver::KWindowStateSaver(Widget \**widget*, const QString &*configGroupName*) {#KWindowStateSaver-3}

Creates a new window state saver for `widget` with the `configGroupName` that holds the window state.

Use this for widgets that aren't shown yet and would still return `nullptr` from windowHandle().
