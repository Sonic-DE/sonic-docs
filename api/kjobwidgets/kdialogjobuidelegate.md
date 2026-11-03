---
title: "KDialogJobUiDelegate Class"
description: "A UI delegate using KMessageBox for interaction (showing errors and warnings)."
---

# KDialogJobUiDelegate Class

A UI delegate using KMessageBox for interaction (showing errors and warnings). [More...](#details)

- **Header:** `#include <KDialogJobUiDelegate>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS JobWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::JobWidgets)`
- **Inherits:** [KJobUiDelegate](../kcoreaddons/kjobuidelegate.md)

[List of all members, including inherited members](kdialogjobuidelegate-members.md)

## Public Functions

- [KDialogJobUiDelegate()](#KDialogJobUiDelegate)
- [KDialogJobUiDelegate(KJobUiDelegate::Flags flags, QWidget \*window)](#KDialogJobUiDelegate-1)
- [void setWindow(QWidget \*window)](#setWindow)
- [void updateUserTimestamp(unsigned long time)](#updateUserTimestamp)
- [QWidget \*window() const](#window)

## Detailed Description {#details}

The KMessageBox will use window as a parent in an application-modal.

## Member Function Documentation {#member-function-documentation}

### KDialogJobUiDelegate::KDialogJobUiDelegate() {#KDialogJobUiDelegate}

Constructs a new [KDialogJobUiDelegate](kdialogjobuidelegate.md).

### \[explicit\] KDialogJobUiDelegate::KDialogJobUiDelegate(KJobUiDelegate::Flags *flags*, QWidget \**window*) {#KDialogJobUiDelegate-1}

Constructs a new [KDialogJobUiDelegate](kdialogjobuidelegate.md).

`flags` allows to enable automatic error/warning handling

`window` the window associated with this delegate, see [setWindow](kdialogjobuidelegate.md#setWindow).

### \[virtual\] void KDialogJobUiDelegate::setWindow(QWidget \**window*) {#setWindow}

Associate this delegate with a window given by `window`.

Needed for dialog boxes to respect stacking order, centering to parent, focus going back to parent after closing...

`window` the window to associate to

*See also* [window](kdialogjobuidelegate.md#window)()

### void KDialogJobUiDelegate::updateUserTimestamp(unsigned long *time*) {#updateUserTimestamp}

Updates the last user action timestamp to the given time.

### QWidget \*KDialogJobUiDelegate::window() const {#window}

Returns the window this delegate is associated with.

*See also* [setWindow](kdialogjobuidelegate.md#setWindow)()
