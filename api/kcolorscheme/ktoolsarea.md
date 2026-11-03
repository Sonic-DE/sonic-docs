---
title: "KToolsArea Class"
description: "The window's tools area: the titlebar and the toolbars and main menu bar under it, drawn as one surface."
---

# KToolsArea Class

The window's tools area: the titlebar and the toolbars and main menu bar under it, drawn as one surface. [More...](#details)

- **Header:** `#include <KToolsArea>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS ColorScheme)`  
  `target_link_libraries(mytarget PRIVATE KF6::ColorScheme)`

[List of all members, including inherited members](ktoolsarea-members.md)

## Static Public Members

- [KToolsArea::Colors colors(const KSharedConfigPtr &scheme, const KToolsArea::Settings &settings)](#colors)
- [QList\<KToolsArea::Exception\> exceptions(const KSharedConfigPtr &scheme)](#exceptions)
- [bool migrateFromSilver(const KSharedConfigPtr &scheme)](#migrateFromSilver)
- [KToolsArea::Settings settings(const KSharedConfigPtr &scheme, const QString &name = QString())](#settings)
- [QString snapshot(const KSharedConfigPtr &scheme)](#snapshot)
- [void writeExceptions(const KSharedConfigPtr &scheme, const QList\<KToolsArea::Exception\> &exceptions)](#writeExceptions)
- [void writeSettings(const KSharedConfigPtr &scheme, const KToolsArea::Settings &settings)](#writeSettings)

## Detailed Description {#details}

The settings are theme-independent and live in the colour scheme config (kdeglobals, or an application's own scheme) as the \[ToolsArea\] group: `Enabled`, `ActiveOpacity`, `InactiveOpacity`, `ApplyOpacityToHeader`, `MatchApplicationColor`, `BlurBehind`, `OpaqueWhenMaximized`, `SeparatorColor`, `HideTitleBar`. Exceptions for chosen applications are the \[ToolsArea\]\[Application \<n\>\] groups (`Pattern`, a regular expression on the application name or window class, `Enabled`, and any of the keys above), after the built-in default exceptions, which can only be switched off (\[ToolsArea\]\[Default Application \<n\>\] `Enabled=false`).

Every reader (window decorations, widget styles, the Qt platform theme, settings pages) uses this class, so they agree. Writers send `KGlobalSettings.notifyChange` themselves afterwards; readers update on it.

## Member Function Documentation {#member-function-documentation}

### \[static\] KToolsArea::Colors KToolsArea::colors(const KSharedConfigPtr &*scheme*, const KToolsArea::Settings &*settings*) {#colors}

The tools area colours for `settings` with the colour scheme `scheme`.

### \[static\] QList\<KToolsArea::Exception\> KToolsArea::exceptions(const KSharedConfigPtr &*scheme*) {#exceptions}

The exceptions, the built-in default ones first.

### \[static\] bool KToolsArea::migrateFromSilver(const KSharedConfigPtr &*scheme*) {#migrateFromSilver}

Once: when \[ToolsArea\] has no Enabled key yet, moves the Silver theme's earlier titlebar transparency settings and exceptions from silver/silverrc here and deletes them there. Returns whether it did.

### \[static\] KToolsArea::Settings KToolsArea::settings(const KSharedConfigPtr &*scheme*, const QString &*name* = QString()) {#settings}

The settings for the application or window class `name` (an empty name: no exceptions).

### \[static\] QString KToolsArea::snapshot(const KSharedConfigPtr &*scheme*) {#snapshot}

Every \[ToolsArea\] entry as text, to tell whether anything changed.

### \[static\] void KToolsArea::writeExceptions(const KSharedConfigPtr &*scheme*, const QList\<KToolsArea::Exception\> &*exceptions*) {#writeExceptions}

Replaces the exceptions with `exceptions` (default ones: only their Enabled).

### \[static\] void KToolsArea::writeSettings(const KSharedConfigPtr &*scheme*, const KToolsArea::Settings &*settings*) {#writeSettings}

Writes `settings` as the \[ToolsArea\] keys (with Enabled=true).
