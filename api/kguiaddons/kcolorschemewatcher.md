---
title: "KColorSchemeWatcher Class"
description: "Information about system-wide color preferences. Use QStyleHints and QAccessibilityHints instead. This class is deprecated since 6.22. We strongly advise against using it in new code."
---

# KColorSchemeWatcher Class

Information about system-wide color preferences. Use [QStyleHints](https://doc.qt.io/qt-6/qstylehints.html) and [QAccessibilityHints](https://doc.qt.io/qt-6/qaccessibilityhints.html) instead. **This class is deprecated since 6.22. We strongly advise against using it in new code.** [More...](#details)

- **Header:** `#include <KColorSchemeWatcher>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS GuiAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::GuiAddons)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)
- **Status:** Deprecated since 6.22

[List of all members, including inherited members](kcolorschemewatcher-members.md)

## Public Types

- [enum KColorSchemeWatcher::ColorPreference](#ColorPreference-enum)

## Public Functions

- [KColorSchemeWatcher(QObject \*parent = nullptr)](#KColorSchemeWatcher)
- [KColorSchemeWatcher::ColorPreference systemPreference() const](#systemPreference)

## Signals

- [void systemPreferenceChanged()](#systemPreferenceChanged)

**This class is deprecated since 6.22. We strongly advise against using it in new code.**

## Detailed Description {#details}

## Member Type Documentation {#member-type-documentation}

### enum KColorSchemeWatcher::ColorPreference {#ColorPreference-enum}

Encodes the color preference of the user to be used by applications as configured in the system settings. On some systems not all values are returned, e.g. PreferHighContrast is currently only returned on Windows.

| Constant | Value | Description |
| --- | --- | --- |
| `KColorSchemeWatcher::NoPreference` | `0` | No preference available |
| `KColorSchemeWatcher::PreferDark` | `1` | The user prefers a dark color scheme |
| `KColorSchemeWatcher::PreferLight` | `2` | The user prefers a light color scheme |
| `KColorSchemeWatcher::PreferHighContrast (since Qt 6.13)` | `3` | The user prefers a system-provided high-contrast color scheme |

*See also* [systemPreference](kcolorschemewatcher.md#systemPreference)

## Member Function Documentation {#member-function-documentation}

### KColorSchemeWatcher::KColorSchemeWatcher(QObject \**parent* = nullptr) {#KColorSchemeWatcher}

### KColorSchemeWatcher::ColorPreference KColorSchemeWatcher::systemPreference() const {#systemPreference}

The system-wide color preference.

### \[signal\] void KColorSchemeWatcher::systemPreferenceChanged() {#systemPreferenceChanged}

Emitted when [systemPreference](kcolorschemewatcher.md#systemPreference) changes.
