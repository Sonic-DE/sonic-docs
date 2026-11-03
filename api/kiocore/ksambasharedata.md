---
title: "KSambaShareData Class"
description: "This class represents a Samba user share."
---

# KSambaShareData Class

This class represents a Samba user share. [More...](#details)

- **Header:** `#include <KSambaShareData>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`

[List of all members, including inherited members](ksambasharedata-members.md)

## Public Types

- [enum KSambaShareData::GuestPermission](#GuestPermission-enum)
- [enum KSambaShareData::UserShareError](#UserShareError-enum)

## Public Functions

- [QString acl() const](#acl)
- [QString comment() const](#comment)
- [KSambaShareData::GuestPermission guestPermission() const](#guestPermission)
- [QString name() const](#name)
- [QString path() const](#path)
- [KSambaShareData::UserShareError remove()](#remove)
- [KSambaShareData::UserShareError save()](#save)
- [KSambaShareData::UserShareError setAcl(const QString &acl)](#setAcl)
- [KSambaShareData::UserShareError setComment(const QString &comment)](#setComment)
- [KSambaShareData::UserShareError setGuestPermission(const KSambaShareData::GuestPermission &permission = KSambaShareData::GuestsNotAllowed)](#setGuestPermission)
- [KSambaShareData::UserShareError setName(const QString &name)](#setName)
- [KSambaShareData::UserShareError setPath(const QString &path)](#setPath)

## Detailed Description {#details}

It is possible to share a directory with one or more different names, update the share details or remove.

*See also* [KSambaShare](ksambashare.md)

## Member Type Documentation {#member-type-documentation}

### enum KSambaShareData::GuestPermission {#GuestPermission-enum}

| Constant |   |
| --- | --- |
| `KSambaShareData::GuestsNotAllowed` | `0` |
| `KSambaShareData::GuestsAllowed` | `1` |

### enum KSambaShareData::UserShareError {#UserShareError-enum}

| Constant | Value |   |
| --- | --- | --- |
| `KSambaShareData::UserShareOk` | `0` |   |
| `KSambaShareData::UserShareExceedMaxShares` | `1` |   |
| `KSambaShareData::UserShareNameOk` | `2` |   |
| `KSambaShareData::UserShareNameInvalid` | `3` |   |
| `KSambaShareData::UserShareNameInUse` | `4` |   |
| `KSambaShareData::UserSharePathOk` | `5` |   |
| `KSambaShareData::UserSharePathInvalid` | `6` |   |
| `KSambaShareData::UserSharePathNotExists` | `7` |   |
| `KSambaShareData::UserSharePathNotDirectory` | `8` |   |
| `KSambaShareData::UserSharePathNotAbsolute` | `9` |   |
| `KSambaShareData::UserSharePathNotAllowed` | `10` |   |
| `KSambaShareData::UserShareAclOk` | `11` |   |
| `KSambaShareData::UserShareAclInvalid` | `12` |   |
| `KSambaShareData::UserShareAclUserNotValid` | `13` |   |
| `KSambaShareData::UserShareCommentOk` | `14` |   |
| `KSambaShareData::UserShareGuestsOk` | `15` |   |
| `KSambaShareData::UserShareGuestsInvalid` | `16` |   |
| `KSambaShareData::UserShareGuestsNotAllowed` | `17` |   |
| `KSambaShareData::UserShareSystemError` | `18` | A system error occurred; check [KSambaShare::lastSystemErrorString](ksambashare.md#lastSystemErrorString) |

## Member Function Documentation {#member-function-documentation}

### QString KSambaShareData::acl() const {#acl}

Containing a string describing the permission added to the users, such as "\[DOMAIN\]username1:X,\[DOMAIN\]username2:X,...". X stands for "F" (full control), "R" (read-only) and "D" (deny). By default the acl is Everyone:R.

Returns the share acl.

*See also* [setAcl](ksambasharedata.md#setAcl)()

### QString KSambaShareData::comment() const {#comment}

Returns the share comment.

*See also* [setComment](ksambasharedata.md#setComment)()

### KSambaShareData::GuestPermission KSambaShareData::guestPermission() const {#guestPermission}

Returns whether guest access to the share is allowed or not.

*See also* [setGuestPermission](ksambasharedata.md#setGuestPermission)()

### QString KSambaShareData::name() const {#name}

Returns the share name.

*See also* [setName](ksambasharedata.md#setName)()

### QString KSambaShareData::path() const {#path}

Returns the share path.

*See also* [setPath](ksambasharedata.md#setPath)()

### KSambaShareData::UserShareError KSambaShareData::remove() {#remove}

Unshare the folder held by the object.

Returns [UserShareOk](ksambasharedata.md#UserShareError-enum) if the share was removed or other errors as applicable. Also see [UserShareSystemError](ksambasharedata.md#UserShareError-enum).

### KSambaShareData::UserShareError KSambaShareData::save() {#save}

Share the folder with the information that has been set.

Returns [UserShareOk](ksambasharedata.md#UserShareError-enum) if the share was added or other errors as applicable. Also see [UserShareSystemError](ksambasharedata.md#UserShareError-enum).

### KSambaShareData::UserShareError KSambaShareData::setAcl(const QString &*acl*) {#setAcl}

Sets the acl to the share.

`acl` the acl that will be given to the share.

Returns [UserShareAclOk](ksambasharedata.md#UserShareError-enum) if the acl is valid.

Returns [UserShareAclInvalid](ksambasharedata.md#UserShareError-enum) if the acl has invalid format.

Returns [UserShareAclUserNotValid](ksambasharedata.md#UserShareError-enum) if one of the users in the acl is invalid.

*See also* [acl](ksambasharedata.md#acl)()

### KSambaShareData::UserShareError KSambaShareData::setComment(const QString &*comment*) {#setComment}

Sets the comment for the share.

`comment` the comment that will be given to the share.

Returns [UserShareCommentOk](ksambasharedata.md#UserShareError-enum) always.

*See also* [comment](ksambasharedata.md#comment)()

### KSambaShareData::UserShareError KSambaShareData::setGuestPermission(const KSambaShareData::GuestPermission &*permission* = KSambaShareData::GuestsNotAllowed) {#setGuestPermission}

Flags if guest is allowed or not to access the share.

`permission` the permission that will be given to the share.

Returns [UserShareGuestsOk](ksambasharedata.md#UserShareError-enum) if the permission was set.

Returns [UserShareGuestsNotAllowed](ksambasharedata.md#UserShareError-enum) if the system does not allow guest access to the shares.

*See also* [guestPermission](ksambasharedata.md#guestPermission)()

### KSambaShareData::UserShareError KSambaShareData::setName(const QString &*name*) {#setName}

Sets the share name. If the share name is changed and valid it will remove the existing share and will create a new share. The share name cannot use a name of a system user or containing the forbidden characters '%, \<, \>, \*, ?, \|, /, , +, =, ;, :, ",,. To check if the name is available or valid use the method [KSambaShare::isShareNameAvailable](ksambashare.md#isShareNameAvailable)().

`name` the name that will be given to the share.

Returns [UserShareNameOk](ksambasharedata.md#UserShareError-enum) if the name is valid, [UserShareNameInvalid](ksambasharedata.md#UserShareError-enum) if the name contains invalid characters, [UserShareNameInUse](ksambasharedata.md#UserShareError-enum) if the name is already in use by another shared folder or a by a system user.

*See also* [name](ksambasharedata.md#name)()

### KSambaShareData::UserShareError KSambaShareData::setPath(const QString &*path*) {#setPath}

Set the path for the share.

`path` the path that will be given to the share.

Returns [UserSharePathOk](ksambasharedata.md#UserShareError-enum) if valid.

Returns [UserSharePathInvalid](ksambasharedata.md#UserShareError-enum) if the path is in invalid format.

Returns [UserSharePathNotExists](ksambasharedata.md#UserShareError-enum) if the path does not exists.

Returns [UserSharePathNotDirectory](ksambasharedata.md#UserShareError-enum) if the path points to file instead of a directory.

Returns [UserSharePathNotAbsolute](ksambasharedata.md#UserShareError-enum) if the path is not is absolute form.

Returns [UserSharePathNotAllowed](ksambasharedata.md#UserShareError-enum) if the path is not owner by the user.

*See also* [path](ksambasharedata.md#path)()
