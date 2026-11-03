---
title: "KIO::AuthInfo Class"
description: "A two way messaging class for passing authentication information."
---

# KIO::AuthInfo Class

A two way messaging class for passing authentication information. [More...](#details)

- **Header:** `#include <KIO/AuthInfo>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`

[List of all members, including inherited members](kio-authinfo-members.md)

## Public Types

- [enum AuthInfo::FieldFlags](#FieldFlags-enum)

## Public Functions

- [AuthInfo()](#AuthInfo)
- [AuthInfo(const KIO::AuthInfo &info)](#AuthInfo-1)
- [QVariant getExtraField(const QString &fieldName) const](#getExtraField)
- [KIO::AuthInfo::FieldFlags getExtraFieldFlags(const QString &fieldName) const](#getExtraFieldFlags)
- [bool isModified() const](#isModified)
- [void setExtraField(const QString &fieldName, const QVariant &value)](#setExtraField)
- [void setExtraFieldFlags(const QString &fieldName, const KIO::AuthInfo::FieldFlags flags)](#setExtraFieldFlags)
- [void setModified(bool flag)](#setModified)

## Static Public Members

- [void registerMetaTypes()](#registerMetaTypes)

## Detailed Description {#details}

This class is intended to make it easier to prompt for, cache and retrieve authorization information.

When using this class to cache, retrieve or prompt authentication information, you only need to set the necessary attributes. For example, to check whether a password is already cached, the only required information is the URL of the resource and optionally whether or not a path match should be performed. Similarly, to prompt for password you only need to optionally set the prompt, username (if already supplied), comment and [commentLabel](kio-authinfo.md#commentLabel-var) fields.

> **Note:** If you extend this class to add additional parameters do not forget to overload the stream insertion and extraction operators ("\<\<" and "\>\>") so that the added data can be correctly serialized.

## Member Type Documentation {#member-type-documentation}

### enum AuthInfo::FieldFlags {#FieldFlags-enum}

Flags for extra fields

| Constant |   |
| --- | --- |
| `KIO::AuthInfo::ExtraFieldNoFlags` | `0` |
| `KIO::AuthInfo::ExtraFieldReadOnly` | `1 << 1` |
| `KIO::AuthInfo::ExtraFieldMandatory` | `1 << 2` |

## Member Function Documentation {#member-function-documentation}

### AuthInfo::AuthInfo() {#AuthInfo}

Default constructor.

### AuthInfo::AuthInfo(const KIO::AuthInfo &*info*) {#AuthInfo-1}

Copy constructor.

### QVariant AuthInfo::getExtraField(const QString &*fieldName*) const {#getExtraField}

Get Extra Field Value Check [QVariant::isValid](https://doc.qt.io/qt-6/qvariant.html#isValid)() to find out if the field exists.

### KIO::AuthInfo::FieldFlags AuthInfo::getExtraFieldFlags(const QString &*fieldName*) const {#getExtraFieldFlags}

Get Extra Field Flags

### bool AuthInfo::isModified() const {#isModified}

Use this method to check if the object was modified. Returns `true` if the object has been modified

### \[static\] void AuthInfo::registerMetaTypes() {#registerMetaTypes}

Register the meta-types for [AuthInfo](kio-authinfo.md). This is called from [AuthInfo](kio-authinfo.md)'s constructor but needed by daemons on the D-Bus such as kpasswdserver.

### void AuthInfo::setExtraField(const QString &*fieldName*, const QVariant &*value*) {#setExtraField}

Set Extra Field Value. Currently supported extra-fields: "domain" ([QString](https://doc.qt.io/qt-6/qstring.html)), "anonymous" (bool) Setting it to an invalid QVariant() will disable the field. Extra Fields are disabled by default.

### void AuthInfo::setExtraFieldFlags(const QString &*fieldName*, const KIO::AuthInfo::FieldFlags *flags*) {#setExtraFieldFlags}

Set Extra Field Flags

### void AuthInfo::setModified(bool *flag*) {#setModified}

Use this method to indicate that this object has been modified.

`flag` true to mark the object as modified, false to clear

*See also* [isModified](kio-authinfo.md#isModified)()

## Member Variable Documentation {#member-variable-documentation}

### QString AuthInfo::caption {#caption-var}

The text to displayed in the title bar of the password prompting dialog.

> **Note:** If this field is not set, the authentication dialog simply displays the preset default caption.

This setting is *optional* and empty by default.

### QString AuthInfo::comment {#comment-var}

Additional comment to be displayed when prompting the user for authentication information.

This field allows you to display a short (no more than 80 characters) extra description in the password prompt dialog. For example, this field along with the [commentLabel](kio-authinfo.md#commentLabel-var) can be used to describe the server that requested the authentication:

```cpp
Server:   Squid Proxy @ foo.com
```

where "Server:" is the [commentLabel](kio-authinfo.md#commentLabel-var) and the rest is the actual comment. Note that it is always better to use the `commentLabel` field as it will be placed properly in the dialog rather than to include it within the actual comment.

This setting is *optional* and empty by default.

### QString AuthInfo::commentLabel {#commentLabel-var}

Descriptive label to be displayed in front of the comment when prompting the user for password.

This setting is *optional* and only applicable when the comment field is also set.

### QString AuthInfo::digestInfo {#digestInfo-var}

Field to store any extra authentication information for protocols that need it.

This setting is *optional* and mostly applicable for HTTP protocol. However, any protocol can make use of it to store extra info.

### bool AuthInfo::keepPassword {#keepPassword-var}

Flag to indicate the persistence of the given password.

This is a two-way flag, when set before calling openPasswordDialog it makes the "keep Password" check box visible to the user. In return the flag will indicate the state of the check box. By default if the flag is checked the password will be cached for the entire life of the current KDE session otherwise the cached password is deleted right after the application using it has been closed.

### QString AuthInfo::password {#password-var}

This is *required* for caching.

### QString AuthInfo::prompt {#prompt-var}

Information to be displayed when prompting the user for authentication information.

> **Note:** If this field is not set, the authentication dialog simply displays the preset default prompt.

This setting is *optional* and empty by default.

### bool AuthInfo::readOnly {#readOnly-var}

Flag which if set forces the username field to be read-only.

This setting is *optional* and false by default.

### QString AuthInfo::realmValue {#realmValue-var}

A unique identifier that allows caching of multiple passwords for different resources in the same server.

Mostly this setting is applicable to the HTTP protocol whose authentication scheme explicitly defines the use of such a unique key. However, any protocol that can generate or supply a unique id can effectively use it to distinguish passwords.

This setting is *optional* and not set by default.

### QUrl AuthInfo::url {#url-var}

The URL for which authentication is to be stored.

This field is required when attempting to cache authorization and retrieve it. However, it is not needed when prompting the user for authorization info.

This setting is *required* except when prompting the user for password.

### QString AuthInfo::username {#username-var}

This is *required* for caching.

### bool AuthInfo::verifyPath {#verifyPath-var}

Flag that, if set, indicates whether a path match should be performed when requesting for cached authorization.

A path is deemed to be a match if it is equal to or is a subset of the cached path. For example, if stored path is "/foo/bar" and the request's path set to "/foo/bar/acme", then it is a match whereas it would not if the request's path was set to "/foo".

This setting is *optional* and false by default.
