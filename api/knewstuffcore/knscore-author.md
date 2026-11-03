---
title: "KNSCore::Author Class"
description: "KNewStuff author information."
---

# KNSCore::Author Class

KNewStuff author information. [More...](#details)

- **Header:** `#include <KNSCore/Author>`
- **CMake:** `find_package(KF6 REQUIRED COMPONENTS NewStuff)`  
  `target_link_libraries(mytarget PRIVATE KF6::NewStuff)`

[List of all members, including inherited members](knscore-author-members.md)

## Properties

- [\[read-only\] email : QString](#email-prop)
- [\[read-only\] name : QString](#name-prop)

## Public Functions

- [Author()](#Author)
- [QUrl avatarUrl() const](#avatarUrl)
- [QString description() const](#description)
- [QString email() const](#email)
- [QString homepage() const](#homepage)
- [QString id() const](#id)
- [QString jabber() const](#jabber)
- [QString name() const](#name)
- [QString profilepage() const](#profilepage)
- [void setAvatarUrl(const QUrl &avatarUrl)](#setAvatarUrl)
- [void setDescription(const QString &description)](#setDescription)
- [void setEmail(const QString &email)](#setEmail)
- [void setHomepage(const QString &homepage)](#setHomepage)
- [void setId(const QString &id)](#setId)
- [void setJabber(const QString &jabber)](#setJabber)
- [void setName(const QString &name)](#setName)
- [void setProfilepage(const QString &profilepage)](#setProfilepage)

## Detailed Description {#details}

This class provides accessor methods to the author data as used by KNewStuff.

> **Warning:** This class should probably not be used directly by the application.

## Property Documentation {#property-documentation}

### \[read-only\] email : QString {#email-prop}

**Access functions:**

- `QString` **[email](knscore-author.md#email)**() const

### \[read-only\] name : QString {#name-prop}

**Access functions:**

- `QString` **[name](knscore-author.md#name)**() const

## Member Function Documentation {#member-function-documentation}

### \[explicit\] Author::Author() {#Author}

### QUrl Author::avatarUrl() const {#avatarUrl}

Returns the author's avatar image URL (may be empty).

*See also* [setAvatarUrl](knscore-author.md#setAvatarUrl)()

### QString Author::description() const {#description}

Returns A long(ish)-form text describing this author, usually self-entered.

*See also* [setDescription](knscore-author.md#setDescription)()

### QString Author::email() const {#email}

Returns the author's email address.

> **Note:** Getter function for property [email](knscore-author.md#email-prop).

*See also* [setEmail](knscore-author.md#setEmail)()

### QString Author::homepage() const {#homepage}

Returns the author's homepage URL.

*See also* [setHomepage](knscore-author.md#setHomepage)()

### QString Author::id() const {#id}

Returns the author's user ID.

*See also* [setId](knscore-author.md#setId)()

### QString Author::jabber() const {#jabber}

Returns the author's jabber address.

*See also* [setJabber](knscore-author.md#setJabber)()

### QString Author::name() const {#name}

Returns the author's full name.

> **Note:** Getter function for property [name](knscore-author.md#name-prop).

*See also* [setName](knscore-author.md#setName)()

### QString Author::profilepage() const {#profilepage}

Returns the author's profile page URL.

*See also* [setProfilepage](knscore-author.md#setProfilepage)()

### void Author::setAvatarUrl(const QUrl &*avatarUrl*) {#setAvatarUrl}

Sets the author's avatar image URL to `avatarUrl`.

*See also* [avatarUrl](knscore-author.md#avatarUrl)()

### void Author::setDescription(const QString &*description*) {#setDescription}

Sets the author's `description`.

*See also* [description](knscore-author.md#description)()

### void Author::setEmail(const QString &*email*) {#setEmail}

Sets the author's `email` address.

*See also* [email](knscore-author.md#email)()

### void Author::setHomepage(const QString &*homepage*) {#setHomepage}

Sets the author's `homepage` URL.

*See also* [homepage](knscore-author.md#homepage)()

### void Author::setId(const QString &*id*) {#setId}

Sets the author's user ID to `id`.

*See also* [id](knscore-author.md#id)()

### void Author::setJabber(const QString &*jabber*) {#setJabber}

Sets the author's `jabber` address.

*See also* [jabber](knscore-author.md#jabber)()

### void Author::setName(const QString &*name*) {#setName}

Sets the author's full `name`.

*See also* [name](knscore-author.md#name)()

### void Author::setProfilepage(const QString &*profilepage*) {#setProfilepage}

Sets the profile page of the author, usually located on the server hosting the content.

`profilepage` is the URL of the author's profile page

*See also* [profilepage](knscore-author.md#profilepage)()
