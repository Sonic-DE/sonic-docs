---
title: "Kirigami::Platform::VirtualKeyboardWatcher Class"
description: "This class reports on the status of KWin's VirtualKeyboard DBus interface."
---

# Kirigami::Platform::VirtualKeyboardWatcher Class

This class reports on the status of KWin's VirtualKeyboard DBus interface. [More...](#details)

- **Header:** `#include <Kirigami/Platform/VirtualKeyboardWatcher>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KirigamiPlatform)`  
  `target_link_libraries(mytarget PRIVATE KF6::KirigamiPlatform)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kirigami-platform-virtualkeyboardwatcher-members.md)

## Properties

- [\[read-only\] active : bool](#active-prop)
- [\[read-only\] available : bool](#available-prop)
- [\[read-only\] enabled : bool](#enabled-prop)
- [\[read-only\] visible : bool](#visible-prop)
- [\[read-only\] willShowOnActive : bool](#willShowOnActive-prop)

## Detailed Description {#details}

## Property Documentation {#property-documentation}

### \[read-only\] active : bool {#active-prop}

**Access functions:**

- `bool` **active**() const

**Notifier signal:**

- `void` **activeChanged**()

### \[read-only\] available : bool {#available-prop}

**Access functions:**

- `bool` **available**() const

**Notifier signal:**

- `void` **availableChanged**()

### \[read-only\] enabled : bool {#enabled-prop}

**Access functions:**

- `bool` **enabled**() const

**Notifier signal:**

- `void` **enabledChanged**()

### \[read-only\] visible : bool {#visible-prop}

**Access functions:**

- `bool` **visible**() const

**Notifier signal:**

- `void` **visibleChanged**()

### \[read-only\] willShowOnActive : bool {#willShowOnActive-prop}

**Access functions:**

- `bool` **willShowOnActive**() const

**Notifier signal:**

- `void` **willShowOnActiveChanged**()
