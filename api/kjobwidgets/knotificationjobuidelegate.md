---
title: "KNotificationJobUiDelegate Class"
description: "A UI delegate using KNotification for interaction (showing errors and warnings). This class was introduced in Qt 6.0."
---

# KNotificationJobUiDelegate Class

A UI delegate using KNotification for interaction (showing errors and warnings). This class was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <KNotificationJobUiDelegate>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS JobWidgets)`  
  `target_link_libraries(mytarget PRIVATE KF6::JobWidgets)`
- **Inherits:** [KJobUiDelegate](../kcoreaddons/kjobuidelegate.md)

[List of all members, including inherited members](knotificationjobuidelegate-members.md)

## Public Functions

- [KNotificationJobUiDelegate(KJobUiDelegate::Flags flags = {KJobUiDelegate::AutoHandlingDisabled})](#KNotificationJobUiDelegate) (since 6.0)
- [void showErrorMessage()](#showErrorMessage)

## Detailed Description {#details}

## Member Function Documentation {#member-function-documentation}

### \[explicit, since 6.0\] KNotificationJobUiDelegate::KNotificationJobUiDelegate(KJobUiDelegate::Flags *flags* = {KJobUiDelegate::AutoHandlingDisabled}) {#KNotificationJobUiDelegate}

Constructs a new [KNotificationJobUiDelegate](knotificationjobuidelegate.md).

`flags` allows to enable automatic error/warning handling

This function was introduced in Qt 6.0.

### \[override virtual\] void KNotificationJobUiDelegate::showErrorMessage() {#showErrorMessage}

Reimplements: [KJobUiDelegate::showErrorMessage()](../kcoreaddons/kjobuidelegate.md#showErrorMessage).

Display a notification to inform the user of the error given by this job.
