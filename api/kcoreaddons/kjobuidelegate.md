---
title: "KJobUiDelegate Class"
description: "The base class for all KJob UI delegate."
---

# KJobUiDelegate Class

The base class for all [KJob](kjob.md) UI delegate. [More...](#details)

- **Header:** `#include <KJobUiDelegate>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kjobuidelegate-members.md)

## Public Types

- [enum KJobUiDelegate::Flag](#Flag-enum)

## Public Functions

- [KJobUiDelegate(KJobUiDelegate::Flags flags = {KJobUiDelegate::AutoHandlingDisabled})](#KJobUiDelegate)
- [bool isAutoErrorHandlingEnabled() const](#isAutoErrorHandlingEnabled)
- [bool isAutoWarningHandlingEnabled() const](#isAutoWarningHandlingEnabled)
- [void setAutoErrorHandlingEnabled(bool enable)](#setAutoErrorHandlingEnabled)
- [void setAutoWarningHandlingEnabled(bool enable)](#setAutoWarningHandlingEnabled)
- [void showErrorMessage()](#showErrorMessage)

## Public Slots

- [void slotWarning(KJob \*job, const QString &message)](#slotWarning)

## Protected Functions

- [KJob \*job() const](#job)
- [bool setJob(KJob \*job)](#setJob)

## Detailed Description {#details}

A UI delegate is responsible for the events of a job and provides a UI for them (an error message box or warning etc.).

*See also* [KJob](kjob.md)

## Member Type Documentation {#member-type-documentation}

### enum KJobUiDelegate::Flag {#Flag-enum}

**flags KJobUiDelegate::Flags**

Flags for the constructor, to enable automatic handling of errors and/or warnings

| Constant | Value | Description |
| --- | --- | --- |
| `KJobUiDelegate::AutoHandlingDisabled` | `0` | No automatic handling (default) |
| `KJobUiDelegate::AutoErrorHandlingEnabled` | `1` | Equivalent to [setAutoErrorHandlingEnabled](kjobuidelegate.md#setAutoErrorHandlingEnabled)(true) |
| `KJobUiDelegate::AutoWarningHandlingEnabled` | `2` | Equivalent to [setAutoWarningHandlingEnabled](kjobuidelegate.md#setAutoWarningHandlingEnabled)(true) |
| `KJobUiDelegate::AutoHandlingEnabled` | `AutoErrorHandlingEnabled | AutoWarningHandlingEnabled` | Enables both error and warning handling |

The `Flags` type is a typedef for `QFlags<Flag>. `It stores an OR combination of `Flag` values.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KJobUiDelegate::KJobUiDelegate(KJobUiDelegate::Flags *flags* = {KJobUiDelegate::AutoHandlingDisabled}) {#KJobUiDelegate}

Constructs a new [KJobUiDelegate](kjobuidelegate.md) with a flags argument.

`flags` allows to enable automatic error/warning handling

### bool KJobUiDelegate::isAutoErrorHandlingEnabled() const {#isAutoErrorHandlingEnabled}

Returns whether automatic error handling is enabled or disabled.

*See also* [setAutoErrorHandlingEnabled](kjobuidelegate.md#setAutoErrorHandlingEnabled)()

### bool KJobUiDelegate::isAutoWarningHandlingEnabled() const {#isAutoWarningHandlingEnabled}

Returns whether automatic warning handling is enabled or disabled.

*See also* [setAutoWarningHandlingEnabled](kjobuidelegate.md#setAutoWarningHandlingEnabled)()

### \[protected\] KJob \*KJobUiDelegate::job() const {#job}

Retrieves the current job this UI delegate is attached to.

Returns the current job this UI delegate is attached to, or `nullptr` if this UI delegate is not tracking any job

*See also* [setJob](kjobuidelegate.md#setJob)()

### void KJobUiDelegate::setAutoErrorHandlingEnabled(bool *enable*) {#setAutoErrorHandlingEnabled}

Enable or disable the automatic error handling. When automatic error handling is enabled and an error occurs, then showErrorDialog() is called, right before the emission of the result signal.

The default is `false`.

`enable` enable or disable automatic error handling

*See also* [isAutoErrorHandlingEnabled](kjobuidelegate.md#isAutoErrorHandlingEnabled)()

### void KJobUiDelegate::setAutoWarningHandlingEnabled(bool *enable*) {#setAutoWarningHandlingEnabled}

Enable or disable the automatic warning handling. When automatic warning handling is enabled and an error occurs, then a message box is displayed with the warning message

The default is `true`.

`enable` enable or disable automatic warning handling

*See also* [isAutoWarningHandlingEnabled](kjobuidelegate.md#isAutoWarningHandlingEnabled)()

### \[virtual protected\] bool KJobUiDelegate::setJob(KJob \**job*) {#setJob}

Attach this UI delegate to a job. Once attached it'll track the job events.

Returns `true` if this UI delegate was successfully attached to `job`, `false` otherwise

> **Note:** if this UI delegate is already attached to a job, calling this method will return `false`.

*See also* [job](kjobuidelegate.md#job)()

### \[virtual\] void KJobUiDelegate::showErrorMessage() {#showErrorMessage}

Display to the user the error given by this job. The default implementation uses [qWarning](https://doc.qt.io/qt-6/qdebug.html#qWarning)(). Subclasses reimplement this to use something more user-visible such as a message box.

Only call this method if error is not 0, and only in the slot connected to result.

### \[virtual protected slot\] void KJobUiDelegate::slotWarning(KJob \**job*, const QString &*message*) {#slotWarning}
