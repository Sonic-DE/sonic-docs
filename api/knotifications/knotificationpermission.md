---
title: "KNotificationPermission Namespace"
description: "Check or request permissions to show notifications on platforms where that is necessary. This namespace was introduced in Qt 6.0."
---

# KNotificationPermission Namespace

Check or request permissions to show notifications on platforms where that is necessary. This namespace was introduced in Qt 6.0. [More...](#details)

- **Header:** `#include <KNotificationPermission>`
- **Since:** Qt 6.0
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Notifications)`  
  `target_link_libraries(mytarget PRIVATE KF6::Notifications)`

## Detailed Description {#details}

## Function Documentation {#function-documentation}

### Qt::PermissionStatus KNotificationPermission::checkPermission() {#checkPermission}

Check if the current application has permissions to show notifications.

### void KNotificationPermission::requestPermission(QObject \**context*, const std::function\<void (Qt::PermissionStatus)\> &*callback*) {#requestPermission}

Request notification permissions.
