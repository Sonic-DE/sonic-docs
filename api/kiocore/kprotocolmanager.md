---
title: "KProtocolManager Class"
description: "Provides information about I/O (Internet, etc.) settings chosen/set by the end user."
---

# KProtocolManager Class

Provides information about I/O (Internet, etc.) settings chosen/set by the end user. [More...](#details)

- **Header:** `#include <KProtocolManager>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`

[List of all members, including inherited members](kprotocolmanager-members.md)  
[Deprecated members](kprotocolmanager-obsolete.md)

## Static Public Members

- [bool autoResume()](#autoResume)
- [bool canCopyFromFile(const QUrl &url)](#canCopyFromFile)
- [bool canCopyToFile(const QUrl &url)](#canCopyToFile)
- [bool canDeleteRecursive(const QUrl &url)](#canDeleteRecursive)
- [bool canRenameFromFile(const QUrl &url)](#canRenameFromFile)
- [bool canRenameToFile(const QUrl &url)](#canRenameToFile)
- [QString charsetFor(const QUrl &url)](#charsetFor)
- [QString defaultMimetype(const QUrl &url)](#defaultMimetype)
- [KProtocolInfo::FileNameUsedForCopying fileNameUsedForCopying(const QUrl &url)](#fileNameUsedForCopying)
- [KProtocolInfo::Type inputType(const QUrl &url)](#inputType)
- [bool isSourceProtocol(const QUrl &url)](#isSourceProtocol)
- [QStringList listing(const QUrl &url)](#listing)
- [bool markPartial()](#markPartial)
- [KProtocolInfo::Type outputType(const QUrl &url)](#outputType)
- [QString protocolForArchiveMimetype(const QString &mimeType)](#protocolForArchiveMimetype)
- [void reparseConfiguration()](#reparseConfiguration)
- [bool supportsDeleting(const QUrl &url)](#supportsDeleting)
- [bool supportsLinking(const QUrl &url)](#supportsLinking)
- [bool supportsListing(const QUrl &url)](#supportsListing)
- [bool supportsMakeDir(const QUrl &url)](#supportsMakeDir)
- [bool supportsMoving(const QUrl &url)](#supportsMoving)
- [bool supportsOpening(const QUrl &url)](#supportsOpening)
- [bool supportsPermissions(const QUrl &url)](#supportsPermissions)
- [bool supportsReading(const QUrl &url)](#supportsReading)
- [bool supportsTruncating(const QUrl &url)](#supportsTruncating)
- [bool supportsWriting(const QUrl &url)](#supportsWriting)

## Detailed Description {#details}

[KProtocolManager](kprotocolmanager.md) has a heap of static functions that allows only read access to KDE's IO related settings. These include proxy, cache, file transfer resumption, timeout and user-agent related settings.

The information provided by this class is generic enough to be applicable to any application that makes use of KDE's IO sub-system. Note that this mean the proxy, timeout etc. settings are saved in a separate user-specific config file and not in the config file of the application.

## Member Function Documentation {#member-function-documentation}

### \[static\] bool KProtocolManager::autoResume() {#autoResume}

Returns `true` if partial downloads should be automatically resumed.

### \[static\] bool KProtocolManager::canCopyFromFile(const QUrl &*url*) {#canCopyFromFile}

Returns whether the protocol can copy files/objects directly from the filesystem itself. If not, the application will read files from the filesystem using the file-protocol and pass the data on to the destination protocol.

This corresponds to the "copyFromFile=" field in the protocol description file. Valid values for this field are "true" or "false" (default).

`url` the url to check

### \[static\] bool KProtocolManager::canCopyToFile(const QUrl &*url*) {#canCopyToFile}

Returns whether the protocol can copy files/objects directly to the filesystem itself. If not, the application will receive the data from the source protocol and store it in the filesystem using the file-protocol.

This corresponds to the "copyToFile=" field in the protocol description file. Valid values for this field are "true" or "false" (default).

`url` the url to check

### \[static\] bool KProtocolManager::canDeleteRecursive(const QUrl &*url*) {#canDeleteRecursive}

Returns whether the protocol can recursively delete directories by itself. If not (the usual case) then KIO will list the directory and delete files and empty directories one by one.

This corresponds to the "deleteRecursive=" field in the protocol description file. Valid values for this field are "true" or "false" (default).

`url` the url to check

### \[static\] bool KProtocolManager::canRenameFromFile(const QUrl &*url*) {#canRenameFromFile}

Returns whether the protocol can rename (i.e. move fast) files/objects directly from the filesystem itself. If not, the application will read files from the filesystem using the file-protocol and pass the data on to the destination protocol.

This corresponds to the "renameFromFile=" field in the protocol description file. Valid values for this field are "true" or "false" (default).

`url` the url to check

### \[static\] bool KProtocolManager::canRenameToFile(const QUrl &*url*) {#canRenameToFile}

Returns whether the protocol can rename (i.e. move fast) files/objects directly to the filesystem itself. If not, the application will receive the data from the source protocol and store it in the filesystem using the file-protocol.

This corresponds to the "renameToFile=" field in the protocol description file. Valid values for this field are "true" or "false" (default).

`url` the url to check

### \[static\] QString KProtocolManager::charsetFor(const QUrl &*url*) {#charsetFor}

Returns the charset to use for the specified `url`.

### \[static\] QString KProtocolManager::defaultMimetype(const QUrl &*url*) {#defaultMimetype}

Returns default MIME type for this URL based on the protocol.

This corresponds to the "defaultMimetype=" field in the protocol description file.

`url` the url to check

### \[static\] KProtocolInfo::FileNameUsedForCopying KProtocolManager::fileNameUsedForCopying(const QUrl &*url*) {#fileNameUsedForCopying}

This setting defines the strategy to use for generating a filename, when copying a file or directory to another directory. By default the destination filename is made out of the filename in the source URL. However if the KIO worker displays names that are different from the filename of the URL (e.g. kio\_fonts shows Arial for arial.ttf, or kio\_trash shows foo.txt and uses some internal URL), using Name means that the display name (UDS\_NAME) will be used to as the filename in the destination directory.

This corresponds to the "fileNameUsedForCopying=" field in the protocol description file. Valid values for this field are "Name" or "FromURL" (default).

`url` the url to check

### \[static\] KProtocolInfo::Type KProtocolManager::inputType(const QUrl &*url*) {#inputType}

Returns whether the protocol should be treated as a filesystem or as a stream when reading from it.

This corresponds to the "input=" field in the protocol description file. Valid values for this field are "filesystem", "stream" or "none" (default).

`url` the url to check

### \[static\] bool KProtocolManager::isSourceProtocol(const QUrl &*url*) {#isSourceProtocol}

Returns whether the protocol can act as a source protocol.

A source protocol retrieves data from or stores data to the location specified by a URL. A source protocol is the opposite of a filter protocol.

The "source=" field in the protocol description file determines whether a protocol is a source protocol or a filter protocol.

`url` the url to check

Returns true if the protocol is a source of data (e.g. http), false if the protocol is a filter (e.g. gzip)

### \[static\] QStringList KProtocolManager::listing(const QUrl &*url*) {#listing}

Returns the list of fields this protocol returns when listing The current possibilities are Name, Type, Size, Date, AccessDate, Access, Owner, Group, Link, URL, MimeType as well as Extra1, Extra2 etc. for extra fields (see extraFields).

This corresponds to the "listing=" field in the protocol description file. The supported fields should be separated with ',' in the protocol description file.

`url` the url to check

### \[static\] bool KProtocolManager::markPartial() {#markPartial}

Returns `true` if partial downloads should be marked with a ".part" extension.

### \[static\] KProtocolInfo::Type KProtocolManager::outputType(const QUrl &*url*) {#outputType}

Returns whether the protocol should be treated as a filesystem or as a stream when writing to it.

This corresponds to the "output=" field in the protocol description file. Valid values for this field are "filesystem", "stream" or "none" (default).

`url` the url to check

### \[static\] QString KProtocolManager::protocolForArchiveMimetype(const QString &*mimeType*) {#protocolForArchiveMimetype}

Returns which protocol handles this MIME type, if it's an archive MIME type. For instance zip:/ handles application/x-zip.

This is defined in the protocol description file using an entry like "archiveMimetype=application/x-zip"

This excludes compressed stream of file, like gzip or xz files.

`mimeType` the MIME type to check

### \[static\] void KProtocolManager::reparseConfiguration() {#reparseConfiguration}

Force a reload of the general config file of KIO workers ( kioslaverc).

### \[static\] bool KProtocolManager::supportsDeleting(const QUrl &*url*) {#supportsDeleting}

Returns whether the protocol can delete files/objects.

This corresponds to the "deleting=" field in the protocol description file. Valid values for this field are "true" or "false" (default).

`url` the url to check

### \[static\] bool KProtocolManager::supportsLinking(const QUrl &*url*) {#supportsLinking}

Returns whether the protocol can create links between files/objects.

This corresponds to the "linking=" field in the protocol description file. Valid values for this field are "true" or "false" (default).

`url` the url to check

### \[static\] bool KProtocolManager::supportsListing(const QUrl &*url*) {#supportsListing}

Returns whether the protocol can list files/objects. If a protocol supports listing it can be browsed in e.g. file-dialogs and konqueror.

Whether a protocol supports listing is determined by the "listing=" field in the protocol description file. If the protocol support listing it should list the fields it provides in this field. If the protocol does not support listing this field should remain empty (default.)

`url` the url to check

*See also* [listing](kprotocolmanager.md#listing)()

### \[static\] bool KProtocolManager::supportsMakeDir(const QUrl &*url*) {#supportsMakeDir}

Returns whether the protocol can create directories/folders.

This corresponds to the "makedir=" field in the protocol description file. Valid values for this field are "true" or "false" (default).

`url` the url to check

### \[static\] bool KProtocolManager::supportsMoving(const QUrl &*url*) {#supportsMoving}

Returns whether the protocol can move files/objects between different locations.

This corresponds to the "moving=" field in the protocol description file. Valid values for this field are "true" or "false" (default).

`url` the url to check

### \[static\] bool KProtocolManager::supportsOpening(const QUrl &*url*) {#supportsOpening}

Returns whether the protocol can be opened using [KIO::open](kio-filejob.md#open-1)(const [QUrl](https://doc.qt.io/qt-6/qurl.html)&).

This corresponds to the "opening=" field in the protocol description file. Valid values for this field are "true" or "false" (default).

`url` the url to check

### \[static\] bool KProtocolManager::supportsPermissions(const QUrl &*url*) {#supportsPermissions}

Returns whether the protocol supports KIO/POSIX permissions handling.

When this is false the Permissions properties tab may be hidden, for example. The protocol may still support permission control through other means, specific to the individual KIO worker.

`url` the url to check

### \[static\] bool KProtocolManager::supportsReading(const QUrl &*url*) {#supportsReading}

Returns whether the protocol can retrieve data from URLs.

This corresponds to the "reading=" field in the protocol description file. Valid values for this field are "true" or "false" (default).

`url` the url to check

### \[static\] bool KProtocolManager::supportsTruncating(const QUrl &*url*) {#supportsTruncating}

Returns whether the protocol can be truncated with FileJob::truncate(KIO::filesize\_t length).

This corresponds to the "truncating=" field in the protocol description file. Valid values for this field are "true" or "false" (default).

`url` the url to check

### \[static\] bool KProtocolManager::supportsWriting(const QUrl &*url*) {#supportsWriting}

Returns whether the protocol can store data to URLs.

This corresponds to the "writing=" field in the protocol description file. Valid values for this field are "true" or "false" (default).

`url` the url to check
