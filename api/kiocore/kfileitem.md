---
title: "KFileItem Class"
description: "A KFileItem is a generic class to handle a file, local or remote."
---

# KFileItem Class

A [KFileItem](kfileitem.md) is a generic class to handle a file, local or remote. [More...](#details)

- **Header:** `#include <KFileItem>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`

[List of all members, including inherited members](kfileitem-members.md)

## Public Types

- [enum KFileItem::FileTimes](#FileTimes-enum)
- [enum KFileItem::MimeTypeDetermination](#MimeTypeDetermination-enum)

## Properties

- [\[read-only\] comment : QString](#comment-prop)
- [\[read-only\] currentMimeType : QMimeType](#currentMimeType-prop)
- [\[read-only\] determineMimeType : QMimeType](#determineMimeType-prop)
- [\[read-only\] getStatusBarInfo : QString](#getStatusBarInfo-prop)
- [\[read-only\] group : QString](#group-prop)
- [\[read-only\] iconName : QString](#iconName-prop)
- [\[read-only\] isDesktopFile : bool](#isDesktopFile-prop)
- [\[read-only\] isDir : bool](#isDir-prop)
- [\[read-only\] isFile : bool](#isFile-prop)
- [\[read-only\] isFinalIconKnown : bool](#isFinalIconKnown-prop)
- [\[read-only\] isHidden : bool](#isHidden-prop)
- [\[read-only\] isLink : bool](#isLink-prop)
- [\[read-only\] isLocalFile : bool](#isLocalFile-prop)
- [\[read-only\] isMimeTypeKnown : bool](#isMimeTypeKnown-prop)
- [\[read-only\] isReadable : bool](#isReadable-prop)
- [\[read-only\] isRegularFile : bool](#isRegularFile-prop)
- [\[read-only\] isSlow : bool](#isSlow-prop)
- [\[read-only\] isWritable : bool](#isWritable-prop)
- [\[read-only\] linkDest : QString](#linkDest-prop)
- [localPath : QString](#localPath-prop)
- [\[read-only\] mimeComment : QString](#mimeComment-prop)
- [\[read-only\] mimetype : QString](#mimetype-prop)
- [name : QString](#name-prop)
- [\[read-only\] overlays : QStringList](#overlays-prop)
- [\[read-only\] targetUrl : QUrl](#targetUrl-prop)
- [\[read-only\] text : QString](#text-prop)
- [url : QUrl](#url-prop)
- [\[read-only\] user : QString](#user-prop)

## Public Functions

- [KFileItem()](#KFileItem)
- [KFileItem(const QUrl &url, KFileItem::MimeTypeDetermination mimeTypeDetermination)](#KFileItem-2)
- [KFileItem(const QUrl &url, const QString &mimeType = QString(), mode\_t mode = KFileItem::Unknown)](#KFileItem-3)
- [KFileItem(const KIO::UDSEntry &entry, const QUrl &itemOrDirUrl, bool delayedMimeTypes = false, bool urlIsDirectory = false)](#KFileItem-4)
- [KFileItem(const KFileItem &)](#KFileItem-1)
- [KACL ACL() const](#ACL)
- [bool cmp(const KFileItem &item) const](#cmp)
- [QString comment() const](#comment)
- [QMimeType currentMimeType() const](#currentMimeType)
- [KACL defaultACL() const](#defaultACL)
- [QMimeType determineMimeType() const](#determineMimeType)
- [KIO::UDSEntry entry() const](#entry)
- [bool exists() const](#exists) (since 6.0)
- [QString getStatusBarInfo() const](#getStatusBarInfo)
- [QString group() const](#group)
- [int groupId() const](#groupId) (since 6.0)
- [bool hasExtendedACL() const](#hasExtendedACL)
- [QString iconName() const](#iconName)
- [bool isDesktopFile() const](#isDesktopFile)
- [bool isDir() const](#isDir)
- [bool isExecutable() const](#isExecutable) (since 6.0)
- [bool isFile() const](#isFile)
- [bool isFinalIconKnown() const](#isFinalIconKnown)
- [bool isHidden() const](#isHidden)
- [bool isLink() const](#isLink)
- [bool isLocalFile() const](#isLocalFile)
- [bool isMimeTypeKnown() const](#isMimeTypeKnown)
- [KFileItem::MostLocalUrlResult isMostLocalUrl() const](#isMostLocalUrl)
- [bool isNull() const](#isNull)
- [bool isReadable() const](#isReadable)
- [bool isRegularFile() const](#isRegularFile)
- [bool isSlow() const](#isSlow)
- [bool isWritable() const](#isWritable)
- [QString linkDest() const](#linkDest)
- [QString localPath() const](#localPath)
- [QString mimeComment() const](#mimeComment)
- [QString mimetype() const](#mimetype)
- [mode\_t mode() const](#mode)
- [QUrl mostLocalUrl(bool \*local = nullptr) const](#mostLocalUrl)
- [QString name(bool lowerCase = false) const](#name)
- [QStringList overlays() const](#overlays)
- [mode\_t permissions() const](#permissions)
- [QString permissionsString() const](#permissionsString)
- [KIO::filesize\_t recursiveSize() const](#recursiveSize)
- [void refresh()](#refresh)
- [void refreshMimeType()](#refreshMimeType)
- [void setDelayedMimeTypes(bool b)](#setDelayedMimeTypes)
- [void setLocalPath(const QString &path)](#setLocalPath)
- [void setName(const QString &name)](#setName)
- [void setUrl(const QUrl &url)](#setUrl)
- [KIO::filesize\_t size() const](#size)
- [QString suffix() const](#suffix) (since 6.0)
- [QUrl targetUrl() const](#targetUrl)
- [QString text() const](#text)
- [QDateTime time(KFileItem::FileTimes which) const](#time)
- [QString timeString(KFileItem::FileTimes which = ModificationTime) const](#timeString)
- [QUrl url() const](#url)
- [QString user() const](#user)
- [int userId() const](#userId) (since 6.0)
- [KFileItem::operator QVariant() const](#operator-QVariant)
- [bool KFileItem::operator!=(const KFileItem &other) const](#operator-not-eq)
- [bool KFileItem::operator\<(const KFileItem &other) const](#operator-lt)
- [bool KFileItem::operator\<(const QUrl &other) const](#operator-lt-1)
- [bool KFileItem::operator==(const KFileItem &other) const](#operator-eq-eq)

## Detailed Description {#details}

In particular, it makes it easier to handle the result of [KIO::listDir](kio-listjob.md#listDir) (UDSEntry isn't very friendly to use). It includes many file attributes such as MIME type, icon, text, mode, link...

[KFileItem](kfileitem.md) is implicitly shared, i.e. it can be used as a value and copied around at almost no cost.

## Member Type Documentation {#member-type-documentation}

### enum KFileItem::FileTimes {#FileTimes-enum}

The timestamps associated with a file.

| Constant | Value | Description |
| --- | --- | --- |
| `KFileItem::ModificationTime` | `0` | The time the file's contents were last modified |
| `KFileItem::AccessTime` | `1` | The time the file was last accessed (last read or written to) |
| `KFileItem::CreationTime` | `2` | The time the file was created |

### enum KFileItem::MimeTypeDetermination {#MimeTypeDetermination-enum}

| Constant |   |
| --- | --- |
| `KFileItem::NormalMimeTypeDetermination` | `0` |
| `KFileItem::SkipMimeTypeFromContent` | `1` |

## Property Documentation {#property-documentation}

### \[read-only\] comment : QString {#comment-prop}

**Access functions:**

- `QString` **[comment](kfileitem.md#comment)**() const

### \[read-only\] currentMimeType : QMimeType {#currentMimeType-prop}

**Access functions:**

- `QMimeType` **[currentMimeType](kfileitem.md#currentMimeType)**() const

### \[read-only\] determineMimeType : QMimeType {#determineMimeType-prop}

**Access functions:**

- `QMimeType` **[determineMimeType](kfileitem.md#determineMimeType)**() const

### \[read-only\] getStatusBarInfo : QString {#getStatusBarInfo-prop}

**Access functions:**

- `QString` **[getStatusBarInfo](kfileitem.md#getStatusBarInfo)**() const

### \[read-only\] group : QString {#group-prop}

**Access functions:**

- `QString` **[group](kfileitem.md#group)**() const

### \[read-only\] iconName : QString {#iconName-prop}

**Access functions:**

- `QString` **[iconName](kfileitem.md#iconName)**() const

### \[read-only\] isDesktopFile : bool {#isDesktopFile-prop}

**Access functions:**

- `bool` **[isDesktopFile](kfileitem.md#isDesktopFile)**() const

### \[read-only\] isDir : bool {#isDir-prop}

**Access functions:**

- `bool` **[isDir](kfileitem.md#isDir)**() const

### \[read-only\] isFile : bool {#isFile-prop}

**Access functions:**

- `bool` **[isFile](kfileitem.md#isFile)**() const

### \[read-only\] isFinalIconKnown : bool {#isFinalIconKnown-prop}

**Access functions:**

- `bool` **[isFinalIconKnown](kfileitem.md#isFinalIconKnown)**() const

### \[read-only\] isHidden : bool {#isHidden-prop}

**Access functions:**

- `bool` **[isHidden](kfileitem.md#isHidden)**() const

### \[read-only\] isLink : bool {#isLink-prop}

**Access functions:**

- `bool` **[isLink](kfileitem.md#isLink)**() const

### \[read-only\] isLocalFile : bool {#isLocalFile-prop}

**Access functions:**

- `bool` **[isLocalFile](kfileitem.md#isLocalFile)**() const

### \[read-only\] isMimeTypeKnown : bool {#isMimeTypeKnown-prop}

**Access functions:**

- `bool` **[isMimeTypeKnown](kfileitem.md#isMimeTypeKnown)**() const

### \[read-only\] isReadable : bool {#isReadable-prop}

**Access functions:**

- `bool` **[isReadable](kfileitem.md#isReadable)**() const

### \[read-only\] isRegularFile : bool {#isRegularFile-prop}

**Access functions:**

- `bool` **[isRegularFile](kfileitem.md#isRegularFile)**() const

### \[read-only\] isSlow : bool {#isSlow-prop}

**Access functions:**

- `bool` **[isSlow](kfileitem.md#isSlow)**() const

### \[read-only\] isWritable : bool {#isWritable-prop}

**Access functions:**

- `bool` **[isWritable](kfileitem.md#isWritable)**() const

### \[read-only\] linkDest : QString {#linkDest-prop}

**Access functions:**

- `QString` **[linkDest](kfileitem.md#linkDest)**() const

### localPath : QString {#localPath-prop}

**Access functions:**

- `QString` **[localPath](kfileitem.md#localPath)**() const
- `void` **[setLocalPath](kfileitem.md#setLocalPath)**(const `QString` &*path*)

### \[read-only\] mimeComment : QString {#mimeComment-prop}

**Access functions:**

- `QString` **[mimeComment](kfileitem.md#mimeComment)**() const

### \[read-only\] mimetype : QString {#mimetype-prop}

**Access functions:**

- `QString` **[mimetype](kfileitem.md#mimetype)**() const

### name : QString {#name-prop}

**Access functions:**

- `QString` **[name](kfileitem.md#name)**(`bool` *lowerCase* = false) const
- `void` **[setName](kfileitem.md#setName)**(const `QString` &*name*)

### \[read-only\] overlays : QStringList {#overlays-prop}

**Access functions:**

- `QStringList` **[overlays](kfileitem.md#overlays)**() const

### \[read-only\] targetUrl : QUrl {#targetUrl-prop}

**Access functions:**

- `QUrl` **[targetUrl](kfileitem.md#targetUrl)**() const

### \[read-only\] text : QString {#text-prop}

**Access functions:**

- `QString` **[text](kfileitem.md#text)**() const

### url : QUrl {#url-prop}

**Access functions:**

- `QUrl` **[url](kfileitem.md#url)**() const
- `void` **[setUrl](kfileitem.md#setUrl)**(const `QUrl` &*url*)

### \[read-only\] user : QString {#user-prop}

**Access functions:**

- `QString` **[user](kfileitem.md#user)**() const

## Member Function Documentation {#member-function-documentation}

### KFileItem::KFileItem() {#KFileItem}

Null [KFileItem](kfileitem.md). Doesn't represent any file, only exists for convenience.

### KFileItem::KFileItem(const QUrl &*url*, KFileItem::MimeTypeDetermination *mimeTypeDetermination*) {#KFileItem-2}

Creates an item representing a file, with the option of skipping MIME type determination.

`url` the file url

`mimeTypeDetermination` the mode of determining the MIME type:

- [NormalMimeTypeDetermination](kfileitem.md#MimeTypeDetermination-enum): By content if local file, i.e. access the file, open and read part of it; by [QMimeDatabase::MatchMode::MatchExtension](https://doc.qt.io/qt-6/qmimedatabase.html#MatchMode-enum) if not local.
- [SkipMimeTypeFromContent](kfileitem.md#MimeTypeDetermination-enum): Always by [QMimeDatabase::MatchMode::MatchExtension](https://doc.qt.io/qt-6/qmimedatabase.html#MatchMode-enum), i.e. won't access the file by stat() or opening it; only suitable for files, directories won't be recognized.

### \[explicit\] KFileItem::KFileItem(const QUrl &*url*, const QString &*mimeType* = QString(), mode\_t *mode* = KFileItem::Unknown) {#KFileItem-3}

Creates an item representing a file, for which the MIME type is already known.

`url` the file url

`mimeType` the name of the file's MIME type

`mode` the mode (S\_IFDIR...)

### KFileItem::KFileItem(const KIO::UDSEntry &*entry*, const QUrl &*itemOrDirUrl*, bool *delayedMimeTypes* = false, bool *urlIsDirectory* = false) {#KFileItem-4}

Creates an item representing a file, from a UDSEntry. This is the preferred constructor when using [KIO::listDir](kio-listjob.md#listDir)().

`entry` the KIO entry used to get the file, contains info about it

`itemOrDirUrl` the URL of the item or of the directory containing this item (see urlIsDirectory).

`delayedMimeTypes` specifies if the MIME type of the given URL should be determined immediately or on demand. See the bool delayedMimeTypes in the [KDirLister](../kiowidgets/kdirlister.md) constructor.

`urlIsDirectory` specifies if the url is just the directory of the fileitem and the filename from the UDSEntry should be used.

When creating KFileItems out of the UDSEntry emitted by a KIO list job, use [KFileItem](kfileitem.md)(entry, listjob-\>[url](kfileitem.md#url)(), delayedMimeTypes, true);

### KFileItem::KFileItem(*const KFileItem &*) {#KFileItem-1}

Copy constructor

### KACL KFileItem::ACL() const {#ACL}

Returns the access control list for the file.

### bool KFileItem::cmp(const KFileItem &*item*) const {#cmp}

Somewhat like a comparison operator, but more explicit, and it can detect that two fileitems differ if any property of the file item has changed (file size, modification date, etc.). Two items are equal if all properties are equal. In contrast, operator== only compares URLs.

`item` the item to compare

Returns `true` if all values are equal

### QString KFileItem::comment() const {#comment}

A comment which can contain anything - even rich text. It will simply be displayed to the user as is.

> **Note:** Getter function for property [comment](kfileitem.md#comment-prop).

### QMimeType KFileItem::currentMimeType() const {#currentMimeType}

Returns the currently known MIME type of the file item. This will not try to determine the MIME type if unknown.

> **Note:** Getter function for property [currentMimeType](kfileitem.md#currentMimeType-prop).

### KACL KFileItem::defaultACL() const {#defaultACL}

Returns the default access control list for the directory.

### QMimeType KFileItem::determineMimeType() const {#determineMimeType}

Returns the MIME type of the file item.

If delayedMimeTypes was used in the constructor, this will determine the MIME type first.

> **Note:** Getter function for property [determineMimeType](kfileitem.md#determineMimeType-prop).

### KIO::UDSEntry KFileItem::entry() const {#entry}

Returns the UDS entry. Used by the tree view to access all details by position.

### \[since 6.0\] bool KFileItem::exists() const {#exists}

Returns whether the [KFileItem](kfileitem.md) exists on-disk

Call only after initialization (i.e \`[KIO::stat](kio-statjob.md#stat)\` or \`[refresh](kfileitem.md#refresh)()\` for local files)

This function was introduced in Qt 6.0.

### QString KFileItem::getStatusBarInfo() const {#getStatusBarInfo}

Returns the string to be displayed in the statusbar, e.g. when the mouse is over this item.

> **Note:** Getter function for property [getStatusBarInfo](kfileitem.md#getStatusBarInfo-prop).

### QString KFileItem::group() const {#group}

Returns the group of the file.

> **Note:** Getter function for property [group](kfileitem.md#group-prop).

### \[since 6.0\] int KFileItem::groupId() const {#groupId}

Returns the file's owner's group id. Available only on supported protocols.

This function was introduced in Qt 6.0.

### bool KFileItem::hasExtendedACL() const {#hasExtendedACL}

Tells if the file has extended access level information ( Posix ACL )

### QString KFileItem::iconName() const {#iconName}

Returns the full path name to the icon that represents this MIME type.

> **Note:** Getter function for property [iconName](kfileitem.md#iconName-prop).

### bool KFileItem::isDesktopFile() const {#isDesktopFile}

Checks whether the file is a readable local .desktop file, i.e. a file whose path can be given to [KDesktopFile](../kconfigcore/kdesktopfile.md)

Returns `true` if the file is a desktop file.

> **Note:** Getter function for property [isDesktopFile](kfileitem.md#isDesktopFile-prop).

### bool KFileItem::isDir() const {#isDir}

Returns `true` if this item represents a directory.

> **Note:** Getter function for property [isDir](kfileitem.md#isDir-prop).

### \[since 6.0\] bool KFileItem::isExecutable() const {#isExecutable}

Returns `true` if the file has executable permission

This function was introduced in Qt 6.0.

### bool KFileItem::isFile() const {#isFile}

Returns `true` if this item represents a file (and not a directory)

> **Note:** Getter function for property [isFile](kfileitem.md#isFile-prop).

### bool KFileItem::isFinalIconKnown() const {#isFinalIconKnown}

Returns `true` if we have determined the final icon of this file already.

> **Note:** Getter function for property [isFinalIconKnown](kfileitem.md#isFinalIconKnown-prop).

### bool KFileItem::isHidden() const {#isHidden}

Checks whether the file is hidden.

Returns `true` if the file is hidden.

> **Note:** Getter function for property [isHidden](kfileitem.md#isHidden-prop).

### bool KFileItem::isLink() const {#isLink}

Returns `true` if this item represents a link in the UNIX sense of a link.

> **Note:** Getter function for property [isLink](kfileitem.md#isLink-prop).

### bool KFileItem::isLocalFile() const {#isLocalFile}

Returns `true` if the file is a local file.

> **Note:** Getter function for property [isLocalFile](kfileitem.md#isLocalFile-prop).

### bool KFileItem::isMimeTypeKnown() const {#isMimeTypeKnown}

Returns `true` if we have determined the MIME type of this file already, i.e. if [determineMimeType](kfileitem.md#determineMimeType)() will be fast. Otherwise it will have to find what the MIME type is, which is a possibly slow operation; usually this is delayed until necessary.

> **Note:** Getter function for property [isMimeTypeKnown](kfileitem.md#isMimeTypeKnown-prop).

### KFileItem::MostLocalUrlResult KFileItem::isMostLocalUrl() const {#isMostLocalUrl}

Returns a MostLocalUrlResult, with the local Url for this item if possible (otherwise the item url), and a bool that is set to `true` if this Url does represent a local file otherwise `false`.

Basically this is an alternative to [mostLocalUrl](kfileitem.md#mostLocalUrl)(bool\*), that does not use an output parameter.

Example:

```cpp
KFileItem item;
const MostLocalUrlResult result = item.isMostLocalUrl();
if (result.local) { // A local file
   // Use result.url
}
```

### bool KFileItem::isNull() const {#isNull}

Returns `true` if default-constructed

### bool KFileItem::isReadable() const {#isReadable}

Checks whether the file or directory is readable. In some cases (remote files), we may return `true` even though it can't be read.

Returns `true` if the file can be read - more precisely, false if we know for sure it can't

> **Note:** Getter function for property [isReadable](kfileitem.md#isReadable-prop).

### bool KFileItem::isRegularFile() const {#isRegularFile}

Return `true` if this item is a regular file, `false` otherwise (directory, link, character/block device, fifo, socket)

> **Note:** Getter function for property [isRegularFile](kfileitem.md#isRegularFile-prop).

### bool KFileItem::isSlow() const {#isSlow}

Returns `true` if the file is a remote URL, or a local file on a network mount. It will return `false` only for really-local file systems.

> **Note:** Getter function for property [isSlow](kfileitem.md#isSlow-prop).

### bool KFileItem::isWritable() const {#isWritable}

Checks whether the file or directory is writable. In some cases (remote files), we may return `true` even though it can't be written to.

Returns `true` if the file or directory can be written to - more precisely, false if we know for sure it can't

> **Note:** Getter function for property [isWritable](kfileitem.md#isWritable-prop).

### QString KFileItem::linkDest() const {#linkDest}

Returns the link destination if [isLink](kfileitem.md#isLink)() == true, or QString() if the item is not a link

> **Note:** Getter function for property [linkDest](kfileitem.md#linkDest-prop).

### QString KFileItem::localPath() const {#localPath}

Returns the local path if [isLocalFile](kfileitem.md#isLocalFile)() == true or the KIO item has a UDS\_LOCAL\_PATH atom.

Treat it as a readonly path to open/list contents, use original url to move/delete files.

Returns the item local path, or QString() if not known

> **Note:** Getter function for property [localPath](kfileitem.md#localPath-prop).

*See also* [setLocalPath](kfileitem.md#setLocalPath)()

### QString KFileItem::mimeComment() const {#mimeComment}

Returns the user-readable string representing the type of this file, like "OpenDocument Text File".

> **Note:** Getter function for property [mimeComment](kfileitem.md#mimeComment-prop).

### QString KFileItem::mimetype() const {#mimetype}

Returns the MIME type of the file item.

If `delayedMimeTypes` was used in the constructor, this will determine the MIME type first. Equivalent to [determineMimeType](kfileitem.md#determineMimeType)()-\>[name](kfileitem.md#name)()

> **Note:** Getter function for property [mimetype](kfileitem.md#mimetype-prop).

### mode\_t KFileItem::mode() const {#mode}

Returns the file type (stat.st\_mode containing only S\_IFDIR, S\_IFLNK, ...).

### QUrl KFileItem::mostLocalUrl(bool \**local* = nullptr) const {#mostLocalUrl}

Tries to return a local URL for this file item if possible.

If `local` is not null, it will be set to `true` if the returned url is local, `false` otherwise.

Example:

```cpp
bool isLocal = false;
KFileItem item;
const QUrl url = item.mostLocalUrl(&isLocal);
if (isLocal) {
   // Use url
}
```

### QString KFileItem::name(bool *lowerCase* = false) const {#name}

Return the name of the file item (without a path).

Similar to [text](kfileitem.md#text)(), but unencoded, i.e. the original name.

`lowerCase` if true, the name will be returned in lower case, which is useful to speed up sorting by name, case insensitively.

Returns the file's name

> **Note:** Getter function for property [name](kfileitem.md#name-prop).

*See also* [setName](kfileitem.md#setName)()

### QStringList KFileItem::overlays() const {#overlays}

Returns the overlays (bitfield of KIconLoader::\*Overlay flags) that are used for this item's pixmap. Overlays are used to show for example, whether a file can be modified.

> **Note:** Getter function for property [overlays](kfileitem.md#overlays-prop).

### mode\_t KFileItem::permissions() const {#permissions}

Returns the permissions of the file (stat.st\_mode containing only permissions).

### QString KFileItem::permissionsString() const {#permissionsString}

Returns the access permissions for the file as a string.

### KIO::filesize\_t KFileItem::recursiveSize() const {#recursiveSize}

For folders, returns its recursive size: the size of its files plus the recursiveSize of its folder

Initially only implemented for trash:/

### void KFileItem::refresh() {#refresh}

Throw away and re-read (for local files) all information about the file. This is called when the \_file\_ changes.

### void KFileItem::refreshMimeType() {#refreshMimeType}

Re-reads MIME type information. This is called when the MIME type database changes.

### void KFileItem::setDelayedMimeTypes(bool *b*) {#setDelayedMimeTypes}

Sets MIME type determination to be immediate or on demand. Call this after the constructor, and before using any MIME-type-related method. 5.0

### void KFileItem::setLocalPath(const QString &*path*) {#setLocalPath}

Sets the item's local path (UDS\_LOCAL\_PATH). Do not call unless you know what you are doing! This won't change the item's name or URL. (used for example when an item got renamed).

`path` the item's local path

> **Note:** Setter function for property [localPath](kfileitem.md#localPath-prop).

*See also* [localPath](kfileitem.md#localPath)()

### void KFileItem::setName(const QString &*name*) {#setName}

Sets the item's name (i.e. the filename). This is automatically done by [setUrl](kfileitem.md#setUrl), to set the name from the URL's fileName(). This method is provided for some special cases like relative paths as names (KFindPart)

`name` the item's name

> **Note:** Setter function for property [name](kfileitem.md#name-prop).

*See also* [name](kfileitem.md#name)()

### void KFileItem::setUrl(const QUrl &*url*) {#setUrl}

Sets the item's URL. Do not call unless you know what you are doing! (used for example when an item got renamed).

`url` the item's URL

> **Note:** Setter function for property [url](kfileitem.md#url-prop).

*See also* [url](kfileitem.md#url)()

### KIO::filesize\_t KFileItem::size() const {#size}

Returns the size of the file, if known.

Returns 0 otherwise.

### \[since 6.0\] QString KFileItem::suffix() const {#suffix}

Returns the file extension

Similar to [QFileInfo::suffix](https://doc.qt.io/qt-6/qfileinfo.html#suffix) except it takes into account UDS\_DISPLAY\_NAME and saves a stat call

This function was introduced in Qt 6.0.

### QUrl KFileItem::targetUrl() const {#targetUrl}

Returns the target url of the file, which is the same as [url](kfileitem.md#url)() in cases where the worker doesn't specify UDS\_TARGET\_URL

> **Note:** Getter function for property [targetUrl](kfileitem.md#targetUrl-prop).

### QString KFileItem::text() const {#text}

Returns the text of the file item.

It's not exactly the filename since some decoding happens ('%2F'-\>'/').

> **Note:** Getter function for property [text](kfileitem.md#text-prop).

### \[invokable\] QDateTime KFileItem::time(KFileItem::FileTimes *which*) const {#time}

Requests the modification, access or creation time, depending on `which`.

`which` the timestamp

Returns the time asked for, QDateTime() if not available

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [timeString](kfileitem.md#timeString)()

### \[invokable\] QString KFileItem::timeString(KFileItem::FileTimes *which* = ModificationTime) const {#timeString}

Requests the modification, access or creation time as a string, depending on `which`.

`which` the timestamp

Returns a formatted string of the requested time.

> **Note:** This function can be invoked via the meta-object system and from QML. See Q\_INVOKABLE.

*See also* [time](kfileitem.md#time)()

### QUrl KFileItem::url() const {#url}

Returns the url of the file.

> **Note:** Getter function for property [url](kfileitem.md#url-prop).

*See also* [setUrl](kfileitem.md#setUrl)()

### QString KFileItem::user() const {#user}

Returns the owner of the file.

> **Note:** Getter function for property [user](kfileitem.md#user-prop).

### \[since 6.0\] int KFileItem::userId() const {#userId}

Returns the file's owner's user id. Available only on supported protocols.

This function was introduced in Qt 6.0.

### KFileItem::operator QVariant() const {#operator-QVariant}

Converts this [KFileItem](kfileitem.md) to a [QVariant](https://doc.qt.io/qt-6/qvariant.html), this allows to use [KFileItem](kfileitem.md) in QVariant() constructor

### bool KFileItem::operator!=(const KFileItem &*other*) const {#operator-not-eq}

Returns `true` if both items do not share the same URL.

### bool KFileItem::operator\<(const KFileItem &*other*) const {#operator-lt}

Returns `true` if this item's URL is lexically less than other's URL; otherwise returns `false`

### bool KFileItem::operator\<(const QUrl &*other*) const {#operator-lt-1}

Returns `true` if this item's URL is lexically less than url other; otherwise returns `false`

### bool KFileItem::operator==(const KFileItem &*other*) const {#operator-eq-eq}

Returns `true` if both items share the same URL.
