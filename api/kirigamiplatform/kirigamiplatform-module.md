---
title: "Kirigami Platform C++ Classes"
description: "Platform Integration Components."
---

# Kirigami Platform C++ Classes

Platform Integration Components. [More...](#details)

## Namespaces {#namespaces}

- [Kirigami](kirigami.md)
- [Kirigami::Platform](kirigami-platform.md): Platform Integration Components.

## Classes {#classes}

- [Kirigami::Platform::PlatformPluginFactory](kirigami-platform-platformpluginfactory.md): This class is reimplemented by plugins to provide different implementations of PlatformTheme.
- [Kirigami::Platform::PlatformTheme](kirigami-platform-platformtheme.md): This class is the base for color management in Kirigami, different platforms can reimplement this class to integrate with system platform colors of a given platform.
- [Kirigami::Platform::PlatformThemeChangeTracker](kirigami-platform-platformthemechangetracker.md): A class that tracks changes to PlatformTheme properties and emits signals at the right moment.
- [Kirigami::Platform::StyleHints](kirigami-platform-stylehints.md): A class providing an attached property to set hints for styles to use.
- [Kirigami::Platform::TabletModeChangedEvent](kirigami-platform-tabletmodechangedevent.md): Event sent by TabletModeWatcher when the tablet mode changes.
- [Kirigami::Platform::TabletModeWatcher](kirigami-platform-tabletmodewatcher.md): This class reports on the status of certain transformable devices which can be both tablets and laptops at the same time, with a detachable keyboard.
- [Kirigami::Platform::Units](kirigami-platform-units.md): A set of values to define semantically sizes and durations.
- [Kirigami::Platform::VirtualKeyboardWatcher](kirigami-platform-virtualkeyboardwatcher.md): This class reports on the status of KWin's VirtualKeyboard DBus interface.

## Detailed Description {#details}
