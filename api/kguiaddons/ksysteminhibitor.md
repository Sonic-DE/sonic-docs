---
title: "KSystemInhibitor Class"
description: "Inhibit system actions such as logout, suspend, etc. This class was introduced in Qt 6.23."
---

# KSystemInhibitor Class

Inhibit system actions such as logout, suspend, etc. This class was introduced in Qt 6.23. [More...](#details)

- **Header:** `#include <KSystemInhibitor>`
- **Since:** Qt 6.23
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS GuiAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::GuiAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](ksysteminhibitor-members.md)

## Public Types

- [enum KSystemInhibitor::Type](#Type-enum)

## Public Functions

- [KSystemInhibitor(const QString &reason, KSystemInhibitor::Types types, QWindow \*window, QObject \*parent = nullptr)](#KSystemInhibitor)
- [~KSystemInhibitor()](#dtor.KSystemInhibitor)

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum KSystemInhibitor::Type {#Type-enum}

**flags KSystemInhibitor::Types**

Inhibition types.

| Constant | Value | Description |
| --- | --- | --- |
| `KSystemInhibitor::Type::Logout` | `1` | Inhibit logout/shutdown |
| `KSystemInhibitor::Type::UserSwitch` | `2` | Inhibit user switching |
| `KSystemInhibitor::Type::Suspend` | `4` | Inhibit suspend/hibernate |
| `KSystemInhibitor::Type::Idle` | `8` | Inhibit idle actions (e.g. screen locking) |

The `Types` type is a typedef for `QFlags<Type>. `It stores an OR combination of `Type` values.

## Member Function Documentation {#member-function-documentation}

### KSystemInhibitor::KSystemInhibitor(const QString &*reason*, KSystemInhibitor::Types *types*, QWindow \**window*, QObject \**parent* = nullptr) {#KSystemInhibitor}

Claim inhibition.

`reason` is the user-visible reason for the inhibition.

`types` is a combination of inhibition types.

`window` is the window for which to apply the inhibition. May be null in which case possible user queries will not be associated with any window.

`parent` is the parent [QObject](https://doc.qt.io/qt-6/qobject.html).

### \[override virtual noexcept\] KSystemInhibitor::~KSystemInhibitor() {#dtor.KSystemInhibitor}

Release inhibition
