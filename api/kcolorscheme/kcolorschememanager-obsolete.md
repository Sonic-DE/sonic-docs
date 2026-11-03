---
title: "Obsolete Members for KColorSchemeManager"
description: "Deprecated members of KColorSchemeManager."
parent: "kcolorscheme/kcolorschememanager"
---

# Obsolete Members for KColorSchemeManager

**The following members of class [KColorSchemeManager](kcolorschememanager.md) are deprecated.** We strongly advise against using them in new code.

## Public Functions

- [void saveSchemeToConfigFile(const QString &schemeName) const](#saveSchemeToConfigFile) (deprecated in 6.19)

## Obsolete Member Function Documentation {#obsolete-member-function-documentation}

### \[deprecated in 6.19\] void KColorSchemeManager::saveSchemeToConfigFile(const QString &*schemeName*) const {#saveSchemeToConfigFile}

This function is deprecated since 6.19. We strongly advise against using it in new code.

Saves the color scheme to config file. The scheme is saved by default whenever it's changed. Use this method when autosaving is turned off, see [setAutosaveChanges](kcolorschememanager.md#setAutosaveChanges)().

Use [saveSchemeIdToConfigFile](kcolorschememanager.md#saveSchemeIdToConfigFile)() instead which is not locale dependent
