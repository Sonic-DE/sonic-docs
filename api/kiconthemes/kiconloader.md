---
title: "KIconLoader Class"
description: "Iconloader for KDE."
---

# KIconLoader Class

Iconloader for KDE. [More...](#details)

- **Header:** `#include <KIconLoader>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS IconThemes)`  
  `target_link_libraries(mytarget PRIVATE KF6::IconThemes)`
- **Inherits:** [QObject](https://doc.qt.io/qt-6/qobject.html)

[List of all members, including inherited members](kiconloader-members.md)  
[Deprecated members](kiconloader-obsolete.md)

## Public Types

- [enum KIconLoader::Context](#Context-enum)
- [enum KIconLoader::Group](#Group-enum)
- [\[since 6.0\] enum KIconLoader::MatchType](#MatchType-enum)
- [enum KIconLoader::States](#States-enum)
- [enum KIconLoader::StdSizes](#StdSizes-enum)
- [enum KIconLoader::Type](#Type-enum)

## Public Functions

- [KIconLoader(const QString &appname = QString(), const QStringList &extraSearchPaths = QStringList(), QObject \*parent = nullptr)](#KIconLoader)
- [void addAppDir(const QString &appname, const QString &themeBaseDir = QString())](#addAppDir)
- [int currentSize(KIconLoader::Group group) const](#currentSize)
- [QPalette customPalette() const](#customPalette)
- [bool hasCustomPalette() const](#hasCustomPalette)
- [bool hasIcon(const QString &iconName) const](#hasIcon)
- [QString iconPath(const QString &name, int group\_or\_size, bool canReturnNull = false) const](#iconPath)
- [QString iconPath(const QString &name, int group\_or\_size, bool canReturnNull, qreal scale) const](#iconPath-1)
- [QPixmap loadIcon(const QString &name, KIconLoader::Group group, int size = 0, int state = KIconLoader::DefaultState, const QStringList &overlays = QStringList(), QString \*path\_store = nullptr, bool canReturnNull = false) const](#loadIcon)
- [QPixmap loadMimeTypeIcon(const QString &iconName, KIconLoader::Group group, int size = 0, int state = KIconLoader::DefaultState, const QStringList &overlays = QStringList(), QString \*path\_store = nullptr) const](#loadMimeTypeIcon)
- [QPixmap loadScaledIcon(const QString &name, KIconLoader::Group group, qreal scale, const QSize &size = {}, int state = KIconLoader::DefaultState, const QStringList &overlays = QStringList(), QString \*path\_store = nullptr, bool canReturnNull = false) const](#loadScaledIcon)
- [QPixmap loadScaledIcon(const QString &name, KIconLoader::Group group, qreal scale, const QSize &size, int state, const QStringList &overlays, QString \*path\_store, bool canReturnNull, const std::optional\<KIconColors\> &colorScheme) const](#loadScaledIcon-2)
- [QStringList queryIcons() const](#queryIcons) (since 6.11)
- [QStringList queryIcons(int group\_or\_size, KIconLoader::Context context = KIconLoader::Any) const](#queryIcons-1)
- [QStringList queryIconsByContext(int group\_or\_size, KIconLoader::Context context = KIconLoader::Any) const](#queryIconsByContext)
- [QStringList queryIconsByDir(const QString &iconsDir) const](#queryIconsByDir)
- [void reconfigure(const QString &appname, const QStringList &extraSearchPaths = QStringList())](#reconfigure)
- [void resetPalette()](#resetPalette)
- [QStringList searchPaths() const](#searchPaths)
- [void setCustomPalette(const QPalette &palette)](#setCustomPalette)
- [KIconTheme \*theme() const](#theme)

## Public Slots

- [void emitChange(KIconLoader::Group group)](#emitChange)

## Signals

- [void iconChanged(int group)](#iconChanged)
- [void iconLoaderSettingsChanged()](#iconLoaderSettingsChanged)

## Static Public Members

- [KIconLoader \*global()](#global)
- [QPixmap unknown()](#unknown)

## Detailed Description {#details}

> **Note:** For most icon loading use cases perfer using [QIcon::fromTheme](https://doc.qt.io/qt-6/qicon.html#fromTheme)

[KIconLoader](kiconloader.md) will load the current icon theme and all its base themes. Icons will be searched in any of these themes. Additionally, it caches icons and applies effects according to the user's preferences.

In KDE, it is encouraged to load icons by "Group". An icon group is a location on the screen where icons are being used. Standard groups are: Desktop, Toolbar, [MainToolbar](kiconloader.md#Group-enum), Small and Panel. Each group can have some centrally-configured effects applied to its icons. This makes it possible to offer a consistent icon look in all KDE applications.

The standard groups are defined below.

- [KIconLoader::Desktop](kiconloader.md#Group-enum): Icons in the iconview of konqueror, kdesktop and similar apps.
- [KIconLoader::Toolbar](kiconloader.md#Group-enum): Icons in toolbars.
- [KIconLoader::MainToolbar](kiconloader.md#Group-enum): Icons in the main toolbars.
- [KIconLoader::Small](kiconloader.md#Group-enum): Various small (typical 16x16) places: titlebars, listviews and menu entries.
- [KIconLoader::Panel](kiconloader.md#Group-enum): Icons in kicker's panel

The icons are stored on disk in an icon theme or in a standalone directory. The icon theme directories contain multiple sizes and/or depths for the same icon. The iconloader will load the correct one based on the icon group and the current theme. Icon themes are stored globally in share/icons, or, application specific in share/apps/$appdir/icons.

The standalone directories contain just one version of an icon. The directories that are searched are: $appdir/pics and $appdir/toolbar. Icons in these directories can be loaded by using the special group "User".

## Member Type Documentation {#member-type-documentation}

### enum KIconLoader::Context {#Context-enum}

Defines the context of the icon.

| Constant | Value | Description |
| --- | --- | --- |
| `KIconLoader::Any` | `0` | Some icon with unknown purpose. |
| `KIconLoader::Action` | `1` | An action icon (e.g. 'save', 'print'). |
| `KIconLoader::Application` | `2` | An icon that represents an application. |
| `KIconLoader::Device` | `3` | An icon that represents a device. |
| `KIconLoader::MimeType` | `4` | An icon that represents a mime type (or file type). |
| `KIconLoader::Animation` | `5` | An icon that is animated. |
| `KIconLoader::Category` | `6` | An icon that represents a category. |
| `KIconLoader::Emblem` | `7` | An icon that adds information to an existing icon. |
| `KIconLoader::Emote` | `8` | An icon that expresses an emotion. |
| `KIconLoader::International` | `9` | An icon that represents a country's flag. |
| `KIconLoader::Place` | `10` | An icon that represents a location (e.g. 'home', 'trash'). |
| `KIconLoader::StatusIcon` | `11` | An icon that represents an event. |

### enum KIconLoader::Group {#Group-enum}

The group of the icon.

| Constant | Value | Description |
| --- | --- | --- |
| `KIconLoader::NoGroup` | `-1` | No group |
| `KIconLoader::Desktop` | `0` | Desktop icons |
| `KIconLoader::FirstGroup` | `0` | First group |
| `KIconLoader::Toolbar` | `1` | Toolbar icons |
| `KIconLoader::MainToolbar` | `2` | Main toolbar icons |
| `KIconLoader::Small` | `3` | Small icons, e.g. for buttons |
| `KIconLoader::Panel` | `4` | Panel (Plasma Taskbar) icons |
| `KIconLoader::Dialog` | `5` | Icons for use in dialog titles, page lists, etc |
| `KIconLoader::LastGroup` | `6` | Last group |
| `KIconLoader::User` | `7` | User icons |

### \[since 6.0\] enum KIconLoader::MatchType {#MatchType-enum}

The type of a match.

| Constant | Value | Description |
| --- | --- | --- |
| `KIconLoader::MatchExact` | `0` | Only try to find an exact match. |
| `KIconLoader::MatchBest` | `1` | Take the best match if there is no exact match. |
| `KIconLoader::MatchBestOrGreaterSize` | `2` | Take the best match or the match with a greater size if there is no exact match. |

This enum was introduced in Qt 6.0.

### enum KIconLoader::States {#States-enum}

Defines the possible states of an icon.

| Constant | Value | Description |
| --- | --- | --- |
| `KIconLoader::DefaultState` | `0` | The default state. |
| `KIconLoader::ActiveState` | `1` | Icon is active. |
| `KIconLoader::DisabledState` | `2` | Icon is disabled. |
| `KIconLoader::SelectedState (since Qt 5.22)` | `3` | Icon is selected. |
| `KIconLoader::LastState` | `4` | Last state (last constant) |

### enum KIconLoader::StdSizes {#StdSizes-enum}

These are the standard sizes for icons.

| Constant | Value | Description |
| --- | --- | --- |
| `KIconLoader::SizeSmall` | `16` | small icons for menu entries |
| `KIconLoader::SizeSmallMedium` | `22` | slightly larger small icons for toolbars, panels, etc |
| `KIconLoader::SizeMedium` | `32` | medium sized icons for the desktop |
| `KIconLoader::SizeLarge` | `48` | large sized icons for the panel |
| `KIconLoader::SizeHuge` | `64` | huge sized icons for iconviews |
| `KIconLoader::SizeEnormous` | `128` | enormous sized icons for iconviews |

### enum KIconLoader::Type {#Type-enum}

The type of the icon.

| Constant | Value | Description |
| --- | --- | --- |
| `KIconLoader::Fixed` | `0` | Fixed-size icon. |
| `KIconLoader::Scalable` | `1` | Scalable-size icon. |
| `KIconLoader::Threshold` | `2` | A threshold icon. |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KIconLoader::KIconLoader(const QString &*appname* = QString(), const QStringList &*extraSearchPaths* = QStringList(), QObject \**parent* = nullptr) {#KIconLoader}

Constructs an iconloader.

`appname` Add the data directories of this application to the icon search path for the "User" group. The default argument adds the directories of the current application.

`extraSearchPaths` additional search paths, either absolute or relative to GenericDataLocation

Usually, you use the default iconloader, which can be accessed via [KIconLoader::global](kiconloader.md#global)(), so you hardly ever have to create an iconloader object yourself. That one is the application's iconloader.

### void KIconLoader::addAppDir(const QString &*appname*, const QString &*themeBaseDir* = QString()) {#addAppDir}

Adds `appname` to the list of application specific directories with `themeBaseDir` as its base directory.

Assume the icons are in /home/user/app/icons/hicolor/48x48/my\_app.png, the base directory would be /home/user/app/icons; [KIconLoader](kiconloader.md) automatically searches `themeBaseDir` + "/hicolor"

This directory must contain a dir structure as defined by the XDG icons specification

`appname` The application name.

`themeBaseDir` The base directory of the application's theme (eg. "/home/user/app/icons")

### int KIconLoader::currentSize(KIconLoader::Group *group*) const {#currentSize}

Returns the size of the specified icon group.

Using e.g. KIconLoader::SmallIcon will return 16.

`group` the group to check.

Returns the current size for an icon group.

### QPalette KIconLoader::customPalette() const {#customPalette}

The colors that will be used for the svg stylesheet in case the loaded icons are svg-based, icons can be colored in different ways in different areas of the application

Returns the palette, if any, an invalid one if the user didn't set it

*See also* [setCustomPalette](kiconloader.md#setCustomPalette)()

### \[static slot\] void KIconLoader::emitChange(KIconLoader::Group *group*) {#emitChange}

Emits an [iconChanged](kiconloader.md#iconChanged)() signal on all the [KIconLoader](kiconloader.md) instances in the system indicating that a system's icon group has changed in some way. It will also trigger a reload in all of them to update to the new theme.

`group` indicates the group that has changed

### \[static\] KIconLoader \*KIconLoader::global() {#global}

Returns the global icon loader initialized with the application name.

### bool KIconLoader::hasCustomPalette() const {#hasCustomPalette}

Returns whether we have set a custom palette using [setCustomPalette](kiconloader.md#setCustomPalette)

*See also* [resetPalette](kiconloader.md#resetPalette), [setCustomPalette](kiconloader.md#setCustomPalette)

### bool KIconLoader::hasIcon(const QString &*iconName*) const {#hasIcon}

### \[signal\] void KIconLoader::iconChanged(int *group*) {#iconChanged}

Emitted when the system icon theme changes

### \[signal\] void KIconLoader::iconLoaderSettingsChanged() {#iconLoaderSettingsChanged}

Emitted by newIconLoader once the new settings have been loaded

### QString KIconLoader::iconPath(const QString &*name*, int *group\_or\_size*, bool *canReturnNull* = false) const {#iconPath}

Returns the path of an icon.

`name` The name of the icon, without extension. If an absolute path is supplied for this parameter, iconPath will return it directly.

`group_or_size` If positive, search icons whose size is specified by the icon group `group_or_size`. If negative, search icons whose size is - `group_or_size`. See [KIconLoader::Group](kiconloader.md#Group-enum) and [KIconLoader::StdSizes](kiconloader.md#StdSizes-enum)

`canReturnNull` Can return a null string? If not, a path to the "unknown" icon will be returned.

Returns the path of an icon, can be null or the "unknown" icon when not found, depending on `canReturnNull`.

### QString KIconLoader::iconPath(const QString &*name*, int *group\_or\_size*, bool *canReturnNull*, qreal *scale*) const {#iconPath-1}

Returns the path of an icon.

`name` The name of the icon, without extension. If an absolute path is supplied for this parameter, [iconPath](kiconloader.md#iconPath) will return it directly.

`group_or_size` If positive, search icons whose size is specified by the icon group `group_or_size`. If negative, search icons whose size is - `group_or_size`. See [KIconLoader::Group](kiconloader.md#Group-enum) and [KIconLoader::StdSizes](kiconloader.md#StdSizes-enum)

`canReturnNull` Can return a null string? If not, a path to the "unknown" icon will be returned.

`scale` The scale of the icon group.

Returns the path of an icon, can be null or the "unknown" icon when not found, depending on `canReturnNull`.

### QPixmap KIconLoader::loadIcon(const QString &*name*, KIconLoader::Group *group*, int *size* = 0, int *state* = KIconLoader::DefaultState, const QStringList &*overlays* = QStringList(), QString \**path\_store* = nullptr, bool *canReturnNull* = false) const {#loadIcon}

Loads an icon. It will try very hard to find an icon which is suitable. If no exact match is found, a close match is searched. If neither an exact nor a close match is found, a null pixmap or the "unknown" pixmap is returned, depending on the value of the `canReturnNull` parameter.

`name` The name of the icon, without extension.

`group` The icon group. This will specify the size of and effects to be applied to the icon.

`size` If nonzero, this overrides the size specified by `group`. See [KIconLoader::StdSizes](kiconloader.md#StdSizes-enum).

`state` The icon state: `DefaultState`, `ActiveState` or `DisabledState`. Depending on the user's preferences, the iconloader may apply a visual effect to hint about its state.

`overlays` a list of emblem icons to overlay, by name

`path_store` If not null, the path of the icon is stored here, if the icon was found. If the icon was not found `path_store` is unaltered even if the "unknown" pixmap was returned.

`canReturnNull` Can return a null pixmap? If false, the "unknown" pixmap is returned when no appropriate icon has been found. Note: a null pixmap can still be returned in the event of invalid parameters, such as empty names, negative sizes, and etc.

Returns the [QPixmap](https://doc.qt.io/qt-6/qpixmap.html). Can be null when not found, depending on `canReturnNull`.

*See also* [drawOverlays](kiconloader-obsolete.md#drawOverlays)

### QPixmap KIconLoader::loadMimeTypeIcon(const QString &*iconName*, KIconLoader::Group *group*, int *size* = 0, int *state* = KIconLoader::DefaultState, const QStringList &*overlays* = QStringList(), QString \**path\_store* = nullptr) const {#loadMimeTypeIcon}

Loads an icon for a mimetype. This is basically like [loadIcon](kiconloader.md#loadIcon) except that extra desktop themes are loaded if necessary.

Consider using [QIcon::fromTheme](https://doc.qt.io/qt-6/qicon.html#fromTheme)() with a fallback to "application-octet-stream" instead.

`iconName` The name of the icon, without extension, usually from KMimeType.

`group` The icon group. This will specify the size of and effects to be applied to the icon.

`size` If nonzero, this overrides the size specified by `group`. See [KIconLoader::StdSizes](kiconloader.md#StdSizes-enum).

`state` The icon state: `DefaultState`, `ActiveState` or `DisabledState`. Depending on the user's preferences, the iconloader may apply a visual effect to hint about its state.

`path_store` If not null, the path of the icon is stored here.

`overlays` a list of emblem icons to overlay, by name

Returns the [QPixmap](https://doc.qt.io/qt-6/qpixmap.html). Can not be null, the "unknown" pixmap is returned when no appropriate icon has been found.

*See also* [drawOverlays](kiconloader-obsolete.md#drawOverlays)

### QPixmap KIconLoader::loadScaledIcon(const QString &*name*, KIconLoader::Group *group*, qreal *scale*, const QSize &*size* = {}, int *state* = KIconLoader::DefaultState, const QStringList &*overlays* = QStringList(), QString \**path\_store* = nullptr, bool *canReturnNull* = false) const {#loadScaledIcon}

Loads an icon. It will try very hard to find an icon which is suitable. If no exact match is found, a close match is searched. If neither an exact nor a close match is found, a null pixmap or the "unknown" pixmap is returned, depending on the value of the `canReturnNull` parameter.

`name` The name of the icon, without extension.

`group` The icon group. This will specify the size of and effects to be applied to the icon.

`scale` The scale of the icon group to use. If no icon exists in the scaled group, a 1x icon with its size multiplied by the scale will be loaded instead.

`size` If nonzero, this overrides the size specified by `group`. See [KIconLoader::StdSizes](kiconloader.md#StdSizes-enum). The icon will be fit into `size` without changing the aspect ratio, which particularly matters for non-square icons.

`state` The icon state: `DefaultState`, `ActiveState` or `DisabledState`. Depending on the user's preferences, the iconloader may apply a visual effect to hint about its state.

`overlays` a list of emblem icons to overlay, by name

`path_store` If not null, the path of the icon is stored here, if the icon was found. If the icon was not found `path_store` is unaltered even if the "unknown" pixmap was returned.

`canReturnNull` Can return a null pixmap? If false, the "unknown" pixmap is returned when no appropriate icon has been found. Note: a null pixmap can still be returned in the event of invalid parameters, such as empty names, negative sizes, and etc.

Returns the [QPixmap](https://doc.qt.io/qt-6/qpixmap.html). Can be null when not found, depending on `canReturnNull`.

*See also* [drawOverlays](kiconloader-obsolete.md#drawOverlays)

### QPixmap KIconLoader::loadScaledIcon(const QString &*name*, KIconLoader::Group *group*, qreal *scale*, const QSize &*size*, int *state*, const QStringList &*overlays*, QString \**path\_store*, bool *canReturnNull*, const std::optional\<KIconColors\> &*colorScheme*) const {#loadScaledIcon-2}

Loads an icon. It will try very hard to find an icon which is suitable. If no exact match is found, a close match is searched. If neither an exact nor a close match is found, a null pixmap or the "unknown" pixmap is returned, depending on the value of the `canReturnNull` parameter.

`name` The name of the icon, without extension.

`group` The icon group. This will specify the size of and effects to be applied to the icon.

`scale` The scale of the icon group to use. If no icon exists in the scaled group, a 1x icon with its size multiplied by the scale will be loaded instead.

`size` If nonzero, this overrides the size specified by `group`. See [KIconLoader::StdSizes](kiconloader.md#StdSizes-enum). The icon will be fit into `size` without changing the aspect ratio, which particularly matters for non-square icons.

`state` The icon state: `DefaultState`, `ActiveState` or `DisabledState`. Depending on the user's preferences, the iconloader may apply a visual effect to hint about its state.

`overlays` a list of emblem icons to overlay, by name

`path_store` If not null, the path of the icon is stored here, if the icon was found. If the icon was not found `path_store` is unaltered even if the "unknown" pixmap was returned. `canReturnNull` Can return a null pixmap? If false, the "unknown" pixmap is returned when no appropriate icon has been found. Note: a null pixmap can still be returned in the event of invalid parameters, such as empty names, negative sizes, and etc.

`colorScheme` will define the stylesheet used to color this icon. Note this will only work if `name` is an svg file.

Returns the [QPixmap](https://doc.qt.io/qt-6/qpixmap.html). Can be null when not found, depending on `canReturnNull`.

*See also* [drawOverlays](kiconloader-obsolete.md#drawOverlays)()

### \[since 6.11\] QStringList KIconLoader::queryIcons() const {#queryIcons}

Queries all available icons.

This function was introduced in Qt 6.11.

### QStringList KIconLoader::queryIcons(int *group\_or\_size*, KIconLoader::Context *context* = KIconLoader::Any) const {#queryIcons-1}

Queries all available icons for a specific group, having a specific context.

`group_or_size` If positive, search icons whose size is specified by the icon group `group_or_size`. If negative, search icons whose size is - `group_or_size`. See [KIconLoader::Group](kiconloader.md#Group-enum) and [KIconLoader::StdSizes](kiconloader.md#StdSizes-enum)

`context` The icon context. Returns a list of all icons

### QStringList KIconLoader::queryIconsByContext(int *group\_or\_size*, KIconLoader::Context *context* = KIconLoader::Any) const {#queryIconsByContext}

Queries all available icons for a specific context.

`group_or_size` The icon preferred group or size. If available at this group or size, those icons will be returned, in other case, icons of undefined size will be returned. Positive numbers are groups, negative numbers are negated sizes. See [KIconLoader::Group](kiconloader.md#Group-enum) and [KIconLoader::StdSizes](kiconloader.md#StdSizes-enum)

`context` The icon context.

Returns A [QStringList](https://doc.qt.io/qt-6/qstringlist.html) containing the icon names available for that context

### QStringList KIconLoader::queryIconsByDir(const QString &*iconsDir*) const {#queryIconsByDir}

Returns a list of all icons (\*.png or \*.xpm extension) in the given directory.

`iconsDir` the directory to search in Returns A [QStringList](https://doc.qt.io/qt-6/qstringlist.html) containing the icon paths

### void KIconLoader::reconfigure(const QString &*appname*, const QStringList &*extraSearchPaths* = QStringList()) {#reconfigure}

Reconfigure the icon loader, for instance to change the associated app name or extra search paths.

This also clears the in-memory pixmap cache (even if the appname didn't change, which is useful for unittests)

`appname` the application name (empty for the global iconloader)

`extraSearchPaths` additional search paths, either absolute or relative to GenericDataLocation

### void KIconLoader::resetPalette() {#resetPalette}

Resets the custom palette used by the [KIconLoader](kiconloader.md) to use the [QGuiApplication::palette](https://doc.qt.io/qt-6/qguiapplication.html#palette)() again (and to follow it in case the application's palette changes)

### QStringList KIconLoader::searchPaths() const {#searchPaths}

Returns all the search paths for this icon loader, either absolute or relative to GenericDataLocation.

Mostly internal (for [KIconDialog](../kiconwidgets/kicondialog.md)).

### void KIconLoader::setCustomPalette(const QPalette &*palette*) {#setCustomPalette}

Sets the colors for this [KIconLoader](kiconloader.md).

> **Note:** if you set a custom palette, if you are using some colors from application's palette, you need to track the application palette changes by yourself.

If you no longer wish to use a custom palette, use [resetPalette](kiconloader.md#resetPalette)()

*See also* [customPalette](kiconloader.md#customPalette)(), [resetPalette](kiconloader.md#resetPalette)()

### KIconTheme \*KIconLoader::theme() const {#theme}

Returns a pointer to the current theme. Can be used to query available and default sizes for groups.

> **Note:** The [KIconTheme](kicontheme.md) will change if [reconfigure](kiconloader.md#reconfigure)() is called and therefore it's not recommended to store the pointer anywhere.

Returns a pointer to the current theme. 0 if no theme set.

### \[static\] QPixmap KIconLoader::unknown() {#unknown}

Returns the unknown icon. An icon that is used when no other icon can be found.

## Related Non-Members {#related-non-members}

### QIcon icon(const QString &*iconName*, KIconLoader \**iconLoader* = nullptr) {#icon}

Returns a [QIcon](https://doc.qt.io/qt-6/qicon.html) with an appropriate [KIconEngine](kiconengine.md) to perform loading and rendering. KIcons thus adhere to KDE style and effect standards.

### QIcon icon(const QString &*iconName*, const KIconColors &*colors*, KIconLoader \**iconLoader* = nullptr) {#icon-1}

Returns a [QIcon](https://doc.qt.io/qt-6/qicon.html) with an appropriate [KIconEngine](kiconengine.md) to perform loading and rendering. KIcons thus adhere to KDE style and effect standards.

### QIcon icon(const QString &*iconName*, const QStringList &*overlays*, KIconLoader \**iconLoader* = nullptr) {#icon-2}

Returns a [QIcon](https://doc.qt.io/qt-6/qicon.html) for the given icon, with additional overlays.
