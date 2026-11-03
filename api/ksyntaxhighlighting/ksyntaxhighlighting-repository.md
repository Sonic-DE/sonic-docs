---
title: "KSyntaxHighlighting::Repository Class"
description: "Syntax highlighting repository."
---

# KSyntaxHighlighting::Repository Class

Syntax highlighting repository. [More...](#details)

- **Header:** `#include <KSyntaxHighlighting/Repository>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KSyntaxHighlighting)`  
  `target_link_libraries(mytarget PRIVATE KF6::KSyntaxHighlighting)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](ksyntaxhighlighting-repository-members.md)

## Public Types

- [enum Repository::DefaultTheme](#DefaultTheme-enum)

## Properties

- [\[read-only\] definitions : QList\<KSyntaxHighlighting::Definition\>](#definitions-prop)
- [\[read-only\] themes : QList\<KSyntaxHighlighting::Theme\>](#themes-prop)

## Public Functions

- [Repository()](#Repository)
- [void addCustomSearchPath(const QString &path)](#addCustomSearchPath)
- [QList\<QString\> customSearchPaths() const](#customSearchPaths)
- [KSyntaxHighlighting::Theme defaultTheme(KSyntaxHighlighting::Repository::DefaultTheme t = KSyntaxHighlighting::Repository::LightTheme) const](#defaultTheme)
- [KSyntaxHighlighting::Definition definitionForFileName(const QString &fileName) const](#definitionForFileName)
- [KSyntaxHighlighting::Definition definitionForMimeType(const QString &mimeType) const](#definitionForMimeType)
- [KSyntaxHighlighting::Definition definitionForName(const QString &defName) const](#definitionForName)
- [QList\<KSyntaxHighlighting::Definition\> definitions() const](#definitions)
- [QList\<KSyntaxHighlighting::Definition\> definitionsForFileName(const QString &fileName) const](#definitionsForFileName)
- [QList\<KSyntaxHighlighting::Definition\> definitionsForMimeType(const QString &mimeType) const](#definitionsForMimeType)
- [void reload()](#reload)
- [KSyntaxHighlighting::Theme theme(const QString &themeName) const](#theme)
- [KSyntaxHighlighting::Theme themeForPalette(const QPalette &palette) const](#themeForPalette)
- [QList\<KSyntaxHighlighting::Theme\> themes() const](#themes)

## Signals

- [void aboutToReload()](#aboutToReload) (since 6.0)
- [void reloaded()](#reloaded) (since 6.0)

## Detailed Description {#details}

The Repository gives access to all syntax Definitions available on the system, typically described in \*.xml files. The Definition files are read from the resource that is compiled into the executable, and from the file system. If a Definition exists in the resource and on the file system, then the one from the file system is chosen.

Typically, only one instance of the Repository is needed. This single instance can be thought of as a singleton you keep alive throughout the lifetime of your application. Then, either call [definitionForName](ksyntaxhighlighting-repository.md#definitionForName)() with the given language name (e.g. "QML" or "Java"), or [definitionForFileName](ksyntaxhighlighting-repository.md#definitionForFileName)() to obtain a Definition based on the filename/mimetype of the file. The function [definitions](ksyntaxhighlighting-repository.md#definitions)() returns a list of all available syntax Definition%s.

In addition to Definitions, the Repository also provides a list of Themes. A Theme is defined by a set of default text style colors as well as editor colors. These colors together provide all required colros for drawing all primitives of a text editor. All available Theme%s can be queried through [themes](ksyntaxhighlighting-repository.md#themes)(), and a Theme with a specific name is obtained through [theme](ksyntaxhighlighting-repository.md#theme)(). Additionally, [defaultTheme](ksyntaxhighlighting-repository.md#defaultTheme)() provides a way to obtain a default theme for either a light or a black color theme.

All highlighting Definition and Theme files are compiled into the shared [KSyntaxHighlighting](ksyntaxhighlighting-module.md) library by using the Qt resource system. Loading additional files from disk is supported as well.

Loading syntax Definition files works as follows:

- First, all syntax highlighting files are loaded that are located in [QStandardPaths::locateAll](https://doc.qt.io/qt-6/qstandardpaths.html#locateAll)([QStandardPaths::GenericDataLocation](https://doc.qt.io/qt-6/qstandardpaths.html#StandardLocation-enum), [QStringLiteral](https://doc.qt.io/qt-6/qstring.html#QStringLiteral)("org.kde.syntax-highlighting/syntax"), [QStandardPaths::LocateDirectory](https://doc.qt.io/qt-6/qstandardpaths.html#LocateOption-enum)); Under Unix, this uses $XDG\_DATA\_HOME and $XDG\_DATA\_DIRS, which could map to $HOME/.local5/share/org.kde.syntax-highlighting/syntax and /usr/share/org.kde.syntax-highlighting/syntax.
- Then, all files compiled into the library through resources are loaded. The internal resource path is ":/org.kde.syntax-highlighting/syntax". This path should never be touched by other applications.
- Then, all custom files compiled into resources are loaded. The resource path is ":/org.kde.syntax-highlighting/syntax-addons". This path can be used by other libraries/applications to bundle specialized definitions. Per default this path isn't used by the framework itself.
- Finally, the search path can be extended by calling [addCustomSearchPath](ksyntaxhighlighting-repository.md#addCustomSearchPath)(). A custom search path can either be a path on disk or again a path to a Qt resource.

Similarly, loading Theme files works as follows:

- First, all Theme files are loaded that are located in [QStandardPaths::locateAll](https://doc.qt.io/qt-6/qstandardpaths.html#locateAll)([QStandardPaths::GenericDataLocation](https://doc.qt.io/qt-6/qstandardpaths.html#StandardLocation-enum), [QStringLiteral](https://doc.qt.io/qt-6/qstring.html#QStringLiteral)("org.kde.syntax-highlighting/themes"), [QStandardPaths::LocateDirectory](https://doc.qt.io/qt-6/qstandardpaths.html#LocateOption-enum)); Under Unix, this uses $XDG\_DATA\_HOME and $XDG\_DATA\_DIRS, which could map to $HOME/.local5/share/org.kde.syntax-highlighting/themes and /usr/share/org.kde.syntax-highlighting/themes.
- Then, all files compiled into the library through resources are loaded. The internal resource path is ":/org.kde.syntax-highlighting/themes". This path should never be touched by other applications.
- Then, all custom files compiled into resources are loaded. The resource path is ":/org.kde.syntax-highlighting/themes-addons". This path can be used by other libraries/applications to bundle specialized themes. Per default this path isn't used by the framework itself.
- Finally, all Theme%s located in the paths added [addCustomSearchPath](ksyntaxhighlighting-repository.md#addCustomSearchPath)() are loaded.

> **Note:** Whenever a Definition or a Theme exists twice, the variant with higher version is used.

> **Note:** The [QStandardPaths](https://doc.qt.io/qt-6/qstandardpaths.html) lookup can be disabled by compiling the framework with the -DNO\_STANDARD\_PATHS define.

*See also* [Definition](ksyntaxhighlighting-definition.md), [Theme](ksyntaxhighlighting-theme.md), [AbstractHighlighter](ksyntaxhighlighting-abstracthighlighter.md)

## Member Type Documentation {#member-type-documentation}

### enum Repository::DefaultTheme {#DefaultTheme-enum}

Built-in default theme types.

| Constant |   |
| --- | --- |
| `KSyntaxHighlighting::Repository::LightTheme` | `0` |
| `KSyntaxHighlighting::Repository::DarkTheme` | `1` |

*See also* [defaultTheme](ksyntaxhighlighting-repository.md#defaultTheme)()

## Property Documentation {#property-documentation}

### \[read-only\] definitions : QList\<KSyntaxHighlighting::Definition\> {#definitions-prop}

**Access functions:**

- `QList`\<`KSyntaxHighlighting::Definition`\> **[definitions](ksyntaxhighlighting-repository.md#definitions)**() const

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

**Notifier signal:**

- `void` **[reloaded](ksyntaxhighlighting-repository.md#reloaded)**()

### \[read-only\] themes : QList\<KSyntaxHighlighting::Theme\> {#themes-prop}

**Access functions:**

- `QList`\<`KSyntaxHighlighting::Theme`\> **[themes](ksyntaxhighlighting-repository.md#themes)**() const

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

**Notifier signal:**

- `void` **[reloaded](ksyntaxhighlighting-repository.md#reloaded)**()

## Member Function Documentation {#member-function-documentation}

### Repository::Repository() {#Repository}

Create a new syntax definition repository. This will read the meta data information of all available syntax definition, which is a moderately expensive operation, it's therefore recommended to keep a single instance of Repository around as long as you need highlighting in your application.

### \[signal, since 6.0\] void Repository::aboutToReload() {#aboutToReload}

This signal is emitted before the reload is started.

This function was introduced in Qt 6.0.

### void Repository::addCustomSearchPath(const QString &*path*) {#addCustomSearchPath}

Add a custom search path to the repository. This path will be searched in addition to the usual locations for syntax and theme definition files. Both locations on disk as well as Qt resource paths are supported.

> **Note:** Internally, the two sub-folders `path/syntax` as well as `path/themes` are searched for additional Definition%s and Theme%s. Do not append syntax or themes to `path` yourself.

> **Note:** Calling this triggers a [reload](ksyntaxhighlighting-repository.md#reload)() of the repository.

### QList\<QString\> Repository::customSearchPaths() const {#customSearchPaths}

Returns the list of custom search paths added to the repository. By default, this list is empty.

*See also* [addCustomSearchPath](ksyntaxhighlighting-repository.md#addCustomSearchPath)()

### \[invokable\] KSyntaxHighlighting::Theme Repository::defaultTheme(KSyntaxHighlighting::Repository::DefaultTheme *t* = KSyntaxHighlighting::Repository::LightTheme) const {#defaultTheme}

Returns a default theme instance of the given type. The returned Theme is guaranteed to be a valid theme.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] KSyntaxHighlighting::Definition Repository::definitionForFileName(const QString &*fileName*) const {#definitionForFileName}

Returns the best matching Definition for the file named `fileName`. The match is performed based on the *extensions* and mimetype of the definition files. If multiple matches are found, the one with the highest priority is returned.

If no match is found, [Definition::isValid](ksyntaxhighlighting-definition.md#isValid)() of the returned instance returns false.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] KSyntaxHighlighting::Definition Repository::definitionForMimeType(const QString &*mimeType*) const {#definitionForMimeType}

Returns the best matching Definition to the type named `mimeType`

If no match is found, [Definition::isValid](ksyntaxhighlighting-definition.md#isValid)() of the returned instance returns false.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] KSyntaxHighlighting::Definition Repository::definitionForName(const QString &*defName*) const {#definitionForName}

Returns the Definition named `defName`.

If no Definition is found, [Definition::isValid](ksyntaxhighlighting-definition.md#isValid)() of the returned instance returns false.

> **Note:** The search is [Qt::CaseInsensitive](https://doc.qt.io/qt-6/qt.html#CaseSensitivity-enum) using untranslated names or alternative names. For instance, the cpp.xml definition file sets its name to C++ with an alternative name of CPP. Therefore, the strings "C++", "c++", "CPP" and "cpp" will all return a valid Definition file.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] QList\<KSyntaxHighlighting::Definition\> Repository::definitions() const {#definitions}

Returns all available Definition%s. Definition%ss are ordered by translated section and translated names, for consistent displaying.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

> **Note:** Getter function for property [definitions](ksyntaxhighlighting-repository.md#definitions-prop).

### \[invokable\] QList\<KSyntaxHighlighting::Definition\> Repository::definitionsForFileName(const QString &*fileName*) const {#definitionsForFileName}

Returns all Definition%s for the file named `fileName` sorted by priority. The match is performed based on the *extensions* and mimetype of the definition files.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### \[invokable\] QList\<KSyntaxHighlighting::Definition\> Repository::definitionsForMimeType(const QString &*mimeType*) const {#definitionsForMimeType}

Returns all Definition%s to the type named `mimeType` sorted by priority

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### void Repository::reload() {#reload}

Reloads the repository. This is a moderately expensive operations and should thus only be triggered when the installed syntax definition files changed.

### \[signal, since 6.0\] void Repository::reloaded() {#reloaded}

This signal is emitted when the reload is finished.

> **Note:** Notifier signal for properties [definitions](ksyntaxhighlighting-repository.md#definitions-prop) and [themes](ksyntaxhighlighting-repository.md#themes-prop).

This function was introduced in Qt 6.0.

### \[invokable\] KSyntaxHighlighting::Theme Repository::theme(const QString &*themeName*) const {#theme}

Returns the theme called `themeName`. If the requested theme cannot be found, the retunred Theme is invalid, see [Theme::isValid](ksyntaxhighlighting-theme.md#isValid)().

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

### KSyntaxHighlighting::Theme Repository::themeForPalette(const QPalette &*palette*) const {#themeForPalette}

Returns the best matching theme for the given palette

### \[invokable\] QList\<KSyntaxHighlighting::Theme\> Repository::themes() const {#themes}

Returns all available color themes. The returned list should never be empty.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

> **Note:** Getter function for property [themes](ksyntaxhighlighting-repository.md#themes-prop).
