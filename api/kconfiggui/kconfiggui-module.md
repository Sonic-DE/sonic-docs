---
title: "KConfigGui C++ Classes"
description: "Persistent platform-independent application settings."
---

# KConfigGui C++ Classes

Persistent platform-independent application settings.

## Namespaces {#namespaces}

- [KConfigGui](kconfiggui.md): Interface-related functions.
- [KStandardActions](kstandardactions.md): Convenience methods to access all standard KDE actions.
- [KStandardShortcut](kstandardshortcut.md): Convenient methods for access to the common accelerator keys in the key configuration.
- [KWindowConfig](kwindowconfig.md): Save and load window sizes into a config.

## Classes {#classes}

- [KConfigLoader](kconfigloader.md): A KConfigSkeleton that populates itself based on KConfigXT XML.
- [KConfigSkeleton](kconfigskeleton.md): Class for handling preferences settings for an application.
- [KConfigSkeleton::ItemColor](kconfigskeleton-itemcolor.md): Class for handling a color preferences item.
- [KConfigSkeleton::ItemFont](kconfigskeleton-itemfont.md): Class for handling a font preferences item.
- [KStandardShortcut::StandardShortcutWatcher](kstandardshortcut-standardshortcutwatcher.md)
- [KWindowStateSaver](kwindowstatesaver.md): Saves and restores a window size and (when possible) position.

## Detailed Description {#details}

[KConfigGui](kconfiggui-module.md) provides a way to hook widgets to the configuration so that they are automatically initialized from the configuration and automatically propagate their changes to their respective configuration files.
