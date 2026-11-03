---
title: "KIO::UDSEntry Class"
description: "Universal Directory Service."
---

# KIO::UDSEntry Class

Universal Directory Service. [More...](#details)

- **Header:** `#include <KIO/UDSEntry>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`

[List of all members, including inherited members](kio-udsentry-members.md)  
[Deprecated members](kio-udsentry-obsolete.md)

## Public Types

- [enum UDSEntry::ItemTypes](#ItemTypes-enum)
- [enum UDSEntry::StandardFieldTypes](#StandardFieldTypes-enum)

## Public Functions

- [UDSEntry()](#UDSEntry)
- [UDSEntry(const struct stat64 &buff, const QString &name = QString())](#UDSEntry-2)
- [UDSEntry(const KIO::UDSEntry &)](#UDSEntry-1)
- [void clear()](#clear)
- [bool contains(uint field) const](#contains)
- [int count() const](#count)
- [void fastInsert(uint field, const QString &value)](#fastInsert)
- [void fastInsert(uint field, long long l)](#fastInsert-1)
- [QList\<uint\> fields() const](#fields)
- [void insert(std::initializer\_list\<std::pair\<uint, const QString &\>\> fieldValuePairs)](#insert) (since 6.29)
- [void insert(std::initializer\_list\<std::pair\<uint, long long\>\> fieldValuePairs)](#insert-1) (since 6.29)
- [bool isDir() const](#isDir)
- [bool isLink() const](#isLink)
- [long long numberValue(uint field, long long defaultValue = 0) const](#numberValue)
- [int numbersCount() const](#numbersCount) (since 6.29)
- [void replace(uint field, const QString &value)](#replace)
- [void replace(uint field, long long l)](#replace-1)
- [void reserve(std::initializer\_list\<uint\> fields)](#reserve-1) (since 6.29)
- [void reserveNumbers(int size)](#reserveNumbers) (since 6.29)
- [void reserveStrings(int size)](#reserveStrings) (since 6.29)
- [QString stringValue(uint field) const](#stringValue)
- [int stringsCount() const](#stringsCount) (since 6.29)

## Detailed Description {#details}

UDS entry is the data structure representing all the fields about a given URL (file or directory).

The [KIO::listDir](kio-listjob.md#listDir)() and KIO:[stat](kio-statjob.md#stat)() operations use this data structure.

KIO defines a number of standard fields, see [UDSEntry::StandardFieldTypes](kio-udsentry.md#StandardFieldTypes-enum) enum.

For instance, to retrieve the display name of the entry, use:

```cpp
QString displayName = entry.stringValue( KIO::UDSEntry::UDS_DISPLAY_NAME );
```

To know the modification time of the file/url in seconds since UNIX epoch, use:

```cpp
QDateTime mtime = QDateTime::fromSecsSinceEpoch(entry.numberValue(KIO::UDSEntry::UDS_MODIFICATION_TIME, 0));
if (mtime.isValid())
    ...
```

If you need higher precision for the modification time, you can also check if [UDS\_MODIFICATION\_TIME\_NS\_OFFSET](kio-udsentry.md#StandardFieldTypes-enum) is supported:

```cpp
if (entry.contains(KIO::UDSEntry::UDS_MODIFICATION_TIME_NS_OFFSET)) {
    long long totalMSecs = (entry.numberValue(KIO::UDSEntry::UDS_MODIFICATION_TIME, 0) * 1000LL)
                          + entry.numberValue(KIO::UDSEntry::UDS_MODIFICATION_TIME_NS_OFFSET, 0) / 1000000LL);

    QDateTime mtime = QDateTime::fromMSecsSinceEpoch(totalMSecs);
```

## Member Type Documentation {#member-type-documentation}

### enum UDSEntry::ItemTypes {#ItemTypes-enum}

Bit field used to specify the item type of a [StandardFieldTypes](kio-udsentry.md#StandardFieldTypes-enum).

| Constant | Value | Description |
| --- | --- | --- |
| `KIO::UDSEntry::UDS_STRING` | `0x01000000` | Indicates that the field is a [QString](https://doc.qt.io/qt-6/qstring.html) |
| `KIO::UDSEntry::UDS_NUMBER` | `0x02000000` | Indicates that the field is a number (long long) |
| `KIO::UDSEntry::UDS_TIME` | `0x04000000 | UDS_NUMBER` | Indicates that the field represents a time, which is modelled by a long long |

### enum UDSEntry::StandardFieldTypes {#StandardFieldTypes-enum}

Constants used to specify the type of a [UDSEntry](kio-udsentry.md)’s field.

| Constant | Value | Description |
| --- | --- | --- |
| `KIO::UDSEntry::UDS_SIZE` | `1 | UDS_NUMBER` | Size of the file |
| `KIO::UDSEntry::UDS_USER` | `3 | UDS_STRING` | User Name of the file owner. Not present on local fs, use UDS\_LOCAL\_USER\_ID |
| `KIO::UDSEntry::UDS_ICON_NAME` | `4 | UDS_STRING` | Name of the icon, that should be used for displaying. It overrides all other detection mechanisms |
| `KIO::UDSEntry::UDS_GROUP` | `5 | UDS_STRING` | Group Name of the file owner. Not present on local fs, use UDS\_LOCAL\_GROUP\_ID |
| `KIO::UDSEntry::UDS_NAME` | `6 | UDS_STRING` | Filename - as displayed in directory listings etc. "." has the usual special meaning of "current directory" UDS\_NAME must always be set and never be empty, neither contain '/'. Note that KIO will append the UDS\_NAME to the url of their parent directory, so all KIO workers must use that naming scheme ("url\_of\_parent/filename" will be the full url of that file). To customize the appearance of files without changing the url of the items, use UDS\_DISPLAY\_NAME. |
| `KIO::UDSEntry::UDS_LOCAL_PATH` | `7 | UDS_STRING` | A local file path if the KIO worker display files sitting on the local filesystem (but in another hierarchy, e.g. settings:/ or remote:/) |
| `KIO::UDSEntry::UDS_HIDDEN` | `8 | UDS_NUMBER` | Treat the file as a hidden file (if set to 1) or as a normal file (if set to 0). This field overrides the default behavior (the check for a leading dot in the filename). |
| `KIO::UDSEntry::UDS_ACCESS` | `9 | UDS_NUMBER` | Access permissions (part of the mode returned by stat) |
| `KIO::UDSEntry::UDS_MODIFICATION_TIME` | `10 | UDS_TIME` | The last time the file was modified. Required time format: seconds since UNIX epoch. |
| `KIO::UDSEntry::UDS_ACCESS_TIME` | `11 | UDS_TIME` | The last time the file was opened. Required time format: seconds since UNIX epoch. |
| `KIO::UDSEntry::UDS_CREATION_TIME` | `12 | UDS_TIME` | The time the file was created. Required time format: seconds since UNIX epoch. |
| `KIO::UDSEntry::UDS_FILE_TYPE` | `13 | UDS_NUMBER` | File type, part of the mode returned by stat (for a link, this returns the file type of the pointed item) check UDS\_LINK\_DEST to know if this is a link |
| `KIO::UDSEntry::UDS_LINK_DEST` | `14 | UDS_STRING` | Name of the file where the link points to. Allows to check for a symlink (don't use S\_ISLNK !) |
| `KIO::UDSEntry::UDS_URL` | `15 | UDS_STRING` | An alternative URL (If different from the caption). Can be used to mix different hierarchies. Use UDS\_DISPLAY\_NAME if you simply want to customize the user-visible filenames, or use UDS\_TARGET\_URL if you want "links" to unrelated urls. |
| `KIO::UDSEntry::UDS_MIME_TYPE` | `16 | UDS_STRING` | A MIME type; the KIO worker should set it if it's known. |
| `KIO::UDSEntry::UDS_GUESSED_MIME_TYPE` | `17 | UDS_STRING` | A MIME type to be used for displaying only. But when 'running' the file, the MIME type is re-determined. This is for special cases like symlinks in FTP; you probably don't want to use this one |
| `KIO::UDSEntry::UDS_XML_PROPERTIES` | `18 | UDS_STRING` | XML properties, e.g. for WebDAV |
| `KIO::UDSEntry::UDS_EXTENDED_ACL` | `19 | UDS_NUMBER` | Indicates that the entry has extended ACL entries |
| `KIO::UDSEntry::UDS_ACL_STRING` | `20 | UDS_STRING` | The access control list serialized into a single string |
| `KIO::UDSEntry::UDS_DEFAULT_ACL_STRING` | `21 | UDS_STRING` | The default access control list serialized into a single string. Only available for directories |
| `KIO::UDSEntry::UDS_DISPLAY_NAME (since Qt 4.1)` | `22 | UDS_STRING` | If set, contains the label to display instead of the 'real name' in UDS\_NAME |
| `KIO::UDSEntry::UDS_TARGET_URL (since Qt 4.1)` | `23 | UDS_STRING` | This file is a shortcut or mount, pointing to an URL in a different hierarchy |
| `KIO::UDSEntry::UDS_DISPLAY_TYPE (since Qt 4.4)` | `24 | UDS_STRING` | User-readable type of file (if not specified, the MIME type's description is used) |
| `KIO::UDSEntry::UDS_ICON_OVERLAY_NAMES (since Qt 4.5)` | `25 | UDS_STRING` | A comma-separated list of supplementary icon overlays which will be added to the list of overlays created by [KFileItem](kfileitem.md). |
| `KIO::UDSEntry::UDS_COMMENT (since Qt 4.6)` | `26 | UDS_STRING` | A comment which will be displayed as is to the user. The string value may contain plain text or Qt-style rich-text extensions. |
| `KIO::UDSEntry::UDS_DEVICE_ID (since Qt 4.7.3)` | `27 | UDS_NUMBER` | Device number for this file, used to detect hardlinks |
| `KIO::UDSEntry::UDS_INODE (since Qt 4.7.3)` | `28 | UDS_NUMBER` | Inode number for this file, used to detect hardlinks |
| `KIO::UDSEntry::UDS_RECURSIVE_SIZE (since Qt 5.70)` | `29 | UDS_NUMBER` | For folders, the recursize size of its content |
| `KIO::UDSEntry::UDS_LOCAL_USER_ID (since Qt 6.0)` | `30 | UDS_NUMBER` | User ID of the file owner |
| `KIO::UDSEntry::UDS_LOCAL_GROUP_ID (since Qt 6.0)` | `31 | UDS_NUMBER` | Group ID of the file owner |
| `KIO::UDSEntry::UDS_SUBVOL_ID (since Qt 6.23)` | `32 | UDS_NUMBER` | subvolume identifier for the filesystem |
| `KIO::UDSEntry::UDS_MOUNT_ID (since Qt 6.23)` | `33 | UDS_NUMBER` | unique mount identifier of the filesystem |
| `KIO::UDSEntry::UDS_MODIFICATION_TIME_NS_OFFSET (since Qt 6.24)` | `34 | UDS_NUMBER` | The offset in nanoseconds to the seconds since the last time the file was modified. This is used to provide higher precision for filesystems that support it. |
| `KIO::UDSEntry::UDS_ACCESS_TIME_NS_OFFSET (since Qt 6.24)` | `35 | UDS_NUMBER` | The offset in nanoseconds to the seconds since the last time the file was accessed. This is used to provide higher precision for filesystems that support it. |
| `KIO::UDSEntry::UDS_CREATION_TIME_NS_OFFSET (since Qt 6.24)` | `36 | UDS_NUMBER` | The offset in nanoseconds to the seconds since the file was created. This is used to provide higher precision for filesystems that support it. |
| `KIO::UDSEntry::UDS_SIZE_ON_DISK (since Qt 6.30)` | `37 | UDS_NUMBER` | The space the file takes up on the storage it lives on, which is what the filesystem has allocated to it rather than how many bytes of data it holds. Larger than UDS\_SIZE for a file whose last block is partly unused, smaller for one that is sparse or compressed, and it counts the space a directory itself takes as well. Absent when the protocol has no way to tell. |
| `KIO::UDSEntry::UDS_EXTRA` | `100 | UDS_STRING` | Extra data (used only if you specified Columns/ColumnsTypes). NB: you cannot repeat this entry; use UDS\_EXTRA + i until UDS\_EXTRA\_END |
| `KIO::UDSEntry::UDS_EXTRA_END` | `140 | UDS_STRING` |   |

## Member Function Documentation {#member-function-documentation}

### UDSEntry::UDSEntry() {#UDSEntry}

### UDSEntry::UDSEntry(const struct stat64 &*buff*, const QString &*name* = QString()) {#UDSEntry-2}

Create a [UDSEntry](kio-udsentry.md) by QT\_STATBUF

`buff` QT\_STATBUF object

`name` filename

### UDSEntry::UDSEntry(*const KIO::UDSEntry &*) {#UDSEntry-1}

Copy constructor

### void UDSEntry::clear() {#clear}

remove all fields

### bool UDSEntry::contains(uint *field*) const {#contains}

check existence of a field

`field` numeric field id

### int UDSEntry::count() const {#count}

The number of fields

### void UDSEntry::fastInsert(uint *field*, const QString &*value*) {#fastInsert}

Insert field with string value, it will assert if the field is already inserted. In that case, use [replace](kio-udsentry.md#replace)() instead. `field` numeric field id `value` to set

### void UDSEntry::fastInsert(uint *field*, long long *l*) {#fastInsert-1}

Insert field with numeric value, it will assert if the field is already inserted. In that case, use [replace](kio-udsentry.md#replace)() instead. `field` numeric field id `l` value to set

### QList\<uint\> UDSEntry::fields() const {#fields}

A vector of fields being present for the current entry.

Returns all fields for the current entry.

### \[since 6.29\] void UDSEntry::insert(std::initializer\_list\<std::pair\<uint, const QString &\>\> *fieldValuePairs*) {#insert}

Insert the values passed as pairs {field, value} in a initializer\_list

This will first pre-allocate the necessary memory in the underlying storage vector.

Example:

```cpp
UDSEntry entry;
entry.insert({{UDS_SIZE, 0}, {UDS_ACCESS, 0}});
```

`fieldValuePairs` the fields and the values to insert

This function was introduced in Qt 6.29.

### \[since 6.29\] void UDSEntry::insert(std::initializer\_list\<std::pair\<uint, long long\>\> *fieldValuePairs*) {#insert-1}

Insert the values passed as pairs {field, value} in a initializer\_list

This will first pre-allocate the necessary memory in the underlying storage vector.

Example:

```cpp
UDSEntry entry;
entry.insert({{UDS_NAME, ""}, {UDS_USER, ""}});
```

`fieldValuePairs` the fields and the values to insert

This function was introduced in Qt 6.29.

### bool UDSEntry::isDir() const {#isDir}

Returns `true` if this entry is a directory (or a link to a directory)

### bool UDSEntry::isLink() const {#isLink}

Returns `true` if this entry is a link

### long long UDSEntry::numberValue(uint *field*, long long *defaultValue* = 0) const {#numberValue}

Returns value of a numeric field

### \[since 6.29\] int UDSEntry::numbersCount() const {#numbersCount}

The number of number fields (including time fields)

This function was introduced in Qt 6.29.

### void UDSEntry::replace(uint *field*, const QString &*value*) {#replace}

Replace or insert field with string value `field` numeric field id `value` to set

### void UDSEntry::replace(uint *field*, long long *l*) {#replace-1}

Replace or insert field with numeric value `field` numeric field id `l` value to set

### \[since 6.29\] void UDSEntry::reserve(std::initializer\_list\<uint\> *fields*) {#reserve-1}

Pre-allocate `fields` fields in the backend storage according to their UDS\_TYPE

Example:

```cpp
UDSEntry entry;
entry.reserve({UDS_SIZE, UDS_ACCESS, UDS_MODIFICATION_TIME, UDS_NAME});
```

`fields` the fields to pre-allocate for

This function was introduced in Qt 6.29.

### \[since 6.29\] void UDSEntry::reserveNumbers(int *size*) {#reserveNumbers}

Calling this function before inserting items into an empty [UDSEntry](kio-udsentry.md) may save time and memory.

`size` number of [UDS\_NUMBER](kio-udsentry.md#ItemTypes-enum) fields for which memory will be pre-allocated

This function was introduced in Qt 6.29.

*See also* [reserveStrings](kio-udsentry.md#reserveStrings)()

### \[since 6.29\] void UDSEntry::reserveStrings(int *size*) {#reserveStrings}

Calling this function before inserting items into an empty [UDSEntry](kio-udsentry.md) may save time and memory.

`size` number of [UDS\_STRING](kio-udsentry.md#ItemTypes-enum) fields for which memory will be pre-allocated

This function was introduced in Qt 6.29.

*See also* [reserveNumbers](kio-udsentry.md#reserveNumbers)()

### QString UDSEntry::stringValue(uint *field*) const {#stringValue}

Returns value of a textual field

### \[since 6.29\] int UDSEntry::stringsCount() const {#stringsCount}

The number of string fields

This function was introduced in Qt 6.29.

## Related Non-Members {#related-non-members}

### UDSEntryList {#UDSEntryList-typedef}

A directory listing is a list of [UDSEntry](kio-udsentry.md) instances.

To list the name and size of all the files in a directory listing you would do:

```cpp
KIO::UDSEntryList::ConstIterator it = entries.begin();
const KIO::UDSEntryList::ConstIterator end = entries.end();
for (; it != end; ++it) {
  const KIO::UDSEntry& entry = *it;
  QString name = entry.stringValue( KIO::UDSEntry::UDS_NAME );
  bool isDir = entry.isDir();
  KIO::filesize_t size = entry.numberValue( KIO::UDSEntry::UDS_SIZE, -1 );
  ...
}
```
