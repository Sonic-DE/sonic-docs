---
title: "Kirigami::Platform::PlatformThemeChangeTracker Class"
description: "A class that tracks changes to PlatformTheme properties and emits signals at the right moment. This class was introduced in Qt 6.7."
---

# Kirigami::Platform::PlatformThemeChangeTracker Class

A class that tracks changes to [PlatformTheme](kirigami-platform-platformtheme.md) properties and emits signals at the right moment. This class was introduced in Qt 6.7. [More...](#details)

- **Header:** `#include <Kirigami/Platform/PlatformTheme>`
- **Since:** Qt 6.7
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KirigamiPlatform)`  
  `target_link_libraries(mytarget PRIVATE KF6::KirigamiPlatform)`

[List of all members, including inherited members](kirigami-platform-platformthemechangetracker-members.md)

## Public Types

- [enum PlatformThemeChangeTracker::PropertyChange](#PropertyChange-enum)

## Detailed Description {#details}

This should be used by [PlatformTheme](kirigami-platform-platformtheme.md) implementations to ensure that multiple changes to a [PlatformTheme](kirigami-platform-platformtheme.md)'s properties do not emit multiple change signals, instead batching all of them into a single signal emission. This then ensures things making use of [PlatformTheme](kirigami-platform-platformtheme.md) aren't needlessly redrawn or redrawn in a partially changed state.

## Member Type Documentation {#member-type-documentation}

### enum PlatformThemeChangeTracker::PropertyChange {#PropertyChange-enum}

**flags PlatformThemeChangeTracker::PropertyChanges**

Flags used to indicate changes made to certain properties.

| Constant |   |
| --- | --- |
| `Kirigami::Platform::PlatformThemeChangeTracker::PropertyChange::None` | `0` |
| `Kirigami::Platform::PlatformThemeChangeTracker::PropertyChange::ColorSet` | `1 << 0` |
| `Kirigami::Platform::PlatformThemeChangeTracker::PropertyChange::ColorGroup` | `1 << 1` |
| `Kirigami::Platform::PlatformThemeChangeTracker::PropertyChange::Color` | `1 << 2` |
| `Kirigami::Platform::PlatformThemeChangeTracker::PropertyChange::Palette` | `1 << 3` |
| `Kirigami::Platform::PlatformThemeChangeTracker::PropertyChange::Font` | `1 << 4` |
| `Kirigami::Platform::PlatformThemeChangeTracker::PropertyChange::Data` | `1 << 5` |
| `Kirigami::Platform::PlatformThemeChangeTracker::PropertyChange::FrameContrast` | `1 << 6` |
| `Kirigami::Platform::PlatformThemeChangeTracker::PropertyChange::All` | `ColorSet | ColorGroup | Color | Palette | Font | Data | FrameContrast` |

The `PropertyChanges` type is a typedef for `QFlags<PropertyChange>. `It stores an OR combination of `PropertyChange` values.
