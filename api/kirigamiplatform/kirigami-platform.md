---
title: "Kirigami::Platform Namespace"
description: "Platform Integration Components."
---

# Kirigami::Platform Namespace

Platform Integration Components. [More...](#details)

- **Header:** `#include <Platform>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KirigamiPlatform)`  
  `target_link_libraries(mytarget PRIVATE KF6::KirigamiPlatform)`

## Detailed Description {#details}

## Classes {#classes}

### class [PlatformPluginFactory](kirigami-platform-platformpluginfactory.md)

This class is reimplemented by plugins to provide different implementations of [PlatformTheme](kirigami-platform-platformtheme.md).

### class [PlatformTheme](kirigami-platform-platformtheme.md)

This class is the base for color management in Kirigami, different platforms can reimplement this class to integrate with system platform colors of a given platform.

### class [PlatformThemeChangeTracker](kirigami-platform-platformthemechangetracker.md)

A class that tracks changes to [PlatformTheme](kirigami-platform-platformtheme.md) properties and emits signals at the right moment.

### class [StyleHints](kirigami-platform-stylehints.md)

A class providing an attached property to set hints for styles to use.

### class [TabletModeChangedEvent](kirigami-platform-tabletmodechangedevent.md)

Event sent by [TabletModeWatcher](kirigami-platform-tabletmodewatcher.md) when the tablet mode changes.

### class [TabletModeWatcher](kirigami-platform-tabletmodewatcher.md)

This class reports on the status of certain transformable devices which can be both tablets and laptops at the same time, with a detachable keyboard.

### class [Units](kirigami-platform-units.md)

A set of values to define semantically sizes and durations.

### class [VirtualKeyboardWatcher](kirigami-platform-virtualkeyboardwatcher.md)

This class reports on the status of KWin's VirtualKeyboard DBus interface.
