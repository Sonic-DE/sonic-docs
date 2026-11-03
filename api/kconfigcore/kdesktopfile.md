---
title: "KDesktopFile Class"
description: "Persistent platform-independent application settings."
---

# KDesktopFile Class

Persistent platform-independent application settings. [More...](#details)

- **Header:** `#include <KDesktopFile>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS Config)`  
  `target_link_libraries(mytarget PRIVATE KF6::ConfigCore)`
- **Inherits:** [KConfig](kconfig.md)

[List of all members, including inherited members](kdesktopfile-members.md)

## Public Functions

- [KDesktopFile(const QString &fileName)](#KDesktopFile)
- [KDesktopFile(QStandardPaths::StandardLocation resourceType, const QString &fileName)](#KDesktopFile-1)
- [~KDesktopFile()](#dtor.KDesktopFile)
- [KConfigGroup actionGroup(const QString &group)](#actionGroup)
- [KConfigGroup actionGroup(const QString &group) const](#actionGroup-1)
- [QList\<KDesktopFileAction\> actions() const](#actions) (since 6.0)
- [KDesktopFile \*copyTo(const QString &file) const](#copyTo)
- [KConfigGroup desktopGroup() const](#desktopGroup)
- [QString fileName() const](#fileName)
- [bool hasActionGroup(const QString &group) const](#hasActionGroup)
- [bool hasApplicationType() const](#hasApplicationType)
- [bool hasDeviceType() const](#hasDeviceType)
- [bool hasLinkType() const](#hasLinkType)
- [bool noDisplay() const](#noDisplay)
- [QStringList readActions() const](#readActions)
- [QString readComment() const](#readComment)
- [QString readDocPath() const](#readDocPath)
- [QString readGenericName() const](#readGenericName)
- [QString readIcon() const](#readIcon)
- [QStringList readMimeTypes() const](#readMimeTypes)
- [QString readName() const](#readName)
- [QString readPath() const](#readPath)
- [QString readType() const](#readType)
- [QString readUrl() const](#readUrl)
- [bool tryExec() const](#tryExec)

## Static Public Members

- [bool isAuthorizedDesktopFile(const QString &path)](#isAuthorizedDesktopFile)
- [bool isDesktopFile(const QString &path)](#isDesktopFile)
- [QString locateLocal(const QString &path)](#locateLocal)

## Detailed Description {#details}

This class implements KDE's support for the freedesktop.org [Desktop Entry Spec](https://specifications.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html).

*See also* [KConfigBase](kconfigbase.md), [KConfig](kconfig-index.md), [KDesktopFileAction](kdesktopfileaction.md)

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KDesktopFile::KDesktopFile(const QString &*fileName*) {#KDesktopFile}

Constructs a [KDesktopFile](kdesktopfile.md) object with the given `fileName` in its standard location [QStandardPaths::ApplicationsLocation](https://doc.qt.io/qt-6/qstandardpaths.html#StandardLocation-enum).

*See also* [QStandardPaths::ApplicationsLocation](https://doc.qt.io/qt-6/qstandardpaths.html#StandardLocation-enum)

### \[explicit\] KDesktopFile::KDesktopFile(QStandardPaths::StandardLocation *resourceType*, const QString &*fileName*) {#KDesktopFile-1}

Constructs a [KDesktopFile](kdesktopfile.md) object in `resourceType` with the given `fileName`.

The `resourceType` allows to change where to search for the desktop file if `fileName` is not absolute. For instance, you might want to specify GenericConfigLocation.

*See also* [QStandardPaths::StandardLocation](https://doc.qt.io/qt-6/qstandardpaths.html#StandardLocation-enum)

### \[override virtual noexcept\] KDesktopFile::~KDesktopFile() {#dtor.KDesktopFile}

Destructs the [KDesktopFile](kdesktopfile.md) object.

Writes back any changed configuration entries.

### KConfigGroup KDesktopFile::actionGroup(const QString &*group*) {#actionGroup}

Sets a new desktop action `group`.

### KConfigGroup KDesktopFile::actionGroup(const QString &*group*) const {#actionGroup-1}

Sets a new desktop action `group`.

### \[since 6.0\] QList\<KDesktopFileAction\> KDesktopFile::actions() const {#actions}

Returns the desktop file's actions.

This function was introduced in Qt 6.0.

### KDesktopFile \*KDesktopFile::copyTo(const QString &*file*) const {#copyTo}

Copies all entries from this config object to a new [KDesktopFile](kdesktopfile.md) object that will save itself to `file`.

Actual saving to `file` happens when the returned object is destructed or when [sync](kconfigbase.md#sync)() is called upon it.

### KConfigGroup KDesktopFile::desktopGroup() const {#desktopGroup}

Returns the main config group (named "Desktop Entry") in a .desktop file.

### QString KDesktopFile::fileName() const {#fileName}

Returns the name of the .desktop file that was used to construct this [KDesktopFile](kdesktopfile.md).

### bool KDesktopFile::hasActionGroup(const QString &*group*) const {#hasActionGroup}

Returns whether the given action `group` exists.

### bool KDesktopFile::hasApplicationType() const {#hasApplicationType}

Returns whether there is an entry "Type=Application".

### bool KDesktopFile::hasDeviceType() const {#hasDeviceType}

Returns whether there is an entry "Type=FSDevice".

### bool KDesktopFile::hasLinkType() const {#hasLinkType}

Returns whether there is a "Type=Link" entry.

The link points to the "URL=" entry.

### \[static\] bool KDesktopFile::isAuthorizedDesktopFile(const QString &*path*) {#isAuthorizedDesktopFile}

Returns whether the user is authorized to run desktop file at the given `path`.

By default users are authorized to run all desktop files but the Kiosk framework can be used to activate certain restrictions.

Note that desktop files that are not in a standard location (as specified by `XDG_DATA_DIRS`) must have their executable bit set to be authorized regardless of Kiosk settings to prevent users from inadvertently running trojan desktop files.

*See also* [KAuthorized](kauthorized.md), [Kiosk - Simple configuration management for large deployment](https://develop.kde.org/docs/administration/kiosk/)

### \[static\] bool KDesktopFile::isDesktopFile(const QString &*path*) {#isDesktopFile}

Returns whether the file in the given `path` is a desktop file.

The check is performed looking at the file extension (the file is not opened). Currently, the only valid extension is ".desktop".

### \[static\] QString KDesktopFile::locateLocal(const QString &*path*) {#locateLocal}

Returns the appropriate location to use to write changes to the desktop file based on the given `path`.

If the `path` is non-writable (such as /usr/share/applications), this function returns the appropriate equivalent.

If the appropriate location cannot be determined, the writable location will be in [QStandardPaths::GenericDataLocation](https://doc.qt.io/qt-6/qstandardpaths.html#StandardLocation-enum).

For example:

| Path | Writable Location |
| --- | --- |
| /etc/xdg/autostart/myapp.desktop | ~/.config/autostart/myapp.desktop |
| /usr/share/applications/myapp.desktop | ~/.local/share/applications/myapp.desktop |
| ~/Documents/myapp.desktop | ~/.local/share/myapp.desktop |
| myapp.desktop | ~/.local/share/myapp.desktop |

### bool KDesktopFile::noDisplay() const {#noDisplay}

Returns whether the entry should be suppressed in menus.

This handles the "NoDisplay=" key.

### QStringList KDesktopFile::readActions() const {#readActions}

Returns a list of the "Actions=" entries.

### QString KDesktopFile::readComment() const {#readComment}

Returns the value of the "Comment=" entry, or QString() if not specified.

### QString KDesktopFile::readDocPath() const {#readDocPath}

Returns the value of the "X-DocPath=" Or "DocPath=" entry.

### QString KDesktopFile::readGenericName() const {#readGenericName}

Returns the value of the "GenericName=" entry, or QString() if not specified.

### QString KDesktopFile::readIcon() const {#readIcon}

Returns the value of the "Icon=" entry, or QString() if not specified.

### QStringList KDesktopFile::readMimeTypes() const {#readMimeTypes}

Returns a list of the "MimeType=" entries.

### QString KDesktopFile::readName() const {#readName}

Returns the value of the "Name=" entry, or QString() if not specified.

### QString KDesktopFile::readPath() const {#readPath}

Returns the value of the "Path=" entry, or QString() if not specified.

### QString KDesktopFile::readType() const {#readType}

Returns the value of the "Type=" entry, or QString() if not specified.

### QString KDesktopFile::readUrl() const {#readUrl}

Returns the value of the "URL=" entry, or QString() if not specified.

### bool KDesktopFile::tryExec() const {#tryExec}

Returns whether the "TryExec=" field contains a binary that is found on the local system.
