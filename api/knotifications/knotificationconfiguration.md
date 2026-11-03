---
title: "KNotificationConfiguration Class"
description: "Configure notifications using the means of the platform. This class was introduced in Qt 6.29."
---

# KNotificationConfiguration Class

Configure notifications using the means of the platform. This class was introduced in Qt 6.29. [More...](#details)

- **Header:** `#include <KNotificationConfiguration>`
- **Since:** Qt 6.29
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Notifications)`  
  `target_link_libraries(mytarget PRIVATE KF6::Notifications)`

[List of all members, including inherited members](knotificationconfiguration-members.md)

## Properties

- [\[read-only\] isAvailable : bool](#isAvailable-prop)

## Static Public Members

- [bool isAvailable()](#isAvailable)
- [void show()](#show)

## Detailed Description {#details}

This provides ways to interact with platform-specific means of configuring notifications of the current application.

This is particularly relevant for sandboxed applications (Flatpak, APK, etc) where the host platform ultimately decides if/how notifications are shown.

This requires an installed `.notifyrc` file matching the application name to work, a `.notifyrc` file bundled as Qt resource will only work on Android.

## Property Documentation {#property-documentation}

### \[read-only\] isAvailable : bool {#isAvailable-prop}

**Access functions:**

- `bool` **[isAvailable](knotificationconfiguration.md#isAvailable)**()

## Member Function Documentation {#member-function-documentation}

### \[static\] bool KNotificationConfiguration::isAvailable() {#isAvailable}

Returns `true` if notifications can be configured on the current platform.

> **Note:** Getter function for property [isAvailable](knotificationconfiguration.md#isAvailable-prop).

### \[static invokable\] void KNotificationConfiguration::show() {#show}

Opens a platform-specific UI for configuring the notifications of the current application.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.
