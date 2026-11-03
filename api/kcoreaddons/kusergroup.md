---
title: "KUserGroup Class"
description: "Represents a group on your system."
---

# KUserGroup Class

Represents a group on your system. [More...](#details)

- **Header:** `#include <KUser>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS CoreAddons)`  
  `target_link_libraries(mytarget PRIVATE KF6::CoreAddons)`

[List of all members, including inherited members](kusergroup-members.md)

## Public Functions

- [KUserGroup(KGroupId gid)](#KUserGroup)
- [KUserGroup(KUser::UIDMode mode = KUser::UseEffectiveUID)](#KUserGroup-1)
- [KUserGroup(K\_GID gid)](#KUserGroup-2)
- [KUserGroup(const QString &name)](#KUserGroup-4)
- [KUserGroup(const char \*name)](#KUserGroup-5)
- [KUserGroup(const group \*g)](#KUserGroup-6)
- [KUserGroup(const KUserGroup &group)](#KUserGroup-3)
- [~KUserGroup()](#dtor.KUserGroup)
- [KGroupId groupId() const](#groupId)
- [bool isValid() const](#isValid)
- [QString name() const](#name)
- [QStringList userNames(uint maxCount = KCOREADDONS\_UINT\_MAX) const](#userNames)
- [QList\<KUser\> users(uint maxCount = KCOREADDONS\_UINT\_MAX) const](#users)
- [bool KUserGroup::operator!=(const KUserGroup &group) const](#operator-not-eq)
- [KUserGroup &KUserGroup::operator=(const KUserGroup &group)](#operator-eq)
- [bool KUserGroup::operator==(const KUserGroup &group) const](#operator-eq-eq)

## Static Public Members

- [QStringList allGroupNames(uint maxCount = KCOREADDONS\_UINT\_MAX)](#allGroupNames)
- [QList\<KUserGroup\> allGroups(uint maxCount = KCOREADDONS\_UINT\_MAX)](#allGroups)

## Detailed Description {#details}

This class represents a group on your system. You can either get information about the group of the current user, of fetch information about a group on the system. Instances of this class will be explicitly shared, so copying objects is very cheap and you can safely pass objects by value.

## Member Function Documentation {#member-function-documentation}

### \[explicit\] KUserGroup::KUserGroup(KGroupId *gid*) {#KUserGroup}

Creates an object for the group with the given group id. If the KGroupId object is invalid this one will be, too.

`gid` the group id

### \[explicit\] KUserGroup::KUserGroup(KUser::UIDMode *mode* = KUser::UseEffectiveUID) {#KUserGroup-1}

Create an object from the group of the current user.

`mode` if \#[KUser::UseEffectiveUID](kuser.md#UIDMode-enum) is passed the effective user will be used. If \#[KUser::UseRealUserID](kuser.md#UIDMode-enum) is passed the real user will be used. The real UID will be different than the effective UID in setuid programs; in such a case use the effective UID for checking permissions, and the real UID for displaying information about the group associated with the user.

### \[explicit\] KUserGroup::KUserGroup(K\_GID *gid*) {#KUserGroup-2}

Create an object from a group id. If the group does not exist, [isValid](kusergroup.md#isValid)() will return false.

`gid` the group id

### \[explicit\] KUserGroup::KUserGroup(const QString &*name*) {#KUserGroup-4}

Create an object from a group name. If the group does not exist, [isValid](kusergroup.md#isValid)() will return false.

`name` the name of the group

### \[explicit\] KUserGroup::KUserGroup(const char \**name*) {#KUserGroup-5}

Create an object from a group name. If the group does not exist, [isValid](kusergroup.md#isValid)() will return false.

`name` the name of the group

### \[explicit\] KUserGroup::KUserGroup(const group \**g*) {#KUserGroup-6}

Creates an object from a group structure. If the pointer is null, [isValid](kusergroup.md#isValid)() will return false.

`g` the group structure to create the group from.

### KUserGroup::KUserGroup(const KUserGroup &*group*) {#KUserGroup-3}

Creates a new [KUserGroup](kusergroup.md) instance from another [KUserGroup](kusergroup.md) object

`group` the [KUserGroup](kusergroup.md) to copy

### \[noexcept\] KUserGroup::~KUserGroup() {#dtor.KUserGroup}

Destructor.

### \[static\] QStringList KUserGroup::allGroupNames(uint *maxCount* = KCOREADDONS\_UINT\_MAX) {#allGroupNames}

`maxCount` the maximum number of groups to return

Returns a list of all group names on this system

### \[static\] QList\<KUserGroup\> KUserGroup::allGroups(uint *maxCount* = KCOREADDONS\_UINT\_MAX) {#allGroups}

`maxCount` the maximum number of groups to return

Returns a list of all groups on this system

### KGroupId KUserGroup::groupId() const {#groupId}

Returns the native group id of the user.

### bool KUserGroup::isValid() const {#isValid}

Returns whether the group is valid. A [KUserGroup](kusergroup.md) object can be invalid if it is created with a non-existing gid or name. Returns true if the group is valid

### QString KUserGroup::name() const {#name}

The name of the group. Returns the name of the group

### QStringList KUserGroup::userNames(uint *maxCount* = KCOREADDONS\_UINT\_MAX) const {#userNames}

`maxCount` the maximum number of groups to return

Returns a list of all user login names of the group

### QList\<KUser\> KUserGroup::users(uint *maxCount* = KCOREADDONS\_UINT\_MAX) const {#users}

`maxCount` the maximum number of users to return

Returns a list of all users of the group

### bool KUserGroup::operator!=(const KUserGroup &*group*) const {#operator-not-eq}

Two [KUserGroup](kusergroup.md) objects are not equal if their gid()s are not identical. Invalid groups always compare unequal. Returns true if the groups are not identical

### KUserGroup &KUserGroup::operator=(const KUserGroup &*group*) {#operator-eq}

Copies a group

`group` the group that should be copied

Returns this group

### bool KUserGroup::operator==(const KUserGroup &*group*) const {#operator-eq-eq}

Returns true if this group's gid() is identical to the one from `group`. Invalid groups never compare equal.
