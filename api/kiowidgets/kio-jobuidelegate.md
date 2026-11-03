---
title: "KIO::JobUiDelegate Class"
description: "productname."
---

# KIO::JobUiDelegate Class

productname. [More...](#details)

- **Header:** `#include <KIO/JobUiDelegate>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOWidgets)`
- **Inherits:** [KDialogJobUiDelegate](../kjobwidgets/kdialogjobuidelegate.md) and [KIO::JobUiDelegateExtension](../kiocore/kio-jobuidelegateextension.md)

[List of all members, including inherited members](kio-jobuidelegate-members.md)

## Public Functions

- [KIO::ClipboardUpdater \*createClipboardUpdater(KIO::Job \*job, KIO::JobUiDelegateExtension::ClipboardUpdaterMode mode)](#createClipboardUpdater)
- [void setWindow(QWidget \*window)](#setWindow)
- [void updateUrlInClipboard(const QUrl &src, const QUrl &dest)](#updateUrlInClipboard)

## Static Public Members

- [void unregisterWindow(QWidget \*window)](#unregisterWindow)

## Protected Functions

- [JobUiDelegate(KJobUiDelegate::Flags flags = AutoHandlingDisabled, QWidget \*window = nullptr, const QList\<QObject \*\> &ifaces = {})](#JobUiDelegate)

## Detailed Description {#details}

A UI delegate tuned to be used with KIO Jobs.

## Member Function Documentation {#member-function-documentation}

### \[explicit protected\] JobUiDelegate::JobUiDelegate(KJobUiDelegate::Flags *flags* = AutoHandlingDisabled, QWidget \**window* = nullptr, const QList\<QObject \*\> &*ifaces* = {}) {#JobUiDelegate}

Constructs a new KIO Job UI delegate.

`flags` allows to enable automatic error/warning handling

`window` the window associated with this delegate, see [setWindow](kio-jobuidelegate.md#setWindow).

`ifaces` Interface instances such as OpenWithHandlerInterface to replace the default interfaces

### \[override virtual\] KIO::ClipboardUpdater \*JobUiDelegate::createClipboardUpdater(KIO::Job \**job*, KIO::JobUiDelegateExtension::ClipboardUpdaterMode *mode*) {#createClipboardUpdater}

Reimplements: [JobUiDelegateExtension::createClipboardUpdater(KIO::Job \*job, KIO::JobUiDelegateExtension::ClipboardUpdaterMode mode)](../kiocore/kio-jobuidelegateextension.md#createClipboardUpdater).

Creates a clipboard updater

### \[override virtual\] void JobUiDelegate::setWindow(QWidget \**window*) {#setWindow}

Reimplements: [KDialogJobUiDelegate::setWindow(QWidget \*window)](../kjobwidgets/kdialogjobuidelegate.md#setWindow).

Associate this job with a window given by `window`.

`window` the window to associate to

*See also* [window](../kjobwidgets/kdialogjobuidelegate.md#window)()

### \[static\] void JobUiDelegate::unregisterWindow(QWidget \**window*) {#unregisterWindow}

Unregister the given window from kded. This is normally done automatically when the window is destroyed.

This method is useful for instance when keeping a hidden window around to make it faster to reuse later.

### \[override virtual\] void JobUiDelegate::updateUrlInClipboard(const QUrl &*src*, const QUrl &*dest*) {#updateUrlInClipboard}

Reimplements: [JobUiDelegateExtension::updateUrlInClipboard(const QUrl &src, const QUrl &dest)](../kiocore/kio-jobuidelegateextension.md#updateUrlInClipboard).

Update URL in clipboard, if present
