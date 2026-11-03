---
title: "KACL Class"
description: "a POSIX ACL encapsulation."
---

# KACL Class

a POSIX ACL encapsulation. [More...](#details)

- **Header:** `#include <KACL>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS KIO)`  
  `target_link_libraries(mytarget PRIVATE KF6::KIOCore)`

[List of all members, including inherited members](kacl-members.md)

## Public Functions

- [KACL()](#KACL)
- [KACL(const QString &aclString)](#KACL-2)
- [KACL(mode\_t basicPermissions)](#KACL-3)
- [KACL(const KACL &rhs)](#KACL-1)
- [ACLGroupPermissionsList allGroupPermissions() const](#allGroupPermissions)
- [ACLUserPermissionsList allUserPermissions() const](#allUserPermissions)
- [QString asString() const](#asString)
- [mode\_t basePermissions() const](#basePermissions)
- [bool isExtended() const](#isExtended)
- [bool isValid() const](#isValid)
- [unsigned short maskPermissions(bool &exists) const](#maskPermissions)
- [unsigned short namedGroupPermissions(const QString &name, bool \*exists) const](#namedGroupPermissions)
- [unsigned short namedUserPermissions(const QString &name, bool \*exists) const](#namedUserPermissions)
- [unsigned short othersPermissions() const](#othersPermissions)
- [unsigned short ownerPermissions() const](#ownerPermissions)
- [unsigned short owningGroupPermissions() const](#owningGroupPermissions)
- [bool setACL(const QString &aclStr)](#setACL)
- [bool setAllGroupPermissions(const ACLGroupPermissionsList &list)](#setAllGroupPermissions)
- [bool setAllUserPermissions(const ACLUserPermissionsList &list)](#setAllUserPermissions)
- [bool setMaskPermissions(unsigned short)](#setMaskPermissions)
- [bool setNamedGroupPermissions(const QString &name, unsigned short)](#setNamedGroupPermissions)
- [bool setNamedUserPermissions(const QString &name, unsigned short)](#setNamedUserPermissions)
- [bool setOthersPermissions(unsigned short)](#setOthersPermissions)
- [bool setOwnerPermissions(unsigned short)](#setOwnerPermissions)
- [bool setOwningGroupPermissions(unsigned short)](#setOwningGroupPermissions)

## Detailed Description {#details}

The KACL class encapsulates a POSIX Access Control List. It follows the little standard that couldn't, 1003.1e/1003.2c, which died in draft status.

## Member Function Documentation {#member-function-documentation}

### KACL::KACL() {#KACL}

Creates an empty KACL. Until a valid acl string is set via [setACL](kacl.md#setACL), [isValid](kacl.md#isValid)() will return false.

### KACL::KACL(const QString &*aclString*) {#KACL-2}

Creates a new KACL from `aclString`. If the string is a valid acl string, [isValid](kacl.md#isValid)() will afterwards return true.

### KACL::KACL(mode\_t *basicPermissions*) {#KACL-3}

Creates a new KACL from the basic permissions passed in `basicPermissions`. [isValid](kacl.md#isValid)() will return true, afterwards.

### KACL::KACL(const KACL &*rhs*) {#KACL-1}

Copy ctor

### ACLGroupPermissionsList KACL::allGroupPermissions() const {#allGroupPermissions}

Returns the list of all group permission entries. Each entry consists of a name/permissions pair. This is a [QPair](https://doc.qt.io/qt-6/qpair.html#QPair-typedef), therefore access is provided via the .first and .next members. Returns the list of all group permission entries.

*See also* [setAllGroupPermissions](kacl.md#setAllGroupPermissions)()

### ACLUserPermissionsList KACL::allUserPermissions() const {#allUserPermissions}

Returns the list of all group permission entries. Each entry consists of a name/permissions pair. This is a [QPair](https://doc.qt.io/qt-6/qpair.html#QPair-typedef), therefore access is provided via the .first and .next members. Returns the list of all group permission entries.

*See also* [setAllUserPermissions](kacl.md#setAllUserPermissions)()

### QString KACL::asString() const {#asString}

Return a string representation of the ACL. Returns a string version of the ACL in the format compatible with libacl and POSIX 1003.1e. Implementations conforming to that standard should be able to take such strings as input.

### mode\_t KACL::basePermissions() const {#basePermissions}

Returns the basic (owner/group/others) part of the ACL as a mode\_t

### bool KACL::isExtended() const {#isExtended}

Return whether the ACL contains extended entries or can be expressed using only basic file permissions.

### bool KACL::isValid() const {#isValid}

Returns whether the KACL object represents a valid acl.

### unsigned short KACL::maskPermissions(bool &*exists*) const {#maskPermissions}

Return the entry for the permissions mask if there is one and sets `exists` to true. If there is no such entry, `exists` is set to false. Returns the permissions mask entry

*See also* [setMaskPermissions](kacl.md#setMaskPermissions)()

### unsigned short KACL::namedGroupPermissions(const QString &*name*, bool \**exists*) const {#namedGroupPermissions}

Access to the permissions entry for a named group, if such an entry exists. If `exists` is non-null, the boolean variable it points to is set to true if a matching entry exists and to false otherwise. Returns the permissions for a group with the name in `name`

*See also* [setNamedGroupPermissions](kacl.md#setNamedGroupPermissions)()

### unsigned short KACL::namedUserPermissions(const QString &*name*, bool \**exists*) const {#namedUserPermissions}

Access to the permissions entry for a named user, if such an entry exists. If `exists` is non-null, the boolean variable it points to is set to true if a matching entry exists and to false otherwise. Returns the permissions for a user entry with the name in `name`

*See also* [setNamedUserPermissions](kacl.md#setNamedUserPermissions)()

### unsigned short KACL::othersPermissions() const {#othersPermissions}

Returns the permissions entry for others

*See also* [setOthersPermissions](kacl.md#setOthersPermissions)()

### unsigned short KACL::ownerPermissions() const {#ownerPermissions}

Returns the owner's permissions entry

*See also* [setOwnerPermissions](kacl.md#setOwnerPermissions)()

### unsigned short KACL::owningGroupPermissions() const {#owningGroupPermissions}

Returns the owning group's permissions entry

*See also* [setOwningGroupPermissions](kacl.md#setOwningGroupPermissions)()

### bool KACL::setACL(const QString &*aclStr*) {#setACL}

Sets the whole list from a string. If the string in `aclStr` represents a valid ACL, it will be set, otherwise the ACL remains unchanged. Returns whether setting the ACL was successful.

### bool KACL::setAllGroupPermissions(const ACLGroupPermissionsList &*list*) {#setAllGroupPermissions}

Replace the list of all user permissions with `list`. If one of the entries in the list does not exists, or setting of the ACL entry fails for any reason, the ACL will be left unchanged. Returns success or failure

*See also* [allGroupPermissions](kacl.md#allGroupPermissions)()

### bool KACL::setAllUserPermissions(const ACLUserPermissionsList &*list*) {#setAllUserPermissions}

Replace the list of all user permissions with `list`. If one of the entries in the list does not exists, or setting of the ACL entry fails for any reason, the ACL will be left unchanged. Returns success or failure

*See also* [allUserPermissions](kacl.md#allUserPermissions)()

### bool KACL::setMaskPermissions(*unsigned short*) {#setMaskPermissions}

Set the permissions mask for the ACL. Permissions set for individual entries will be masked with this, such that their effective permissions are the result of the logical and of their entry and the mask. Returns success or failure

*See also* [maskPermissions](kacl.md#maskPermissions)()

### bool KACL::setNamedGroupPermissions(const QString &*name*, *unsigned short*) {#setNamedGroupPermissions}

Set the permissions for a group with the name `name`. Will fail if the group doesn't exist, in which case the ACL be unchanged. Returns success or failure.

*See also* [namedGroupPermissions](kacl.md#namedGroupPermissions)()

### bool KACL::setNamedUserPermissions(const QString &*name*, *unsigned short*) {#setNamedUserPermissions}

Set the permissions for a user with the name `name`. Will fail if the user doesn't exist, in which case the ACL will be unchanged. Returns success or failure.

*See also* [namedUserPermissions](kacl.md#namedUserPermissions)()

### bool KACL::setOthersPermissions(*unsigned short*) {#setOthersPermissions}

Set the permissions entry for others. Returns success or failure

*See also* [othersPermissions](kacl.md#othersPermissions)()

### bool KACL::setOwnerPermissions(*unsigned short*) {#setOwnerPermissions}

Set the owner's permissions entry. Returns success or failure

*See also* [ownerPermissions](kacl.md#ownerPermissions)()

### bool KACL::setOwningGroupPermissions(*unsigned short*) {#setOwningGroupPermissions}

Set the owning group's permissions entry. Returns success or failure

*See also* [owningGroupPermissions](kacl.md#owningGroupPermissions)()
