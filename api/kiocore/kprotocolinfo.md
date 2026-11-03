---
title: "KProtocolInfo Class"
description: "Information about I/O (Internet, etc.) protocols supported by KDE."
---

# KProtocolInfo Class

Information about I/O (Internet, etc.) protocols supported by KDE. [More...](#details)

- **Header:** `#include <KProtocolInfo>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`

[List of all members, including inherited members](kprotocolinfo-members.md)  
[Deprecated members](kprotocolinfo-obsolete.md)

## Public Types

- [KProtocolInfo::ExtraFieldList](#ExtraFieldList-typedef)
- [enum KProtocolInfo::Type](#Type-enum)

## Static Public Members

- [QStringList archiveMimetypes(const QString &protocol)](#archiveMimetypes)
- [QStringList capabilities(const QString &protocol)](#capabilities)
- [QString config(const QString &protocol)](#config)
- [QString defaultMimetype(const QString &protocol)](#defaultMimetype)
- [bool determineMimetypeFromExtension(const QString &protocol)](#determineMimetypeFromExtension)
- [QString docPath(const QString &protocol)](#docPath)
- [QString exec(const QString &protocol)](#exec)
- [KProtocolInfo::ExtraFieldList extraFields(const QUrl &url)](#extraFields)
- [QString icon(const QString &protocol)](#icon)
- [bool isFilterProtocol(const QString &protocol)](#isFilterProtocol)
- [bool isFilterProtocol(const QUrl &url)](#isFilterProtocol-1)
- [bool isHelperProtocol(const QString &protocol)](#isHelperProtocol)
- [bool isHelperProtocol(const QUrl &url)](#isHelperProtocol-1)
- [bool isKnownProtocol(const QUrl &url)](#isKnownProtocol)
- [bool isKnownProtocol(const QString &protocol, bool updateCacheIfNotfound = true)](#isKnownProtocol-1)
- [int maxWorkers(const QString &protocol)](#maxWorkers)
- [int maxWorkersPerHost(const QString &protocol)](#maxWorkersPerHost)
- [QString protocolClass(const QString &protocol)](#protocolClass)
- [QStringList protocols()](#protocols)
- [bool showFilePreview(const QString &protocol)](#showFilePreview)

## Detailed Description {#details}

\* \* \* \*

\* [KProtocolInfo](kprotocolinfo.md) is useful if you want to know which protocols \* KDE supports. In addition you can find out lots of information \* about a certain protocol. All of the functionality is provided by the static \* methods. \* The implementation scans the \*.protocol files of all installed KIO workers to get \* this information and stores the result into an internal cache. \* \* \*.protocol files are installed in the "services" resource. \* \* The [KProtocolInfo](kprotocolinfo.md) methods are reentrant (i.e. can be called from multiple threads simultaneously).

## Member Type Documentation {#member-type-documentation}

### KProtocolInfo::ExtraFieldList {#ExtraFieldList-typedef}

TODO qdoc?

### enum KProtocolInfo::Type {#Type-enum}

Describes the type of a protocol. For instance ftp:// appears as a filesystem with folders and files, while bzip2:// appears as a single file (a stream of data), and telnet:// doesn't output anything.

| Constant | Value | Description |
| --- | --- | --- |
| `KProtocolInfo::T_STREAM` | `0` | stream of data (e.g. single file) |
| `KProtocolInfo::T_FILESYSTEM` | `1` | structured directory |
| `KProtocolInfo::T_NONE` | `2` | no information about the type available |
| `KProtocolInfo::T_ERROR` | `3` | used to signal an error |

## Member Function Documentation {#member-function-documentation}

### \[static\] QStringList KProtocolInfo::archiveMimetypes(const QString &*protocol*) {#archiveMimetypes}

Returns the list of archive MIME types handled by the KIO worker implementing this protocol.

This corresponds to the "archiveMimetype=" field in the protocol description file.

`protocol` the protocol to check

Returns the list of archive MIME types (e.g. application/x-zip) handled.

### \[static\] QStringList KProtocolInfo::capabilities(const QString &*protocol*) {#capabilities}

Returns the list of capabilities provided by the KIO worker implementing this protocol.

This corresponds to the "Capabilities=" field in the protocol description file.

The capability names are not defined globally, they are up to each worker implementation. For example when adding support for a new special command for mounting, one would add the string "Mount" to the capabilities list, and applications could check for that string before sending a special() command that would otherwise do nothing on older KIO worker implementations.

`protocol` the protocol to check

Returns the list of capabilities.

### \[static\] QString KProtocolInfo::config(const QString &*protocol*) {#config}

Returns the name of the config file associated with the specified protocol. This is useful if two similar protocols need to share a single config file, e.g. http and https.

This corresponds to the "config=" field in the protocol description file.

`protocol` the protocol to check

Returns the config file, or an empty string if unknown

### \[static\] QString KProtocolInfo::defaultMimetype(const QString &*protocol*) {#defaultMimetype}

Returns the default MIME type for the specified protocol, if one exists.

This corresponds to the "defaultMimetype=" field in the protocol description file.

`protocol` the protocol to check

Returns the default MIME type of the protocol, or an empty string if none set or protocol unknown

### \[static\] bool KProtocolInfo::determineMimetypeFromExtension(const QString &*protocol*) {#determineMimetypeFromExtension}

Returns whether MIME types can be determined based on extension for this protocol. For some protocols, e.g. http, the filename extension in the URL can not be trusted to truly reflect the file type.

This corresponds to the "determineMimetypeFromExtension=" field in the protocol description file. Valid values for this field are "true" (default) or "false".

`protocol` the protocol to check

Returns `true` if the MIME types can be determined by extension

### \[static\] QString KProtocolInfo::docPath(const QString &*protocol*) {#docPath}

Returns the documentation path for the specified protocol.

This corresponds to the "X-DocPath=" or "DocPath=" field in the protocol description file.

`protocol` the protocol to check

Returns the docpath of the protocol, or an empty string if unknown

### \[static\] QString KProtocolInfo::exec(const QString &*protocol*) {#exec}

Returns the library / executable to open for the protocol `protocol` Example : "kio\_ftp", meaning either the executable "kio\_ftp" or the library "kio\_ftp.la" (recommended), whichever is available.

This corresponds to the "exec=" field in the protocol description file.

`protocol` the protocol to check

Returns the executable of library to open, or QString() for unsupported protocols

### \[static\] KProtocolInfo::ExtraFieldList KProtocolInfo::extraFields(const QUrl &*url*) {#extraFields}

Definition of extra fields in the UDS entries, returned by a listDir operation.

This corresponds to the "ExtraNames=" and "ExtraTypes=" fields in the protocol description file. Those two lists should be separated with ',' in the protocol description file. See [ExtraField](kprotocolinfo-extrafield.md) for details about names and types

### \[static\] QString KProtocolInfo::icon(const QString &*protocol*) {#icon}

Returns the name of the icon, associated with the specified protocol.

This corresponds to the "Icon=" field in the protocol description file.

`protocol` the protocol to check

Returns the icon of the protocol, or an empty string if unknown

### \[static\] bool KProtocolInfo::isFilterProtocol(const QString &*protocol*) {#isFilterProtocol}

Same as above except you can supply just the protocol instead of the whole URL.

### \[static\] bool KProtocolInfo::isFilterProtocol(const QUrl &*url*) {#isFilterProtocol-1}

Returns whether the protocol can act as a filter protocol.

A filter protocol can operate on data that is passed to it but does not retrieve/store data itself, like gzip. A filter protocol is the opposite of a source protocol.

The "source=" field in the protocol description file determines whether a protocol is a source protocol or a filter protocol. Valid values for this field are "true" (default) for source protocol or "false" for filter protocol.

`url` the url to check

Returns `true` if the protocol is a filter (e.g. gzip), false if the protocol is a helper or source

### \[static\] bool KProtocolInfo::isHelperProtocol(const QString &*protocol*) {#isHelperProtocol}

Same as above except you can supply just the protocol instead of the whole URL.

### \[static\] bool KProtocolInfo::isHelperProtocol(const QUrl &*url*) {#isHelperProtocol-1}

Returns whether the protocol can act as a helper protocol. A helper protocol invokes an external application and does not return a file or stream.

This corresponds to the "helper=" field in the protocol description file. Valid values for this field are "true" or "false" (default).

`url` the url to check

Returns `true` if the protocol is a helper protocol (e.g. vnc), false if not (e.g. http)

### \[static\] bool KProtocolInfo::isKnownProtocol(const QUrl &*url*) {#isKnownProtocol}

Returns whether a protocol is installed that is able to handle `url`.

`url` the url to check

### \[static\] bool KProtocolInfo::isKnownProtocol(const QString &*protocol*, bool *updateCacheIfNotfound* = true) {#isKnownProtocol-1}

Same as above except you can supply just the protocol instead of the whole URL.

### \[static\] int KProtocolInfo::maxWorkers(const QString &*protocol*) {#maxWorkers}

Returns the soft limit on the number of KIO workers for this protocol. This limits the number of workers used for a single operation, note that multiple operations may result in a number of instances that exceeds this soft limit.

This corresponds to the "maxInstances=" field in the protocol's worker metadata. The default is 1.

`protocol` the protocol to check

Returns the maximum number of workers, or 1 if unknown

### \[static\] int KProtocolInfo::maxWorkersPerHost(const QString &*protocol*) {#maxWorkersPerHost}

Returns the limit on the number of KIO workers for this protocol per host.

This corresponds to the "maxInstancesPerHost=" field in the protocol's worker metadata. The default is 0 which means there is no per host limit.

`protocol` the protocol to check

Returns the maximum number of workers, or 1 if unknown

### \[static\] QString KProtocolInfo::protocolClass(const QString &*protocol*) {#protocolClass}

Returns the protocol class for the specified protocol.

This corresponds to the "Class=" field in the protocol description file.

The following classes are defined:

- ":internet" for common internet protocols
- ":local" for protocols that access local resources

Protocol classes always start with a ':' so that they can not be confused with the protocols themselves.

`protocol` the protocol to check

Returns the class of the protocol, or an empty string if unknown

### \[static\] QStringList KProtocolInfo::protocols() {#protocols}

Returns list of all known protocols.

### \[static\] bool KProtocolInfo::showFilePreview(const QString &*protocol*) {#showFilePreview}

Returns whether file previews should be shown for the specified protocol.

This corresponds to the "ShowPreviews=" field in the protocol description file.

By default previews are shown if [protocolClass](kprotocolinfo.md#protocolClass) is :local.

`protocol` the protocol to check

Returns `true` if previews should be shown by default, false otherwise
