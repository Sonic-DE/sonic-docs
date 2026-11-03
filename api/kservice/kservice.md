---
title: "KService Class"
description: "Represents an installed application."
---

# KService Class

Represents an installed application. [More...](#details)

- **Header:** `#include <KService>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Service)`  
  `target_link_libraries(mytarget PRIVATE KF6::Service)`
- **Inherits:** [KSycocaEntry](ksycocaentry.md)

[List of all members, including inherited members](kservice-members.md)

## Public Types

- [KService::List](#List-typedef)
- [KService::Ptr](#Ptr-typedef)

## Public Functions

- [KService(const QString &fullpath)](#KService)
- [KService(const KDesktopFile \*config, const QString &entryPath = QString())](#KService-1)
- [KService(const QString &name, const QString &exec, const QString &icon)](#KService-2)
- [QList\<KServiceAction\> actions() const](#actions)
- [QString aliasFor() const](#aliasFor)
- [bool allowMultipleFiles() const](#allowMultipleFiles)
- [QStringList categories() const](#categories)
- [QString comment() const](#comment)
- [QString desktopEntryName() const](#desktopEntryName)
- [QString docPath() const](#docPath)
- [QString exec() const](#exec)
- [QString genericName() const](#genericName)
- [bool hasMimeType(const QString &mimeType) const](#hasMimeType)
- [QString icon() const](#icon)
- [bool isApplication() const](#isApplication)
- [QStringList keywords() const](#keywords)
- [QString locateLocal() const](#locateLocal)
- [QString menuId() const](#menuId)
- [QStringList mimeTypes() const](#mimeTypes)
- [bool noDisplay() const](#noDisplay)
- [template \<typename T\> T property(const QString &name) const](#property) (since 6.0)
- [bool runOnDiscreteGpu() const](#runOnDiscreteGpu)
- [QStringList schemeHandlers() const](#schemeHandlers) (since 6.0)
- [bool showInCurrentDesktop() const](#showInCurrentDesktop)
- [bool showOnCurrentPlatform() const](#showOnCurrentPlatform)
- [std::optional\<bool\> startupNotify() const](#startupNotify) (since 6.0)
- [QString storageId() const](#storageId)
- [bool substituteUid() const](#substituteUid)
- [QStringList supportedProtocols() const](#supportedProtocols) (since 6.0)
- [bool terminal() const](#terminal)
- [QString terminalOptions() const](#terminalOptions)
- [QString untranslatedGenericName() const](#untranslatedGenericName)
- [QString untranslatedName() const](#untranslatedName) (since 6.0)
- [QString username() const](#username)
- [QString workingDirectory() const](#workingDirectory)

## Static Public Members

- [KService::List allServices()](#allServices)
- [QString newServicePath(bool showInMenu, const QString &suggestedName, QString \*menuId = nullptr, const QStringList \*reservedMenuIds = nullptr)](#newServicePath)
- [KService::Ptr serviceByDesktopName(const QString &\_name)](#serviceByDesktopName)
- [KService::Ptr serviceByDesktopPath(const QString &\_path)](#serviceByDesktopPath)
- [KService::Ptr serviceByMenuId(const QString &\_menuId)](#serviceByMenuId)
- [KService::Ptr serviceByStorageId(const QString &\_storageId)](#serviceByStorageId)

## Detailed Description {#details}

To obtain a [KService](kservice.md) instance for a specific application you typically use [serviceByDesktopName](kservice.md#serviceByDesktopName)(), e.g.:

```cpp
KService::Ptr service = KService::serviceByDesktopName("org.kde.kate");
```

Other typical usage would be in combination with [KApplicationTrader](kapplicationtrader.md) to obtain e.g. the default application for a given file type.

See the [Desktop Entry Specification](https://specifications.freedesktop.org/desktop-entry-spec/latest/)

## Member Type Documentation {#member-type-documentation}

### KService::List {#List-typedef}

A list of shared data pointers for [KService](kservice.md).

### KService::Ptr {#Ptr-typedef}

A shared data pointer for [KService](kservice.md).

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KService::KService(const QString &*fullpath*) {#KService}

Construct a service and take all information from a .desktop file.

`fullpath` Full path to the .desktop file.

### \[explicit\] KService::KService(const KDesktopFile \**config*, const QString &*entryPath* = QString()) {#KService-1}

Construct a service and take all information from a desktop file.

`config` the desktop file to read

`entryPath` optional relative path to store for findByName

### KService::KService(const QString &*name*, const QString &*exec*, const QString &*icon*) {#KService-2}

Construct a temporary service with a given name, exec-line and icon.

`name` the name of the service

`exec` the executable

`icon` the name of the icon

### QList\<KServiceAction\> KService::actions() const {#actions}

Returns the actions defined in this desktop file

Only valid actions according to specification are included.

> **Note:** This function copies the action list.

### QString KService::aliasFor() const {#aliasFor}

A desktop file name that this application is an alias for.

This is used when a `NoDisplay` application is used to enforce specific handling for an application. In that case the `NoDisplay` application is an `AliasFor` another application and be considered roughly equal to the `AliasFor` application (which should not be `NoDisplay=true`)

For example Okular supplies a desktop file for each supported format (e.g. PDF), all of which `NoDisplay` and it is merely there to selectively support specific file formats. A UI may choose to display the aliased entry org.kde.okular instead of the NoDisplay entries.

Returns [QString](https://doc.qt.io/qt-6/qstring.html) desktopName of the aliased application (excluding .desktop suffix)

### \[static\] KService::List KService::allServices() {#allServices}

Returns the whole list of applications.

Useful for being able to to display them in a list box, for example.

More memory consuming than the ones above, don't use unless really necessary.

### bool KService::allowMultipleFiles() const {#allowMultipleFiles}

Returns whether this application can handle several files as startup arguments.

### QStringList KService::categories() const {#categories}

Returns a list of VFolder categories.

### QString KService::comment() const {#comment}

Returns the descriptive comment for the application, if there is one. if not set

### QString KService::desktopEntryName() const {#desktopEntryName}

Returns the filename of the desktop entry without any extension, e.g. "org.kde.kate"

### QString KService::docPath() const {#docPath}

Returns the path to the documentation for this application.

### QString KService::exec() const {#exec}

Returns the command that the service executes, or QString() if not set

### QString KService::genericName() const {#genericName}

Returns the generic name for the application, if there is one (e.g. "Mail Client").

### bool KService::hasMimeType(const QString &*mimeType*) const {#hasMimeType}

Returns whether the application supports this MIME type

`mimeType` The name of the MIME type you are interested in determining whether this service supports.

### QString KService::icon() const {#icon}

Returns the name of the icon associated with the service, or QString() if not set

### bool KService::isApplication() const {#isApplication}

Whether this service is an application

Returns `true` if this service is an application, i.e. it has `Type=Application` in its .desktop file and [exec](kservice.md#exec)() will not be empty.

### QStringList KService::keywords() const {#keywords}

Returns a list of descriptive keywords for the application, if there are any.

### QString KService::locateLocal() const {#locateLocal}

Returns a path that can be used for saving changes to this application

### QString KService::menuId() const {#menuId}

Returns the menu ID of the application desktop entry.

The menu ID is used to add or remove the entry to a menu.

### QStringList KService::mimeTypes() const {#mimeTypes}

Returns the list of MIME types that this application supports.

Note that this doesn't include inherited MIME types, only the MIME types listed in the .desktop file.

### \[static\] QString KService::newServicePath(bool *showInMenu*, const QString &*suggestedName*, QString \**menuId* = nullptr, const QStringList \**reservedMenuIds* = nullptr) {#newServicePath}

Returns a path that can be used to create a new [KService](kservice.md) based on `suggestedName`.

`showInMenu` `true`, if the application should be shown in the KDE menu `false`, if the application should be hidden from the menu This argument isn't used anymore, use `NoDisplay=true` to hide the application.

`suggestedName` name to base the file on, if an application with such a name already exists, a suffix will be added to make it unique (e.g. foo.desktop, foo-1.desktop, foo-2.desktop).

`menuId` If provided, [menuId](kservice.md#menuId) will be set to the menu id to use for the [KService](kservice.md)

`reservedMenuIds` If provided, the path and menu id will be chosen in such a way that the new menu id does not conflict with any of the reservedMenuIds

### bool KService::noDisplay() const {#noDisplay}

Returns whether the entry should be hidden from the menu.

Such services still appear in trader queries, i.e. in "Open With" popup menus for instance.

### \[since 6.0\] template \<typename T\> T KService::property(const QString &*name*) const {#property}

Returns the requested property.

T the type of the requested property.

`name` the name of the property.

This function was introduced in Qt 6.0.

### bool KService::runOnDiscreteGpu() const {#runOnDiscreteGpu}

Returns `true` if the application indicates that it's preferred to run on a discrete graphics card, otherwise return `false`.

In releases older than 5.86, this method checked for the `X-KDE-RunOnDiscreteGpu` key in the .desktop file represented by this service; starting from 5.86 this method now also checks for `PrefersNonDefaultGPU` key (added to the Freedesktop.org desktop entry spec in version 1.4 of the spec).

### \[since 6.0\] QStringList KService::schemeHandlers() const {#schemeHandlers}

Returns the list of scheme handlers this application supports.

For example a web browser could return {"http", "https"}.

This is taken from the x-scheme-handler MIME types listed in the .desktop file.

This function was introduced in Qt 6.0.

### \[static\] KService::Ptr KService::serviceByDesktopName(const QString &*\_name*) {#serviceByDesktopName}

Find an application by the name of its desktop file, not depending on its actual location (as long as it's under the applications or application directories). For instance "konqbrowser" or "kcookiejar". Note that the ".desktop" extension is implicit.

This is the recommended method (safe even if the user moves stuff) but note that it assumes that no two entries have the same filename.

`_name` the name of the configuration file

Returns a pointer to the requested application or `nullptr` if the application is unknown.

Very important: Don't store the result in a [KService](kservice.md)\* !

### \[static\] KService::Ptr KService::serviceByDesktopPath(const QString &*\_path*) {#serviceByDesktopPath}

Find a application based on its path as returned by [entryPath](ksycocaentry.md#entryPath)().

It's usually better to use [serviceByStorageId](kservice.md#serviceByStorageId)() instead.

`_path` the path of the configuration file

Returns a pointer to the requested application or `nullptr` if the application is unknown.

Very important: Don't store the result in a [KService](kservice.md)\* !

### \[static\] KService::Ptr KService::serviceByMenuId(const QString &*\_menuId*) {#serviceByMenuId}

Find a application by its menu-id

`_menuId` the menu id of the application

Returns a pointer to the requested application or `nullptr` if the application is unknown.

Very important: Don't store the result in a [KService](kservice.md)\* !

### \[static\] KService::Ptr KService::serviceByStorageId(const QString &*\_storageId*) {#serviceByStorageId}

Find a application by its storage-id or desktop-file path. This function will try very hard to find a matching application.

`_storageId` the storage id or desktop-file path of the application

Returns a pointer to the requested application or `nullptr` if the application is unknown.

Very important: Don't store the result in a [KService](kservice.md)\* !

### bool KService::showInCurrentDesktop() const {#showInCurrentDesktop}

Returns whether the application should be shown in the current desktop (including in context menus).

[KApplicationTrader](kapplicationtrader.md) honors this and removes such services from its results.

### bool KService::showOnCurrentPlatform() const {#showOnCurrentPlatform}

Returns whether the application should be shown on the current platform (e.g. on xcb or on wayland).

### \[since 6.0\] std::optional\<bool\> KService::startupNotify() const {#startupNotify}

Returns the value of StartupNotify for this service.

If the service doesn't define a value nullopt is returned.

See StartupNotify in the [Desktop Entry Specification](https://specifications.freedesktop.org/desktop-entry-spec/latest/).

This function was introduced in Qt 6.0.

### QString KService::storageId() const {#storageId}

Returns a normalized ID suitable for storing in configuration files.

It will be based on the menu-id when available and otherwise falls back to [entryPath](ksycocaentry.md#entryPath)()

### bool KService::substituteUid() const {#substituteUid}

Returns whether the application needs to run under a different UID.

*See also* [username](kservice.md#username)()

### \[since 6.0\] QStringList KService::supportedProtocols() const {#supportedProtocols}

Returns the list of protocols this application supports.

This is taken from the x-scheme-handler MIME types listed in the .desktop file as well as the 'X-KDE-Protocols' entry

For example a web browser could return {"http", "https"}.

This function was introduced in Qt 6.0.

### bool KService::terminal() const {#terminal}

Checks whether the application should be run in a terminal.

This corresponds to `Terminal=true` in the .desktop file.

Returns `true` if the application should be run in a terminal.

### QString KService::terminalOptions() const {#terminalOptions}

Returns any options associated with the terminal the application runs in, if it requires a terminal.

The application must be a TTY-oriented program.

### QString KService::untranslatedGenericName() const {#untranslatedGenericName}

Returns the untranslated (US English) generic name for the application, if there is one (e.g. "Mail Client").

### \[since 6.0\] QString KService::untranslatedName() const {#untranslatedName}

Returns the untranslated name for the given service

This function was introduced in Qt 6.0.

### QString KService::username() const {#username}

Returns the user name if the application runs with a different user id.

*See also* [substituteUid](kservice.md#substituteUid)()

### QString KService::workingDirectory() const {#workingDirectory}

Returns the working directory to run the program in, or QString() if not set
