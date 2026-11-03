---
title: "KUser Class"
description: "Represents a user on your system."
---

# KUser Class

Represents a user on your system. [More...](#details)

- **Header:** `#include <KUser>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

[List of all members, including inherited members](kuser-members.md)

## Public Types

- [enum KUser::UIDMode](#UIDMode-enum)
- [enum KUser::UserProperty](#UserProperty-enum)

## Public Functions

- [KUser(KUser::UIDMode mode = UseEffectiveUID)](#KUser)
- [KUser(KUserId uid)](#KUser-1)
- [KUser(K\_UID uid)](#KUser-2)
- [KUser(const QString &name)](#KUser-4)
- [KUser(const char \*name)](#KUser-5)
- [KUser(const passwd \*p)](#KUser-6)
- [KUser(const KUser &user)](#KUser-3)
- [QString faceIconPath() const](#faceIconPath)
- [KGroupId groupId() const](#groupId)
- [QStringList groupNames(uint maxCount = KCOREADDONS\_UINT\_MAX) const](#groupNames)
- [QList\<KUserGroup\> groups(uint maxCount = KCOREADDONS\_UINT\_MAX) const](#groups)
- [QString homeDir() const](#homeDir)
- [bool isSuperUser() const](#isSuperUser)
- [bool isValid() const](#isValid)
- [QString loginName() const](#loginName)
- [QVariant property(KUser::UserProperty which) const](#property)
- [QString shell() const](#shell)
- [KUserId userId() const](#userId)
- [bool KUser::operator!=(const KUser &user) const](#operator-not-eq)
- [KUser &KUser::operator=(const KUser &user)](#operator-eq)
- [bool KUser::operator==(const KUser &user) const](#operator-eq-eq)

## Static Public Members

- [QStringList allUserNames(uint maxCount = KCOREADDONS\_UINT\_MAX)](#allUserNames)
- [QList\<KUser\> allUsers(uint maxCount = KCOREADDONS\_UINT\_MAX)](#allUsers)

## Detailed Description {#details}

This class represents a user on your system. You can either get information about the current user, or fetch information about a user on the system. Instances of this class will be explicitly shared, so copying objects is very cheap and you can safely pass objects by value.

## Member Type Documentation {#member-type-documentation}

### enum KUser::UIDMode {#UIDMode-enum}

| Constant | Value | Description |
| --- | --- | --- |
| `KUser::UseEffectiveUID` | `0` | Use the effective user id |
| `KUser::UseRealUserID` | `1` | Use the real user id |

### enum KUser::UserProperty {#UserProperty-enum}

| Constant |   |
| --- | --- |
| `KUser::FullName` | `0` |
| `KUser::RoomNumber` | `1` |
| `KUser::WorkPhone` | `2` |
| `KUser::HomePhone` | `3` |

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KUser::KUser(KUser::UIDMode *mode* = UseEffectiveUID) {#KUser}

Creates an object that contains information about the current user. (as returned by getuid(2) or geteuid(2), taking $LOGNAME/$USER into account).

`mode` if \#[UseEffectiveUID](kuser.md#UIDMode-enum) is passed the effective user is returned. If \#[UseRealUserID](kuser.md#UIDMode-enum) is passed the real user will be returned. The real UID will be different than the effective UID in setuid programs; in such a case use the effective UID for checking permissions, and the real UID for displaying information about the user.

### \[explicit\] KUser::KUser(KUserId *uid*) {#KUser-1}

Creates an object for the user with the given user id. If the KUserId object is invalid this one will be, too.

`uid` the user id

### \[explicit\] KUser::KUser(K\_UID *uid*) {#KUser-2}

Creates an object for the user with the given user id. If the user does not exist [isValid](kuser.md#isValid)() will return false.

`uid` the user id

### \[explicit\] KUser::KUser(const QString &*name*) {#KUser-4}

Creates an object that contains information about the user with the given name. If the user does not exist [isValid](kuser.md#isValid)() will return false.

`name` the name of the user

### \[explicit\] KUser::KUser(const char \**name*) {#KUser-5}

Creates an object that contains information about the user with the given name. If the user does not exist [isValid](kuser.md#isValid)() will return false.

`name` the name of the user

### \[explicit\] KUser::KUser(const passwd \**p*) {#KUser-6}

Creates an object from a passwd structure. If the pointer is null [isValid](kuser.md#isValid)() will return false.

`p` the passwd structure to create the user from

### KUser::KUser(const KUser &*user*) {#KUser-3}

Creates an object from another [KUser](kuser.md) object

`user` the user to create the new object from

### \[static\] QStringList KUser::allUserNames(uint *maxCount* = KCOREADDONS\_UINT\_MAX) {#allUserNames}

`maxCount` the maximum number of users to return

Returns all user names of the system.

### \[static\] QList\<KUser\> KUser::allUsers(uint *maxCount* = KCOREADDONS\_UINT\_MAX) {#allUsers}

`maxCount` the maximum number of users to return

Returns all users of the system.

### QString KUser::faceIconPath() const {#faceIconPath}

The path to the user's face file. Returns the path to the user's face file or QString() if no face has been set

### KGroupId KUser::groupId() const {#groupId}

Returns the native user id of the user.

### QStringList KUser::groupNames(uint *maxCount* = KCOREADDONS\_UINT\_MAX) const {#groupNames}

`maxCount` the maximum number of groups to return

Returns all group names of the user

### QList\<KUserGroup\> KUser::groups(uint *maxCount* = KCOREADDONS\_UINT\_MAX) const {#groups}

`maxCount` the maximum number of groups to return

Returns all groups of the user

### QString KUser::homeDir() const {#homeDir}

The path to the user's home directory. Returns the home directory of the user or QString() if the user is invalid

### bool KUser::isSuperUser() const {#isSuperUser}

Checks whether the user is the super user (root). Returns true if the user is root

### bool KUser::isValid() const {#isValid}

Returns true if the user is valid. A [KUser](kuser.md) object can be invalid if you created it with an non-existing uid or name. Returns true if the user is valid

### QString KUser::loginName() const {#loginName}

The login name of the user. Returns the login name of the user or QString() if user is invalid

### QVariant KUser::property(KUser::UserProperty *which*) const {#property}

Returns an extended property given by `which`.

Under Windows, [RoomNumber](kuser.md#UserProperty-enum), [WorkPhone](kuser.md#UserProperty-enum) and [HomePhone](kuser.md#UserProperty-enum) are unsupported.

Returns a [QVariant](https://doc.qt.io/qt-6/qvariant.html) with the value of the property or an invalid [QVariant](https://doc.qt.io/qt-6/qvariant.html), if the property is not set

### QString KUser::shell() const {#shell}

The path to the user's login shell. Returns the login shell of the user or QString() if the user is invalid

### KUserId KUser::userId() const {#userId}

Returns the native user id of the user.

### bool KUser::operator!=(const KUser &*user*) const {#operator-not-eq}

Two [KUser](kuser.md) objects are not equal if [userId](kuser.md#userId)() are not identical. Invalid users always compare unequal.

### KUser &KUser::operator=(const KUser &*user*) {#operator-eq}

Copies a user

`user` the user to copy

Returns this object

### bool KUser::operator==(const KUser &*user*) const {#operator-eq-eq}

Two [KUser](kuser.md) objects are equal if the [userId](kuser.md#userId)() are identical. Invalid users never compare equal.
