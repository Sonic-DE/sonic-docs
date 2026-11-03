---
title: "KNotificationPermission Namespace"
description: "Check or request permissions to show notifications on platforms where that is necessary. This namespace was introduced in Qt 6.0."
---

# KNotificationPermission Namespace

Check or request permissions to show notifications on platforms where that is necessary. This namespace was introduced in Qt 6.0. [More...](#details)

- Header: KNotificationPermission
- Since: Qt 6.0
- CMake: find\_package(KF6 REQUIRED COMPONENTS Notifications) target\_link\_libraries(mytarget PRIVATE KF6::Notifications)

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### Qt::PermissionStatus KNotificationPermission::checkPermission() {#checkPermission}

Check if the current application has permissions to show notifications.

### void KNotificationPermission::requestPermission(QObject \**context*, const std::function\<void (Qt::PermissionStatus)\> &*callback*) {#requestPermission}

Request notification permissions.
