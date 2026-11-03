---
title: "KIconTheme Class"
description: "Class to use/access icon themes in KDE."
---

# KIconTheme Class

Class to use/access icon themes in KDE. [More...](#details)

- **Header:** `#include <KIconTheme>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS IconThemes)`  
  `target_link_libraries(mytarget PRIVATE KF6::IconThemes)`

[List of all members, including inherited members](kicontheme-members.md)

## Public Functions

- [KIconTheme(const QString &name, const QString &appName = QString(), const QString &basePathHint = QString())](#KIconTheme)
- [int defaultSize(KIconLoader::Group group) const](#defaultSize)
- [int depth() const](#depth)
- [QString description() const](#description)
- [QString dir() const](#dir)
- [QString example() const](#example)
- [bool followsColorScheme() const](#followsColorScheme)
- [bool hasContext(KIconLoader::Context context) const](#hasContext)
- [QString iconPath(const QString &name, int size, KIconLoader::MatchType match) const](#iconPath)
- [QString iconPath(const QString &name, int size, KIconLoader::MatchType match, qreal scale) const](#iconPath-1)
- [QString iconPathByName(const QString &name, int size, KIconLoader::MatchType match) const](#iconPathByName)
- [QString iconPathByName(const QString &name, int size, KIconLoader::MatchType match, qreal scale) const](#iconPathByName-1)
- [QStringList inherits() const](#inherits)
- [QString internalName() const](#internalName)
- [bool isHidden() const](#isHidden)
- [bool isValid() const](#isValid)
- [QString name() const](#name)
- [QStringList queryIcons() const](#queryIcons) (since 6.11)
- [QStringList queryIcons(int size, KIconLoader::Context context = KIconLoader::Any) const](#queryIcons-1)
- [QStringList queryIconsByContext(int size, KIconLoader::Context context = KIconLoader::Any) const](#queryIconsByContext)
- [QList\<int\> querySizes(KIconLoader::Group group) const](#querySizes)
- [QString screenshot() const](#screenshot)

## Static Public Members

- [QString current()](#current)
- [QString defaultThemeName()](#defaultThemeName)
- [void forceThemeForTests(const QString &themeName)](#forceThemeForTests)
- [void initTheme()](#initTheme) (since 6.3)
- [QStringList list()](#list)
- [void reconfigure()](#reconfigure)

## Detailed Description {#details}

This class is used by the iconloader but can be used by others too.

> **Warning:** You should not use this class externally. This class is exported because the KCM needs it.

*See also* [KIconLoader](kiconloader.md)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KIconTheme::KIconTheme(const QString &*name*, const QString &*appName* = QString(), const QString &*basePathHint* = QString()) {#KIconTheme}

Load an icon theme by name.

`name` the name of the theme (e.g. "hicolor" or "keramik")

`appName` the name of the application. Can be null. This argument allows applications to have themed application icons.

`basePathHint` optional hint where to search the app themes. This is appended at the end of the search paths

### \[static\] QString KIconTheme::current() {#current}

Returns the current icon theme.

### int KIconTheme::defaultSize(KIconLoader::Group *group*) const {#defaultSize}

The default size of this theme for a certain icon group.

`group` The icon group. See [KIconLoader::Group](kiconloader.md#Group-enum).

Returns The default size in pixels for the given icon group.

### \[static\] QString KIconTheme::defaultThemeName() {#defaultThemeName}

Returns the name of the default theme name

### int KIconTheme::depth() const {#depth}

The minimum display depth required for this theme. This can either be 8 or 32.

Returns the minimum bpp (8 or 32)

### QString KIconTheme::description() const {#description}

A description for the icon theme.

Returns a human-readable description of the theme, QString() if there is none

### QString KIconTheme::dir() const {#dir}

Returns the toplevel theme directory.

### QString KIconTheme::example() const {#example}

Return the name of the "example" icon. This can be used to present the theme to the user.

Returns the name of the example icon, QString() if there is none

### bool KIconTheme::followsColorScheme() const {#followsColorScheme}

If true, this theme is made of SVG icons that will be colorized following the system color scheme. This is necessary for monochrome themes that should look visible on both light and dark color schemes.

Returns true if the SVG will be colorized with a stylesheet.

### \[static\] void KIconTheme::forceThemeForTests(const QString &*themeName*) {#forceThemeForTests}

Force a current theme and disable automatic resolution of the current theme in favor of the forced theme.

To reset a forced theme, simply set an empty themeName.

`themeName` name of the theme to force as current theme, or an empty string to unset theme forcing.

> **Note:** This should only be used when a very precise expectation about the current theme is present. Most notably in unit tests this can be used to force a given theme.

> **Warning:** A forced theme persists across [reconfigure](kicontheme.md#reconfigure)() calls!

*See also* [current](kicontheme.md#current)

### bool KIconTheme::hasContext(KIconLoader::Context *context*) const {#hasContext}

Returns true if the theme has any icons for the given context.

### QString KIconTheme::iconPath(const QString &*name*, int *size*, KIconLoader::MatchType *match*) const {#iconPath}

Lookup an icon in the theme.

`name` The name of the icon, with extension.

`size` The desired size of the icon.

`match` The matching mode. [KIconLoader::MatchExact](kiconloader.md#MatchType-enum) returns an icon only if matches exactly. [KIconLoader::MatchBest](kiconloader.md#MatchType-enum) returns the best matching icon.

Returns An absolute path to the file of the icon if it's found, QString() otherwise.

KIconLoader::isValid will return true, and false otherwise.

### QString KIconTheme::iconPath(const QString &*name*, int *size*, KIconLoader::MatchType *match*, qreal *scale*) const {#iconPath-1}

Lookup an icon in the theme.

`name` The name of the icon, with extension.

`size` The desired size of the icon.

`match` The matching mode. [KIconLoader::MatchExact](kiconloader.md#MatchType-enum) returns an icon only if matches exactly. [KIconLoader::MatchBest](kiconloader.md#MatchType-enum) returns the best matching icon.

`scale` The scale of the icon group.

Returns An absolute path to the file of the icon if it's found, QString() otherwise.

KIconLoader::isValid will return true, and false otherwise.

### QString KIconTheme::iconPathByName(const QString &*name*, int *size*, KIconLoader::MatchType *match*) const {#iconPathByName}

Lookup an icon in the theme.

`name` The name of the icon, without extension.

`size` The desired size of the icon.

`match` The matching mode. [KIconLoader::MatchExact](kiconloader.md#MatchType-enum) returns an icon only if matches exactly. [KIconLoader::MatchBest](kiconloader.md#MatchType-enum) returns the best matching icon.

Returns An absolute path to the file of the icon if it's found, QString() otherwise.

KIconLoader::isValid will return true, and false otherwise.

### QString KIconTheme::iconPathByName(const QString &*name*, int *size*, KIconLoader::MatchType *match*, qreal *scale*) const {#iconPathByName-1}

Lookup an icon in the theme.

`name` The name of the icon, without extension.

`size` The desired size of the icon.

`match` The matching mode. [KIconLoader::MatchExact](kiconloader.md#MatchType-enum) returns an icon only if matches exactly. [KIconLoader::MatchBest](kiconloader.md#MatchType-enum) returns the best matching icon.

`scale` The scale of the icon group.

Returns An absolute path to the file of the icon if it's found, QString() otherwise.

KIconLoader::isValid will return true, and false otherwise.

### QStringList KIconTheme::inherits() const {#inherits}

The themes this icon theme falls back on.

Returns a list of icon themes that are used as fall-backs

### \[static, since 6.3\] void KIconTheme::initTheme() {#initTheme}

Enforces the Breeze icon theme (including our [KIconEngine](kiconengine.md) for re-coloring).

If the user has configured a different icon set, that one will be taken.

(following the settings in the application configuration with fallback to kdeglobals)

Must be called before the construction of the first Q(Core)Application, as it might need to modify plugin loading and installs a startup function.

If the application is already using the KDE platform theme, the icon set will not be touched and the platform theme will ensure proper theming.

Does setup the needed KColorSchemeManager to follow the system color mode starting with version 6.6.

This function was introduced in Qt 6.3.

### QString KIconTheme::internalName() const {#internalName}

The internal name of the icon theme (same as the name argument passed to the constructor).

Returns the internal name of the theme

### bool KIconTheme::isHidden() const {#isHidden}

The icon theme should be hidden to the user?

Returns true if the icon theme is hidden

### bool KIconTheme::isValid() const {#isValid}

The icon theme exists?

Returns true if the icon theme is valid

### \[static\] QStringList KIconTheme::list() {#list}

List all icon themes installed on the system, global and local.

Returns the list of all icon themes

### QString KIconTheme::name() const {#name}

The stylized name of the icon theme.

Returns the (human-readable) name of the theme

### \[since 6.11\] QStringList KIconTheme::queryIcons() const {#queryIcons}

Query all available icons.

Returns the list of icon names

This function was introduced in Qt 6.11.

### QStringList KIconTheme::queryIcons(int *size*, KIconLoader::Context *context* = KIconLoader::Any) const {#queryIcons-1}

Query available icons for a size and context.

`size` the size of the icons

`context` the context of the icons

Returns the list of icon names

### QStringList KIconTheme::queryIconsByContext(int *size*, KIconLoader::Context *context* = KIconLoader::Any) const {#queryIconsByContext}

Query available icons for a context and preferred size.

`size` the size of the icons

`context` the context of the icons

Returns the list of icon names

### QList\<int\> KIconTheme::querySizes(KIconLoader::Group *group*) const {#querySizes}

Query available sizes for a group.

`group` The icon group. See [KIconLoader::Group](kiconloader.md#Group-enum).

Returns a list of available sizes for the given group

### \[static\] void KIconTheme::reconfigure() {#reconfigure}

Reconfigure the theme.

### QString KIconTheme::screenshot() const {#screenshot}

Returns the name of the screenshot, QString() if there is none
